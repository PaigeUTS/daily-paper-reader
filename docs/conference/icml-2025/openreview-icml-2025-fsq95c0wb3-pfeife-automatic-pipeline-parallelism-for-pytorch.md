---
title: "Pfeife: Automatic Pipeline Parallelism for PyTorch"
title_zh: Pfeife：PyTorch自动流水线并行
authors: "Ho Young Jhoo, Chung-Kil Hur, Nuno P. Lopes"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=FSq95c0wb3"
tags: ["query:agents-os"]
score: 8.0
evidence: 针对多个设备的PyTorch模型自动流水线并行
tldr: Pfeife是首个与PyTorch集成的自动流水线并行工具，能够透明地截获模型执行并跨设备并行化。它支持执行超出单GPU内存的大模型，无需手动修改代码，显著降低了异构计算环境下大模型部署的工程负担。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-fsq95c0wb3/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1236, \"height\": 419, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fsq95c0wb3/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1167, \"height\": 275, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fsq95c0wb3/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1344, \"height\": 407, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fsq95c0wb3/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 862, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fsq95c0wb3/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 844, \"height\": 537, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fsq95c0wb3/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 828, \"height\": 455, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fsq95c0wb3/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 865, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fsq95c0wb3/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1775, \"height\": 327, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-fsq95c0wb3/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1744, \"height\": 348, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-fsq95c0wb3/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 897, \"height\": 426, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fsq95c0wb3/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 769, \"height\": 596, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fsq95c0wb3/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1418, \"height\": 114, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fsq95c0wb3/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1341, \"height\": 252, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-fsq95c0wb3/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1493, \"height\": 723, \"label\": \"Table\"}]"
motivation: 大模型无法单GPU部署，而手动流水线并行复杂。
method: 开发与PyTorch集成的自动流水线并行工具，透明拦截执行。
result: 可执行超大模型，无需手动工作。
conclusion: Pfeife使大模型多设备部署自动化。
---

## Abstract
The memory requirements of machine learning (ML) models has been growing quickly. However, the memory capacity of GPUs has not kept pace. Despite significant research on reducing the memory usage of ML models, the larger models do not fit in a single device. A popular solution to the memory capacity issue is to use multiple devices in parallel. In this paper, we focus on a particular form of parallelism called pipelining, as it offers a good balance between cost and performance for many ML models. We present Pfeife, the first tool that integrates with PyTorch to provide automatic pipelining of ML models. Pfeife intercepts the execution of models and parallelizes them transparently, requiring no manual work. We show that Pfeife can execute large models that would otherwise not run due to not fitting in a single device. Moreover, Pfeife can pipeline non-sequential models such as Stable Diffusion, which are not supported by existing pipelining parallelism tools. Pfeife outperforms state-of-the-art tools by up to 22%.

---

## 论文详细总结（自动生成）

# Pfeife: 自动流水线并行工具 —— 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：机器学习模型的内存需求急剧增长（如 Llama 3.1 405B FP16 权重占用约 754 GiB），而 GPU 内存容量增长缓慢（最新 NVIDIA GB200 仅 384 GiB），导致超大规模模型无法在单块 GPU 上训练或推理。
- **现有方案局限性**：数据并行、模型并行等技术或通信开销大，或需要人工手动划分模型、编写特定代码，对 ML 从业者（非分布式系统专家）极不友好。流水线并行（pipeline parallelism）在性能和成本之间取得较好平衡，但现有工具（如 DeepSpeed、Colossal-AI）仍需大量手动工作，且不支持非顺序模型（如 Stable Diffusion 的 U-Net）。
- **本文目标**：开发一个与 PyTorch 深度集成、完全自动化的流水线并行工具 **Pfeife**，用户无需修改模型代码，即可透明地将大模型跨多 GPU 运行，并支持复杂模型结构。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
- 利用 PyTorch 2 的 **TorchDynamo** JIT 编译器在运行时捕获模型的静态数据流图（DFG）。
- 自动将 DFG 中的操作（算子）分配到多个设备，生成流水线调度计划，并透明替换原模型执行。
- 采用 **联合优化（co-optimization）** 策略，同时优化图的切片分割和调度参数。

