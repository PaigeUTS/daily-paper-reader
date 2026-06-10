---
title: "DynaPipe: Dynamic Layer Redistribution for Efficient Serving of LLMs with Pipeline Parallelism"
title_zh: DynaPipe：面向LLM流水线并行服务的动态层重分配
authors: "HongXin Xu, Tianyu Guo, Xianwei Zhang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=D6w7wIN360"
tags: ["query:agents-os"]
score: 4.0
evidence: 针对LLM服务的流水线并行，解决跨设备负载不均衡
tldr: 大语言模型推理中流水线并行常因尾阶段任务不均衡导致气泡。DynaPipe通过动态重分配层来平衡各阶段计算负载，减少空闲时间。实验表明该方法显著提升吞吐量并降低延迟，为异构服务器上的高效LLM服务提供了新思路。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 现有流水线并行中尾阶段计算负载过重导致上游设备空闲，整体性能受损。
method: 提出动态层重分配算法，根据各阶段实际计算需求重新分配模型层。
result: 在模拟和真实环境中均显著减少流水线气泡，提升吞吐量。
conclusion: 动态层重分配可有效缓解流水线不平衡问题，适用于异构计算环境。
---

## Abstract
To accelerate large language model (LLM) inference, pipeline parallelism partitions model layers into sequential stages, each assigned to a different device for concurrent execution. However, this method often suffers from pipeline bubbles caused by imbalanced computation in the tail stage. While upstream stages focus solely on layer-forward operations, the final stage must also handle post-processing tasks like sampling, introducing significant latency. This uneven workload leads to pipeline misalignment, forcing upstream stages to idle and degrading overall performance. Existing frameworks typically distribute layers evenly across stages without accounting for computational load differences. To address this, we propose DynaPipe, a dynamic layer redistribution scheme that adaptively balances computation by predicting execution latency in real time. Moreover, we introduce an asynchronous key-value (KV) cache migration coordinator to enable
non-blocking layer redistribution during inference. Experiments on representative LLMs demonstrate that DynaPipe reduces average end-to-end request latency by 8% to 49% across diverse workloads, outperforming state-of-the-art pipeline parallelism systems.

---

## 论文详细总结（自动生成）

# DynaPipe：面向LLM流水线并行服务的动态层重分配 —— 论文详细总结

## 1. 核心问题与整体含义（研究动机与背景）
- **问题**：在基于Transformer的大语言模型（LLM）推理中，流水线并行（Pipeline Parallelism, PP）是一种常用的跨设备模型划分策略。然而，现有PP框架通常将模型层均匀分配到各个流水线阶段（stage），忽略了**尾阶段（final stage）的额外计算负载**——尾阶段不仅需要执行前向计算，还必须完成logits计算和采样（sampling）等后处理操作。这导致尾阶段的计算时间显著长于上游阶段，产生“流水线气泡”（pipeline bubble），上游设备被迫空闲等待，严重降低整体吞吐量和硬件利用率。
- **背景**：尽管已有工作（如gLLM、SARATHI）通过调度优化缓解气泡，但均未系统性解决由采样操作引起的**跨阶段负载不均衡**。实验表明，采样时间平均约为单层前向计算时间的3.09倍，且随解码请求数动态变化，静态均匀划分无法适应这种变化。
- **核心含义**：本文首次明确指出采样操作是PP推理中不可忽视的性能瓶颈，并提出动态调整层分配以平衡各阶段负载，从而提升LLM服务效率。

## 2. 方法论：核心思想、关键技术细节、公式与算法流程
### 核心思想
DynaPipe在运行时**动态重新分配各流水线阶段的层数**，通过将尾阶段的部分层迁移到上游阶段，使采样计算与前向计算部分重叠，减少流水线气泡。系统包含三个核心组件：执行时间预测器、气泡感知调度器、异步KV缓存迁移协调器。

