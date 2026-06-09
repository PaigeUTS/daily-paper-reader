---
title: "PipeOffload: Improving Scalability of Pipeline Parallelism with Memory Optimization"
title_zh: PipeOffload：通过内存优化提升流水线并行可扩展性
authors: "Xinyi Wan, Penghui Qi, Guangxing Huang, Min Lin, Jialin Li"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=O0lxLP4ABD"
tags: ["query:agents-os"]
score: 8.0
evidence: 内存卸载提升流水线并行可扩展性，适用于异构系统上的大模型训练
tldr: 流水线并行中激活内存随微批数量增长，限制可扩展性。本文提出PipeOffload，利用内存卸载策略，发现多数配置下可卸载至少一半激活且开销可忽略；当不能完全卸载时，采用选择性卸载策略亚线性降低峰值内存。集成后显著提升大模型训练的扩展性，对异构计算基础设施优化有直接帮助。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-o0lxlp4abd/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1357, \"height\": 460, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-o0lxlp4abd/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 675, \"height\": 443, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-o0lxlp4abd/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 743, \"height\": 398, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-o0lxlp4abd/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 844, \"height\": 300, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-o0lxlp4abd/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1735, \"height\": 604, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-o0lxlp4abd/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1718, \"height\": 372, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-o0lxlp4abd/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1438, \"height\": 230, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-o0lxlp4abd/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1713, \"height\": 858, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-o0lxlp4abd/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1573, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-o0lxlp4abd/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 831, \"height\": 282, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-o0lxlp4abd/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 847, \"height\": 524, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-o0lxlp4abd/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 856, \"height\": 271, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-o0lxlp4abd/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 831, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-o0lxlp4abd/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1740, \"height\": 339, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-o0lxlp4abd/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1722, \"height\": 877, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-o0lxlp4abd/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 814, \"height\": 504, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-o0lxlp4abd/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 778, \"height\": 541, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-o0lxlp4abd/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1663, \"height\": 799, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-o0lxlp4abd/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1392, \"height\": 1320, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-o0lxlp4abd/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1698, \"height\": 574, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-o0lxlp4abd/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 892, \"height\": 313, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-o0lxlp4abd/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 891, \"height\": 383, \"label\": \"Table\"}]"
motivation: 流水线并行训练大模型时激活内存消耗巨大，限制可扩展性。
method: 提出内存卸载策略，包括全面卸载和选择性卸载以亚线性降低峰值内存。
result: 实验表明多数配置下可卸载大部分激活，显著提升可扩展性。
conclusion: PipeOffload是一种有效的内存优化方法，能够增强异构计算环境下的模型训练能力。
---

## Abstract
Pipeline parallelism (PP) is widely used for training large language models (LLMs), yet its scalability is often constrained by high activation memory consumption as the number of in-flight microbatches grows with the degree of PP. In this paper, we focus on addressing this challenge by leveraging the under-explored memory offload strategy in PP. With empirical study, we discover that in the majority of standard configurations, at least half, and potentially all, of the activations can be offloaded with negligible overhead. In the cases where full overload is not possible, we introduce a novel selective offload strategy that decreases peak activation memory in a better-than-linear manner. Furthermore, we integrate memory offload with other techniques to jointly consider overall throughput and memory limitation. Our experiments proves that the per-device activation memory effectively reduces with the total number of stages, making PP a stronger alternative than TP, offering up to a 19\% acceleration with even lower memory consumption.

---

## 论文详细总结（自动生成）