### 关键技术细节

1. **图构造与融合**
   - 从 TorchFX 获取计算图（可能有数千个节点），通过**切片**将节点分组为融合图（fused graph）以减小搜索空间。

2. **调度规范语言**
   - 定义形式化的调度模型：由设备操作集合 `P` 和操作间依赖关系 `R` 组成。支持同步/异步管道，可表达大多数已知流水线调度（如 GPipe、1F1B、BFS 等）。

3. **成本模型**
   - **运行时间**：基于**关键路径分析**，将调度依赖图视为 DAG，通过 Dijkstra 求最长路径（关键路径）来估计总执行时间。
   - **峰值内存**：根据每个设备上激活值的累积情况估算（保守地高估以避免 OOM）。
   - **通信时间**：离线微基准测试测量设备间的吞吐和延迟。

4. **参数化调度空间**
   - 限制搜索空间为 **looped 1F1B** 调度，参数包括：
     - `B`（总微批次数）
     - `Nl`（循环次数）
     - `Bl`（每循环每阶段的微批次数）
     - `Bf`（预取批次数列表，每个设备额外前向传播的批次数）
   - 该参数化可模拟多种已有调度，并引入**预取（prefetching）** 机制来填充前向-后向之间的气泡。

5. **联合优化算法（算法 1）**
   - 对每组调度参数，使用**束搜索（beam search）** 优化切片点：
     - 初始切片基于均匀分布；
     - 逐步移动切片点，向两端成比例调整；
     - 若新切片在估计延迟上更优且不超过内存容量，则保留；
     - 迭代直到收敛；
     - 选择所有调度参数中延迟最小的方案。
   - 亮点：算法发现**不均匀切片**配合预取往往优于均匀切片（与常识相悖）。

6. **运行时（PipeRunner）**
   - 通过闭包（closure）封装训练循环，自动将输入切分为微批次，控制前向/后向/优化步骤的流水线执行。

## 3. 实验设计

### 数据集/场景
- **覆盖测试**：使用 TorchBench 官方基准套件中的 49 个可训练模型（包括 CNN、Transformer、扩散模型等）。
- **端到端性能测试**：选择 4 个代表性大模型：
  - ViT-g/14（视觉 Transformer，计算密集型）
  - Llama2-7B（LLM，内存密集型）
  - Stable Diffusion-XL（非顺序模型，U-Net 含跳跃连接）
  - GPT2-large（辅助验证）
- 所有模型均使用 HuggingFace 实现，微批次大小按要求调整。

### Benchmark 与对比方法
- **覆盖测试**：对比有无流水线并行下的输出（loss）是否一致。
- **端到端测试**：对比 **DeepSpeed**（ZeRO-2/3） 和 **Colossal-AI**（自动 3D 并行但仅支持选定模型）。由于两者均非全自动流水线，对比时尽量使用其自动模式。
- **消融实验**：比较不同切片策略（均匀权重、均匀时间、Pfeife 不均匀）、不同调度参数（`Nl`, `Bl`, `Bf`）对延迟的影响。

### 实验设置
- 小服务器：8×RTX 3090 24GB（用于覆盖和正确性验证）。
- 大服务器：8×A100 40GB（用于端到端性能测试）。

## 4. 资源与算力

- **覆盖测试**：8×RTX 3090，单次训练迭代，时间未具体说明。
- **端到端测试**：8×A100 40GB，NVSwitch 互联。具体训练时长未给出，但报告了优化搜索时间：
  - ViT-g/14（4 batches, 406 节点）在 10 秒内完成。
  - Stable Diffusion-XL（1645 节点, 8 设备）在约 10 分钟内完成。
- **能耗与计算总量**：论文未直接报告总 GPU 小时数。

## 5. 实验数量与充分性

