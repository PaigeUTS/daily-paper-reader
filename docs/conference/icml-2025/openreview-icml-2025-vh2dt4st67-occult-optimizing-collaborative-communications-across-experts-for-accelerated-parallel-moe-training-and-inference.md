---
title: "Occult: Optimizing Collaborative Communications across Experts for Accelerated Parallel MoE Training and Inference"
title_zh: Occult：优化专家间的协作通信以加速并行MoE训练与推理
authors: "Shuqing Luo, Pingzhi Li, Jie Peng, Yang Zhao, Yu Cao, Yu Cheng, Tianlong Chen"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=vh2Dt4sT67"
tags: ["query:agents-os"]
score: 9.0
evidence: 减少大规模MoE训练中的通信开销
tldr: "MoE架构在大规模训练中面临严重的通信瓶颈，消耗超过40%的运行时间。本文定义了协作通信概念，并提出系统和算法层面的创新来减少专家间的通信开销。实验表明，该方法显著加速了并行MoE训练与推理过程，提升了异构计算资源的利用效率。"
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-vh2dt4st67/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 843, \"height\": 695, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vh2dt4st67/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 831, \"height\": 597, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vh2dt4st67/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 826, \"height\": 273, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vh2dt4st67/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1755, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vh2dt4st67/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1681, \"height\": 414, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vh2dt4st67/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 622, \"height\": 212, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vh2dt4st67/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 622, \"height\": 235, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vh2dt4st67/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1667, \"height\": 340, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vh2dt4st67/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1761, \"height\": 760, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vh2dt4st67/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 853, \"height\": 657, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vh2dt4st67/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1758, \"height\": 397, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vh2dt4st67/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1760, \"height\": 431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vh2dt4st67/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 841, \"height\": 703, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-vh2dt4st67/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1758, \"height\": 433, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-vh2dt4st67/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 846, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vh2dt4st67/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 851, \"height\": 487, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vh2dt4st67/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1773, \"height\": 533, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vh2dt4st67/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1772, \"height\": 1092, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vh2dt4st67/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1773, \"height\": 1094, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-vh2dt4st67/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1773, \"height\": 1094, \"label\": \"Table\"}]"
motivation: MoE大规模训练中通信开销巨大，限制了可扩展性。
method: 提出协作通信定义，并从系统和算法层面设计优化方法减少通信量。
result: 在大规模训练中显著降低通信时间，加速训练和推理。
conclusion: 本工作有效缓解了MoE通信瓶颈，提升了分布式训练效率。
---

## Abstract
Mixture-of-experts (MoE) architectures could achieve impressive computational efficiency with expert parallelism, which relies heavily on all-to-all communication across devices. Unfortunately, such communication overhead typically constitutes a significant portion of the total runtime, hampering the scalability of distributed training and inference for modern MoE models (consuming over 40% runtime in large-scale training). In this paper, we first define $\textit{collaborative communication}$ to illustrate this intrinsic limitation, and then propose system- and algorithm-level innovations to reduce communication costs. Specifically, given a pair of experts co-activated by one token, we call them as $\textit{collaborated}$, which comprises $2$ cases as $\textit{intra-}$ and $\textit{inter-collaboration}$, depending on whether they are kept on the same device. Our pilot investigations reveal that augmenting the proportion of intra-collaboration can accelerate expert parallel at scale. It motivates us to strategically $\underline{\texttt{o}}$ptimize $\underline{\texttt{c}}$ollaborative $\underline{\texttt{c}}$omm$\underline{\texttt{u}}$nication for acce$\underline{\texttt{l}}$era$\underline{\texttt{t}}$ed MoE training and inference, dubbed $\textbf{\texttt{Occult}}$. Our designs are capable of $\underline{either}$ delivering exact results with reduced communication cost, $\underline{or}$ controllably minimizing the cost with collaboration pruning, materialized by modified fine-tuning. Comprehensive experiments on various MoE-LLMs demonstrate that $\texttt{Occult}$ can be faster than popular state-of-the-art inference or training frameworks (over 50% speed up across multiple tasks and models) with comparable or superior quality compared to the standard fine-tuning. Codes will be available upon acceptance.

---

## 论文详细总结（自动生成）

# 论文《Occult》详细中文总结

## 一、核心问题与整体含义（研究动机和背景）

- **核心问题**：混合专家（MoE）架构在专家并行（expert parallelism）下高度依赖设备间的 all-to-all 通信，而这种通信开销在大型训练中往往占据总运行时间的 40% 以上，严重限制了分布式训练与推理的可扩展性。
- **研究动机**：现有 MoE 库（如 Tutel、MegaBlocks）在通信密集型任务（如大 batch 训练、长序列预填充、并发生成解码）中性能瓶颈明显，亟需优化通信效率。
- **整体含义**：本文从“协作通信”这一新视角出发，通过最大化同一设备内专家协作（intra-collaboration）、最小化跨设备协作（inter-collaboration），设计系统和算法协同优化方案，旨在加速 MoE 模型的训练与推理，同时保持模型质量。