# 论文 PipeOffload：通过内存优化提升流水线并行可扩展性 — 中文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：流水线并行（Pipeline Parallelism, PP）在大语言模型训练中广泛使用，但其可扩展性受到激活内存（activation memory）的严重限制。随着 PP 的度数（stage 数量）增加，设备上同时驻留的微批（microbatch）数量也随之增加，导致每设备激活内存几乎不随 stage 数增加而下降，从而阻碍 PP 扩展到更多 GPU。
- **研究动机**：现有方法如激活重计算（activation rematerialization）会带来显著计算开销；而内存卸载（memory offload）在数据并行中已被广泛采用，但在 PP 中尚未充分探索。PP 中前向与反向之间存在自然的时间窗口，可以将激活卸载到主机内存并重叠计算，理论上可实现“免费午餐”（free lunch）——在不影响吞吐的情况下显著降低显存占用。
- **整体含义**：本文旨在通过精心设计的内存卸载策略，突破 PP 的激活内存瓶颈，使 PP 成为一种比张量并行（Tensor Parallelism, TP）更具竞争力的模型并行方案，最高可带来 19% 的训练加速，同时内存消耗更低。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：利用 PP 中前向与反向之间的时间空隙，将激活数据从 GPU 卸载到主机内存，并在后续反向前重新加载，通过异步流重叠计算与传输，实现几乎零开销的内存节省。
- **关键技术细节**：
    - **全卸载可行性判据**：定义比例 \( k = T_o / T_c \)，其中 \( T_o \) 为单个 transformer 层激活的往返传输时间（Device-to-Host + Host-to-Device），\( T_c \) 为该层前向+反向总计算时间。若 \( k \leq 1 \)，则可完全卸载所有激活而不会影响吞吐。公式推导给出：
      \[
      k = \frac{T_o}{T_c} = \frac{10}{3(6h + s)} \cdot \frac{B_c}{B_o}
      \]
      其中 \( h \) 为隐藏层大小，\( s \) 为序列长度，\( B_c \) 为 GPU 计算带宽，\( B_o \) 为 PCI-E 双向带宽。
    - **选择性卸载策略**：当 \( k > 1 \) 时，不能完全卸载所有激活。本文提出优先卸载生命周期更长的 stage（即前向到反向间隔大的 stage），因为其对峰值内存贡献更大。结合均匀重复策略（uniform repeating），可实现“优于线性”（better-than-linear）的峰值内存降低——例如卸载一半 stage 可降低约 3/4 的峰值内存。
    - **调度优化**：提出广义的 interleaving 策略（Generalized Interleaved Schedule, GIS）和 GIS-H（将峰值内存降至约 half）。进一步设计 PipeOffload 系列调度（PO-H 卸载半数 stage，PO-F 卸载全部 stage），在吞吐和内存之间实现平滑权衡。
- **算法流程（文字说明）**：
    1. 根据模型配置和硬件带宽计算 \( k \)。
    2. 若 \( k \leq 1 \)，采用全卸载，将激活在每次 forward 后立即开始卸载，并在最后一次 backward 前重新加载，通过单流调度确保稳定时序。
    3. 若 \( k > 1 \)，采用选择性卸载：利用均匀重复策略，将多个 stage 按生命周期排序，优先卸载最长的 stage，直到满足内存约束。
    4. 结合 GIS 或 GIS-H 缩短 warmup 阶段的前向次数，进一步减少峰值激活数。
    5. 实际实现中采用拓扑感知的卸载调度（同一 PCI-E switch 下的 GPU 交错执行卸载），使用连续主机缓冲区减少内存浪费，并对 LayerNorm、GeLU 等轻量层进行重计算以降低需卸载的激活量。

## 3. 实验设计：使用的数据集/场景、benchmark、对比方法

- **数据集/场景**：使用 GPT-3 类模型（自回归语言模型），训练任务为标准语言建模（未指定具体数据集，重点在系统性能而非收敛）。
- **Benchmark**：主要指标为模型浮点利用率（Model Flops Utilization, MFU）和每设备峰值激活内存（activation memory）。激活内存定义为峰值减去迭代开始时的内存。
- **对比方法**：
    - 基线：1F1B、Interleaved 1F1B（1F1B-I）（出自 Megatron-LM）。
    - 本文方法：GIS、GIS-H、PO-H（卸载半数 stage）、PO-F（卸载全部 stage）。
    - 其他相关方法：V-Min、V-Half（出自 Qi et al. 2024）、1F1B-I 结合激活重计算（1F1B-I-R）。
    - 与 TP 混合并行对比：1F1B-I 配合 TP8（张量并行度 8）+ 序列并行。
- **模型规模**：测试了 5.8B、10.5B、18.1B、42.9B、66.6B、83.8B 参数量的模型，均使用 GQA（query group=8）。具体配置见表 2。

## 4. 资源与算力

- **GPU 型号与数量**：NVIDIA A100 80GB，最多 32 张（4 节点），节点间通过 RoCE RDMA 网络互联。
- **训练时长**：文中未明确给出完整训练时长，实验多为短时间性能测试（测量 MFU 和内存），未进行完整收敛训练（仅收敛实验中运行了 1000 步）。
- **其他硬件细节**：PCI-E 带宽估计为 15 GB/s，GPU 计算带宽 220 TFLOPS。

## 5. 实验数量与充分性