### 关键技术细节
1. **执行时间预测器（Execution Time Predictor）**  
   - 建立两个轻量级线性预测模型：
     - 单层前向时间模型：\( T_{\text{layer}} = \sum_{i=1}^{N} (\phi_1 n_i + \phi_2 n_i L_i + \epsilon) \)，其中 \( n_i \) 为第i个请求的token数，\( L_i \) 为序列长度，参数通过离线profiling拟合。
     - 采样时间模型：\( T_{\text{sample}} = \alpha N_{\text{decode}} + \beta \)，其中 \( N_{\text{decode}} \) 为解码请求数。
   - 预测误差：层前向时间平均相对误差4.95%，采样时间误差仅0.31%，每次预测仅需0.5微秒。

2. **气泡感知调度器（Bubble-Aware Scheduler）**  
   - **目标**：使所有流水线阶段执行时间尽可能一致，即 \( \Delta \approx 0 \)。
   - **决策变量**：从尾阶段移除k层，并将这些层均匀分配到前 \( m = \min(k, \text{num\_stages}-1) \) 个上游阶段。
   - **度量指标**：\(\Delta = T_{\text{sample}} - k \cdot T_{\text{layer}} - \frac{k}{m} \cdot T_{\text{layer}}\)
   - **稳定窗口机制**：引入大小为25的滑动窗口，仅当同一配置在窗口内持续出现时才触发调整，避免频繁重分配。

3. **迁移协调器（Migration Coordinator）**  
   - **设计**：实现异步非阻塞的KV缓存迁移。源阶段完成待迁移层的前向计算后，立即通过NCCL异步发送KV缓存至目标阶段；目标阶段在到达新层时仅需等待接收完成，其余计算可并行进行。预加载权重减少迁移延迟。
   - **效果**：迁移操作与计算高度重叠，每次迁移额外开销可控（单层KV缓存迁移在PCIe环境下<100ms）。

### 算法流程（文字说明）
1. 初始化阶段：预加载可能被重新分配的层权重到各GPU。
2. 每个batch计算后，执行时间预测器给出当前的前向和采样时间估计。
3. 气泡感知调度器计算是否需要调整层分配（基于滑动窗口的累积决策）。
4. 若触发调整，迁移协调器执行异步KV缓存迁移，同时流水线继续执行其他层的计算。
5. 调整完成后，新配置生效，继续推理。

## 3. 实验设计
### 数据集
- **ShareGPT**：真实对话数据（平均输入221 tokens，输出157 tokens；P90：627输入/382输出）
- **Azure-Conv**：Azure生产环境对话数据（平均输入514 tokens，输出192 tokens；P90：1008输入/412输出）
- **合成数据集**：固定输入长度512，变化输出长度以测试不同输出-输入比（O:I Ratio）

### Benchmark与对比方法
- 基线系统：
  - **gLLM**：基于PP的高效推理框架（DynaPipe的基础框架）
  - **vLLM (v0.8.5 V1)**：使用PP + 固定chunk size
  - **SGLang (v0.4.3.post2)**：仅使用张量并行（TP）
- 所有方法均采用chunked prefill（最大chunk size=2048）。

### 评价指标
- 平均端到端延迟（E2EL）
- SLO合规率：同时满足TTFT和TPOT阈值（根据模型和数据集设定，如14B模型ShareGPT：TTFT≤1s，TPOT≤100ms）

### 模型
- **Qwen2.5-14B**（14B参数）
- **Qwen2.5-32B**（32B参数）
- 附加实验：Qwen3-30B-A3B（MoE模型）、Meta-Llama-3-8B-Instruct（稠密模型）

## 4. 资源与算力
- **GPU**：4块 NVIDIA A100-PCIe-40GB
- **互联方式**：单节点内通过PCIe连接；多节点实验通过禁用共享内存、P2P和InfiniBand模拟TCP网络，还原跨节点场景。
- **通信库**：ZeroMQ（进程间通信）、NCCL（GPU间通信）
- **训练时长**：未明确说明，仅提到离线profiling用于拟合预测模型参数。实验为推理服务评估，非训练任务。