- **覆盖测试**：49 个模型中 37 个成功（输出一致），5 个因 PyTorch 图断裂问题失败，4 个因多进程序列化错误，2 个编译错误，1 个结果错误。覆盖范围较广，但受限于 PyTorch 自身能力。
- **端到端性能**：对 4 个主要模型在不同设备数（2、4、8）和不同微批次数下共约 12 组对比实验；Stable Diffusion 测试了混合数据并行的多种配置。
- **消融实验**：
  - 验证成本模型准确性（估计 vs 实际延迟/内存）。
  - 展示不同调度参数对性能的影响（图 6）。
  - 对比三种切片策略（图 6 柱状图）。
  - 单独分析预取和不均匀切片的协同效果（图 7）。
- **充分性评估**：实验设计较全面，对比方法选取了主流工具（DeepSpeed, Colossal-AI），但注意到 DeepSpeed 不提供全自动流水线（需手动写层序），Colossal-AI 仅支持有限模型，因此对比有一定不对称性。消融实验充分解释了设计选择。实验结果客观，报告中 Pfeife 在少数场景（ViT 8设备 batch=16）比 DeepSpeed 慢 — 体现对比的诚实性。

## 6. 主要结论与发现

1. **自动流水线可行**：Pfeife 能透明地将大模型跨设备并行化，无需用户手动干预。
2. **性能优势**：与现有最优工具相比，Pfeife 在多数任务上吞吐率提升最高达 **22%**（ViT-g/14 4设备 batch=4）。
3. **关键发现**：
   - **不均匀切片 + 预取**是全局最优解，而非传统均匀切片。预取可填充前向-后向之间的气泡，使不均匀分配成为可能。
   - **循环调度（looped schedule）** 有效减少初始气泡。
4. **支持非顺序模型**：Pfeife 成功并行化 Stable Diffusion（U-Net），这是现有自动流水线工具无法做到的。
5. **成本模型准确**：估计延迟与实测偏差大部分在 30-60ms 内，峰值内存估计保守且误差 <10%。

## 7. 优点

- **完全自动化**：用户只须调用 `torch.compile(..., backend=pfeife_compiler)` 并稍改训练循环，无需任何手动切分或注释。
- **透明集成**：基于 PyTorch 原生编译框架，不侵入模型定义。
- **通用性**：适用于任意计算图，包括带跳跃连接的非顺序模型。支持混合数据并行（SDXL 示例）。
- **联合优化**：同时搜索切片和调度参数，避免分开优化的次优陷阱。
- **成本模型通用且高效**：基于关键路径分析，不受特定调度策略限制，束搜索在大多数模型上只需数秒到数分钟。
- **实验设计细致**：明确展示了成本模型误差、参数影响、与现有工具的公平对比，并证明了不均匀切片+预取的优越性。

## 8. 不足与局限

- **PyTorch 依赖**：部分模型（11/49）因 PyTorch 自身问题无法编译，限制了适用范围。
- **小节点场景性能退化**：当单节点前向时间 <6ms 时，Python 线程与 CUDA 内核间的开销会主导性能，优化器会自动拒绝这些切片。
- **大 batch 时可能不如成熟工具**：在 ViT 8设备 batch=16 时，DeepSpeed 更快（因为其工程优化更成熟，且此时管道气泡占比小）。
- **不支持所有调度策略**：如 kFkB、Chimera 等无法用参数化表达，但作者指出它们内存需求过高，对当前大模型不实用。
- **优化时间在超大模型上仍较长**：Stable Diffusion-XL 且 8 设备时优化约 10 分钟，对于需要频繁重配的场景可能不可接受。
- **未探索多节点场景**：实验限于单机多 GPU，多节点情况下的通信开销和扩展性待验证。
- **缺乏细粒度算子内并行（tensor parallelism）结合**：Pfeife 专注于操作级流水线，未与张量并行（如 Megatron-LM TP）深度融合，在极端大模型上可能仍需混合并行。

（完）