## 二、方法论：核心思想与技术细节

### 2.1 核心思想
- **协作通信定义**：若一个 token 同时激活两个专家 \(E_i\) 和 \(E_j\)，则称它们为“协作”。同设备内协作称为“intra-collaboration”，跨设备称为“inter-collaboration”。
- **通信复杂度度量**：提出 CT（每个 token 的平均副本数），作为 all-to-all 通信预算的指标。CT 与运行时呈强线性相关。
- **优化目标**：通过增大 intra-collaboration 比例、降低 inter-collaboration 比例来压缩 CT，从而减少通信开销。

### 2.2 关键技术细节

#### (a) 稀疏矩阵乘法（SMM）与双向重索引矩阵（BRIM）
- 设计 **BRIM** 数据结构统一管理三种 token 状态：原始态 ORI、简化态 SFD、扩展态 EPD。
- BRIM 提供两个函数：
  - **Merging**：将 EPD 合并为 SFD，再合并为 ORI（与 All-to-All 结合）。
  - **Scattering**：将 ORI 分散为 SFD，再分散为 EPD（与专家计算结合）。
- 基于 Triton 实现 BRIM 的 SMM 核，每个 thread-block 处理 BRIM 的一行子向量，实现瓦片化矩阵乘法，支持设备内预聚合。

#### (b) 专家放置重调度（Expert Placement Rescheduling）
- 利用 profiling 数据集构建协作频率图 \(P \in \mathbb{R}^{N_e \times N_e}\)。
- 设计聚类算法（Algorithm 1）：依次为每个设备选择协作最紧密的专家，使设备内专家协作最大化、设备间协作最小化。
- 相比随机放置，该方法在保持精确计算的前提下降低 CT 约 20%。

#### (c) 专家协作剪枝（Collaboration Pruning）
- 纯系统方法（动态优化放置）因 mini-batch 中专家连通子图迅速收敛为完全图而不可行，故采用算法-系统协同设计。
- **路由分数剪枝**：对每个 token 的 gating 分数排序，只在预先指定的 \(N_d\) 个设备范围内选取 top-k 专家。
- **专家相似性剪枝**：基于 profiling 数据计算专家 cos 相似度，当所选专家超出设备范围时，用最相似且未选中的同设备专家替换。
- 两种剪枝均可通过微调实现可控的 CT 最小化，通常限制在 2 个设备内可保持模型性能。

#### 算法流程（PyTorch 伪码，Algorithm 2）
1. 路由网络输出 top-k 专家 ID 和权重。
2. 构建 BRIM_0 用于 Dispatch 和 Combine。
3. Dispatch：根据 BRIM_0 选择性复制 token → SFD 态。
4. 第一次 All-to-All 通信：将 SFD token 分发给对应设备。
5. 构建 BRIM_1 用于专家计算。
6. 稀疏矩阵乘法（Scattering）：SFD → EPD，包含权重调制。
7. 稀疏矩阵乘法（Merging）：EPD → SFD。
8. 第二次 All-to-All 通信：聚合结果。
9. Combine：根据 BRIM_0 合并 token 副本 → ORI 态。

## 三、实验设计

### 3.1 模型与数据集
- **模型**：三个前沿 MoE-LLM：OLMoE-1B-7B、Qwen1.5-MoE-A2.7B、DeepSeek-MoE。
- **任务**：训练和推理三个阶段：预填充（prefilling）、解码（decoding）、训练（training）。
- **评测数据集**：
  - 主实验：Winogrande、WSC、PIQA、RACE、MathQA、RTE。
  - 全面评估（附录）：共 23 个基准，包括 ASDiv、OpenBookQA、HellaSwag、SST-2、MultiNLI、QASPER、MRPC、MultiRC、WNLI、QNLI、MMLU、SciQ、PROST、BoolQ、COPA、LogiQA、COQA 等。
- **微调数据**：Alpaca 数据集。

### 3.2 对比方法
- **推理框架**：vllm、HuggingFace。
- **训练框架**：PyTorch FSDP、DeepSpeed。
- **MoE 专用库**：Tutel、MegaBlocks（包括 block-sparse 和 grouped GeMM 两种模式）。

### 3.3 评估指标
- 主要指标：准确率（Accuracy），附录中还报告了 F1 和 Exact Match。

### 3.4 实验场景
- **预填充**：固定 prompt tokens = 214，比较延迟。
- **解码**：固定 prompt tokens = 12800，batch size = 512，完整生成延迟。
- **训练**：序列长度 512，batch size 变化，平均每步延迟（1k 步）。
- **并行配置**：4、8、16 路专家并行。