## 5. 实验数量与充分性
### 实验组数
- **总体性能对比**（图4）：在ShareGPT和Azure-Conv两个数据集上，针对14B和32B模型，各设置5-6个不同请求速率，共约20+组实验。
- **静态重分配策略对比**（图5）：合成数据集，输出-输入比从0到0.5，对比5种静态配置 + DynaPipe。
- **窗口阈值消融**（图6）：窗口大小从0到50，记录E2EL和调整次数。
- **多节点实验**（图7）：14B模型，ShareGPT和Azure-Conv，5个速率点。
- **预测器精度验证**（图8）：合成数据，14B和32B模型，评估层时间和采样时间的预测vs实际散点图。
- **额外模型验证**（附录图9）：Qwen3-30B-A3B和Llama3-8B，ShareGPT和Azure-Conv，多个速率点。
- **系统开销分析**（附录B）：迁移开销、内存开销的理论与实验分析。

### 充分性与公平性
- **公平性**：所有基线均使用相同数据集、相同GPU数量和相同chunked prefill策略。实验代码将开源。
- **充分性**：覆盖了不同模型规模（8B、14B、30B-MoE、32B）、不同数据集（对话型、生产型）、不同请求率（低到高）、不同输出-输入比、单节点与跨节点场景。消融实验验证了窗口阈值、预测器精度的有效性。但未进行多GPU数量（如8卡）或更复杂拓扑的实验，也未探讨与张量并行、专家并行等联合优化的场景。

## 6. 主要结论与发现
1. **显著降低延迟**：与最优基线gLLM相比，DynaPipe在ShareGPT上降低端到端延迟8%-41%（不同模型和请求率），在Azure-Conv上降低约8%-34%。
2. **提升SLO合规率**：在高请求率下，DynaPipe能维持更高的SLO达标率，尤其在接近饱和点时优势明显（如32B模型在ShareGPT上可多支持19%的请求率）。
3. **适应性优于静态策略**：在不同输出-输入比下，DynaPipe始终接近或达到最佳性能，而静态重分配策略仅在特定比率下有效。
4. **迁移开销可控**：窗口机制将调整次数限制在5-7次左右，额外内存开销约7.5%（以32B模型为例），系统性能提升远大于开销。
5. **跨模型通用性**：在MoE模型和稠密模型上均有效，证明采样气泡是PP推理的普遍问题。
6. **多节点场景有效**：在模拟跨网络环境下，DynaPipe仍能降低延迟24%左右（14B模型）。

## 7. 优点
- **问题新颖且实际**：首次系统揭示采样操作导致的流水线气泡问题，并给出实用解决方案。
- **轻量高效**：预测模型简单（线性拟合），开销极低（每次预测0.5μs）；迁移异步化避免阻塞。
- **健壮性设计**：滑动窗口机制避免频繁调整，稳定性好。
- **实验全面**：涵盖多种模型、数据集、请求率、消融实验和跨节点场景，结果可靠。
- **开源友好**：代码将开源，便于复现和扩展。

## 8. 不足与局限
- **实验范围有限**：
  - GPU数量固定为4块，未测试更多设备（如8卡、16卡）的扩展性。
  - 仅使用PCIe互联，未涵盖NVLink等高速互联场景（但附录提及NVLink可进一步降低迁移开销）。
  - 未与其他动态调度方法（如Llumnix、Seesaw）对比，仅对比了静态划分框架。
- **内存开销**：预加载未使用的层权重，导致额外7.5%显存占用（论文认为可接受，但未提供进一步优化实验）。
- **迁移开销**：虽重叠良好，但在极端小batch场景下迁移仍可能成为瓶颈（论文提及单次<100ms）。
- **未考虑多维度并行**：当前仅针对PP，未与TP、EP（专家并行）联合优化，未来工作需拓展。
- **理论分析深度**：预测模型基于线性假设，未严格证明在复杂注意力计算下的普适性（但实验验证误差小）。
- **未讨论冷启动或模型切换场景**：预加载策略在模型频繁切换时可能内存不足。

（完）