- **实验组数**：涵盖了多种变量组合：
    - 模型规模（6 种，从 5.8B 到 83.8B）。
    - 序列长度（4096、8192、16384、32768）。
    - GPU 数量（8、16、32）。
    - 卸载策略（无卸载、GIS、GIS-H、PO-H、PO-F）。
    - 与其他方法对比（V-Min、V-Half、1F1B-I-R）在不同模型和序列长度下。
    - 消融实验：不同卸载 stage 数量对内存的影响（图 9）、拓扑感知调度对比（附录 D）、重计算开销（附录 C）。
    - 收敛实验：在 5.4B 模型、8 GPU、seq 长情况下运行 1000 步，比较训练损失曲线。
- **充分性与公平性**：
    - 实验覆盖了主流配置，数据点较多（如图 15 给出了详细数值表格）。
    - 对比方法均为开源实现或作者复现，且开源了自己的实现（附 URL），可重复性较好。
    - 但部分场景（如大模型长序列）出现 OOM，因此部分数据缺失，但作者已解释原因。
    - 收敛实验仅验证了梯度正确性（损失曲线一致），未进行完整训练验证。

## 6. 论文的主要结论与发现

- **全卸载的可行性**：在大多数标准配置下（隐藏尺寸 ≥ 8k 或序列长度 ≥ 16k），k ≤ 1，可以完全卸载所有激活而吞吐几乎无下降（甚至因减少内存分配而更优）。
- **选择性卸载的“优于线性”效果**：通过卸载生命周期最长的 stage，峰值激活内存的下降速度超过线性比例（例如卸载一半 stage 可降低约 3/4）。
- **性能提升**：PO-F 相比标准 Interleaved 1F1B + TP8，可达到 **12%-19% 的 MFU 提升**，同时内存更低，证明纯 PP 结合内存卸载可替代 TP 成为更优方案。
- **内存可扩展性**：PO-F 的每设备激活内存随总 stage 数增加而保持恒定（约 4 个 transformer 层的激活），而传统方法几乎线性增长。
- **收敛正确性**：损失曲线与基线完全一致，说明该方法在数值上是精确的。

## 7. 优点：方法或实验设计上的亮点

- **方法创新**：
    - 提出“免费午餐”概念，基于 PCI-E 与计算带宽的比值定量评估卸载可行性。
    - 选择性卸载策略利用生命周期和调度模式实现亚线性内存降低。
    - 引入广义 interleaving 调度（GIS、GIS-H），在不增加气泡的情况下降低内存。
- **工程实践**：
    - 实现了单流卸载调度，避免多流导致的延迟波动。
    - 拓扑感知的卸载同步（同一 PCI-E switch 下 GPU 交错执行），提升带宽稳定性。
    - 连续主机缓冲区减少内存碎片，确定性设备内存管理避免频繁 cudaMalloc。
- **实验设计**：
    - 对比方法全面，包括领域最新成果（V-Min、V-Half）。
    - 可视化内存模式（图 2）和卸载对吞吐的影响（图 1）直观。
    - 提供了强扩展性分析（图 10），展示每设备激活内存随 stage 数变化。

## 8. 不足与局限

- **硬件依赖性**：卸载效率高度依赖 PCI-E 带宽与计算带宽的比值。A100 上表现良好，H100 等新硬件类似，但若 PCI-E 成为瓶颈（如多路 DMA 争抢），可能无法达到“免费午餐”。
- **主机内存限制**：虽然主机内存通常远大于 GPU 内存，但在极端大模型或长序列场景下（如 83.8B + seq 32768）仍然可能出现主机 OOM（文中提及 OOM(H)）。
- **实验覆盖性**：
    - 未在数百 GPU 的大规模集群上测试（最多 32 GPU），可扩展性结论需进一步验证。
    - 未测试跨节点通信对卸载的影响（作者认为 P2P 通信量远小于卸载，但未实际测量干扰）。
    - 收敛实验仅运行 1000 步，未完成完整训练。
- **应用限制**：
    - 当 k > 1 且内存预算极低时，需要更多 stage 卸载，可能导致吞吐下降（如 PO-F 在不满足 k≤1 时文中选择跳过）。
    - 方法假设每个设备上运行多个 stage（interleaved），若仅运行一个 stage（v=1），选择性卸载的自由度变小。
- **评价偏倚风险**：作者为 Sea AI Lab 和 NUS，与 Megatron-LM 等基线实现可能存在系统级差异（如代码优化程度），但已开源可验证。

（完）