## 四、资源与算力

- **硬件**：单节点，使用 NVIDIA A6000 GPU（48GB HBM，PCIe 连接），共使用 4、8、16 块 GPU 分别进行实验。
- **软件**：BFloat16 存储参数和激活；CUDA atomic add 使用 Float32；基于 Triton 实现自定义核。
- **训练时长**：文中未明确给出总训练时长或具体小时数，仅报告了每步延迟。微调时冻结非 MoE 层，只更新 MoE 模块，共 1k 步迭代。因此无法直接计算总 GPU 时数。

## 五、实验数量与充分性

- **实验量级**：非常丰富。
  - 3 个模型 × 3 个场景（预填充/解码/训练）× 多个 batch size × 多种 GPU 数 × 多种剪枝策略（无剪枝、1GPU 剪枝、2GPU 剪枝）⇒ 大量组合。
  - 全面评估在 23 个基准上进行，包括准确率、F1、EM 指标。
- **消融实验**：
  - 对比路由分数剪枝 vs 相似性剪枝。
  - 对比不同设备数（1 GPU vs 2 GPU vs 4 GPU）。
  - 对比专家放置重调度 vs 原始放置。
- **公平性**：与 SOTA 框架在同一硬件环境下对比，控制 batch size 和 sequence length；Occult 独立于框架可正交集成；MegaBlocks 的两种模式均被比较。实验设计客观全面。
- **充分性**：覆盖了训练和推理的典型通信密集型场景，并验证了剪枝后模型质量（23个基准）。不足之处在于未进行跨节点（多机）实验。

## 六、主要结论与发现

1. **通信开销显著**：大规模 MoE 训练中 all-to-all 通信占用 >40% 运行时，CT 与运行时强线性相关。
2. **Occult 加速效果**：
   - 预填充阶段：相比 Tutel 加速 2.74~8.66×；相比 MegaBlocks 加速 0.66~1.70×；相比 vllm 加速 1.51~1.86×。
   - 解码阶段：在大 batch 下表现最佳，小 batch 时加速有限。
   - 训练阶段：batch size=8 时，相比 MegaBlocks 加速 1.54×，相比 FSDP 2.65×，相比 DeepSpeed ~9×，相比 Tutel ~20×。
3. **协作剪枝的效果**：
   - 限制在 2 个设备内剪枝，可以达到与标准 top-k 训练相当甚至更好的模型质量。
   - 相似性剪枝整体优于路由分数剪枝。
4. **动态专家放置不可行**：mini-batch 中专家连通子图快速增长为完全图，导致优化无解，因此需采用固定重调度 + 剪枝的协同设计。
5. **可扩展性**：Occult 在 8 和 16 路专家并行下仍保持稳定的加速趋势，且内存效率更高（支持更大 batch size）。

## 七、优点

- **新颖视角**：首次从“协作通信”角度审视 MoE all-to-all 通信，提出 intra/inter 分类，为优化提供了直观依据。
- **算法-系统协同设计**：不仅优化系统实现（SMM、BRIM），还从算法层面剪枝路由，实现可控的通信最小化，且不影响精度。
- **正交可集成**：Occult 的通信优化与现有框架（vllm、DeepSpeed 等）正交，便于嵌入使用。
- **实验全面扎实**：覆盖多个前沿 MoE 模型、多种任务场景、多种 GPU 规模，并在 23 个基准上验证模型质量，结论可信。
- **实际加速显著**：在通信密集型任务上实现 1.5× 以上的加速，且内存更高效。

## 八、不足与局限

1. **负载均衡未处理**：论文明确指出未解决专家间负载不均匀问题，这可能在高负载下导致部分 GPU 计算过载或 idle。
2. **实验环境局限**：所有实验仅在单节点 PCIe 连接的 GPU 上进行，未验证多节点、NVLink 等高带宽场景下的性能。节点间通信可能是更大规模部署的关键瓶颈。
3. **固定剪枝策略**：剪枝时预先设定设备数范围（如 2 设备），未探索自适应或自动搜索最优设备数的方法。
4. **额外调优成本**：协作剪枝需要基于 profiling 数据构建相似度表或重调度放置，引入了预处理阶段。对于快速变化的部署场景可能不够灵活。
5. **模型质量波动**：在单设备剪枝下，部分 benchmark 性能下降明显；不同模型对剪枝的容忍度不同（如 DeepSeek-MoE 的 raw off-the-shelf 模型在 7 个基准上表现最优，表明剪枝存在偏差风险）。
6. **未评估更大规模模型**：仅测试了参数小于 16B 的模型，未在千亿参数级 MoE（如 Mixtral-8x22B, DeepSeek-V3）上进行实验，可扩展性仍需验证。
7. **资源算力信息不完整**：未提供总 GPU 小时数或训练总能耗，不利于与其他方法做成本对比。

（完）
