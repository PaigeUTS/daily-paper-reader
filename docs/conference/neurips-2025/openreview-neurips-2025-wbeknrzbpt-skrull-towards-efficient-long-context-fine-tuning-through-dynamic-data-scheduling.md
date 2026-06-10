---
title: "Skrull: Towards Efficient Long Context Fine-tuning through Dynamic Data Scheduling"
title_zh: "Skrull: 面向高效长上下文微调的动态数据调度"
authors: "Hongtao Xu, Wenting Shen, Yuanxin Wei, Ang Wang, Guo Runfan, Tianxing Wang, Yong Li, Mingzhen Li, Weile Jia"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=WBEknRZBpT"
tags: ["query:agents-os"]
score: 5.0
evidence: 针对异构序列长度的动态数据调度
tldr: 长上下文微调中长短序列混合导致训练效率低下，本文提出Skrull，从数据调度新视角出发，动态调整数据顺序以匹配计算资源，显著提升端到端系统性能，缓解异构数据分布带来的挑战，为资源调度提供思路。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-wbeknrzbpt/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 679, \"height\": 513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wbeknrzbpt/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 657, \"height\": 487, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wbeknrzbpt/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1426, \"height\": 593, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wbeknrzbpt/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1447, \"height\": 596, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wbeknrzbpt/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1445, \"height\": 452, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wbeknrzbpt/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 727, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-wbeknrzbpt/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 721, \"height\": 439, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-wbeknrzbpt/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1297, \"height\": 221, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wbeknrzbpt/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1450, \"height\": 353, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wbeknrzbpt/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 499, \"height\": 258, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wbeknrzbpt/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 654, \"height\": 258, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wbeknrzbpt/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1458, \"height\": 1060, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-wbeknrzbpt/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1261, \"height\": 475, \"label\": \"Table\"}]"
motivation: 长上下文微调中异构序列长度分布导致训练系统效率低下。
method: 提出动态数据调度方法，根据序列长度优化训练批次顺序。
result: 在保持模型性能的同时显著提升训练吞吐量。
conclusion: Skrull有效应对异构数据分布，提升长上下文微调效率。
---

## Abstract
Long-context supervised fine-tuning (Long-SFT) plays a vital role in enhancing the performance of large language models (LLMs) on long-context tasks. To smoothly adapt LLMs to long-context scenarios, this process typically entails training on mixed datasets containing both long and short sequences. However, this heterogeneous sequence length distribution poses significant challenges for existing training systems, as they fail to simultaneously achieve high training efficiency for both long and short sequences, resulting in sub-optimal end-to-end system performance in Long-SFT.
In this paper, we present a novel perspective on data scheduling to address the challenges posed by the heterogeneous data distributions in Long-SFT. We propose Skrull, a dynamic data scheduler specifically designed for efficient long-SFT. Through dynamic data scheduling, Skrull balances the computation requirements of long and short sequences, improving overall training efficiency. Furthermore, we formulate the scheduling process as a joint optimization problem and thoroughly analyze the trade-offs involved. Based on those analysis, Skrull employs a lightweight scheduling algorithm to achieve near-zero cost online scheduling in Long-SFT. Finally, we implement Skrull upon DeepSpeed, a state-of-the-art distributed training system for LLMs. Experimental results demonstrate that Skrull outperforms DeepSpeed by 3.76x on average (up to 7.54x) in real-world long-SFT scenarios.

---

## 论文详细总结（自动生成）

## 论文详细中文总结

### 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：长上下文能力对大语言模型（LLM）处理长文档摘要、问答、多轮对话等任务至关重要。标准做法是通过长上下文监督微调（Long-SFT）或继续预训练（Long-CPT）来扩展上下文长度。然而，Long-SFT 训练数据往往混合了极长和极短的序列（例如 Llama3 中 99.89% 的序列平均低于 1K tokens，而 0.11% 的序列约为 37K tokens），这种异构的序列长度分布给现有分布式训练系统（如 DeepSpeed）带来了巨大挑战。
- **整体问题**：现有系统无法同时高效处理长短序列。长序列需要上下文并行（CP）等内存节省策略，但这些策略对短序列引入不必要的通信开销和 GPU 利用率不足，导致端到端训练效率严重下降。例如，短序列在高 CP 度下内核执行效率降低，且通信开销占比过大。
- **论文目标**：提出一种新的数据调度视角来解决异构数据分布带来的训练效率问题，设计一个动态数据调度器 Skrull，通过智能调度平衡长短序列的计算需求，显著提升 Long-SFT 的端到端性能。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：从数据调度角度出发，通过两层协作的调度机制来优化异构序列的训练效率：(1) **分布式感知上下文并行（DACP）**：在细粒度（微批次内）动态决定是否对序列进行分片（shard）或保留在单设备上，以减少短序列的不必要通信开销，同时保持处理长序列的能力；(2) **全局数据调度（GDS）**：在粗粒度（全局批次）上将序列重新打包成最优的微批次，以平衡不同数据并行（DP）工作节点间的计算负载，并为 DACP 提供更优的调度空间。
- **关键技术细节**：
    - **DACP**：将序列分为“分布式序列”（需要 CP 分片）和“本地序列”（整个序列留在单个 GPU 上）。通过离线性能建模（包括 FLOPs 计算、内存估计、通信延迟），将调度问题形式化为一个联合优化问题（目标是最小化每个微批次的执行时间，满足内存约束）。设计了轻量级启发式算法（Algorithm 1）：优先避免分片、优先平衡计算（而非内存），并引入回滚机制（roll-back）防止 OOM。
    - **GDS**：将全局批次中的序列分配到不同 DP 工作节点的微批次中。同样形式化为联合优化问题（目标是最小化所有 DP 工作节点中最长的累计执行时间）。启发式算法（Algorithm 2）先通过 bin-packing 粗平衡计算负载，再通过交织排序（长短配对）生成微批次，并逐步增加微批次数目直至调度成功（利用回滚机制避免 OOM）。
- **公式/算法流程（文字说明）**：
    - **DACP 优化目标** (公式1-7)：最小化 max_j (Time_j)，其中 Time_j 由通信与本地序列计算的重叠项及分布式序列计算项组成；约束包括序列完整性（每个序列要么分片要么本地分配）及内存约束（每个 rank 的总序列长度不超过 BucketSize C）。
    - **GDS 联合优化** (公式8-11)：最小化 max_i (sum_j Time_ij)，即最慢 DP rank 的总时间；通过 batching 矩阵 B_kij 将序列分配到各 DP rank 的微批次中，每个微批次的 Time_ij 由 DACP 函数计算。
    - **启发式算法**：DACP 算法对序列按长度升序排列，依次尝试分配到当前负载最小的 bucket，若内存不足则尝试分配到剩余空间最大的 bucket，若仍不足则标记为分片，否则触发回滚。GDS 算法先按 FLOPs 排序后执行 bin-packing，再在每 DP rank 内做交织分批，动态增加微批次数量直至满足内存和 DACP 调度约束。

### 3. 实验设计

- **数据集**：三种真实世界 Long-SFT 数据集：
    - **Wikipedia**（长尾分布，87.88% 序列 <1K tokens，最长 78K）
    - **LMsysChat1M**（长尾分布，87.12% <1K，最长 1643K）
    - **ChatQA2-Long-SFT**（双峰分布，约 40% 短序列、60% 长序列，最长 99K）
- **模型**：Qwen2.5-0.5B 和 Qwen2.5-7B
- **基准（Baseline）**：DeepSpeed（SOTA 分布式训练框架），并实现了排序批次方法（LongAlign 中的 sorted batching）作为额外对比。
- **对比方法**：Baseline (DeepSpeed)、Baseline + DACP 单独、Baseline + DACP+GDS 完整、Sorted batching。
- **实验场景**：涵盖不同数据集、不同模型规模、不同并行配置（DP=4, CP=8, BatchSize=64 为主，Qwen-7B+ChatQA2 使用 DP=2, CP=16, BatchSize=40），并进行了 BatchSize 和 BucketSize 影响分析、LoRA 兼容性验证、调度策略对比（随机轮询 vs Skrull，有/无回滚）、以及精度验证（训练损失曲线对比）。

### 4. 资源与算力

- **实验环境**：4 节点集群，每节点 8 块 Nvidia H100 GPU（共 32 块 H100），节点间通过高速 InfiniBand 网络连接，节点内 GPU 通过 900GB/s NVLink 互连。
- **训练时长**：论文未明确给出总训练时长，仅报告了迭代时间对比（即平均每步耗时）。
- **其他细节**：使用 ZeRO-2 优化作为基准；启用了选择性重计算策略。

### 5. 实验数量与充分性

- **主要实验组数**：
    - 总体性能对比：2 个模型 × 3 个数据集 × 3 个对比方法（Baseline, Baseline+DACP, Baseline+GDS+DACP）+ 额外 Sorted Batching 对比，共约 18 组主实验。
    - 逐步消融：在相同配置下分别启用 DACP 和 GDS，显示各自贡献。
    - 参数影响分析：BatchSize 从 8 到 54，BucketSize 从 8K 到 32K。
    - LoRA 兼容性：在 14B、32B 更大模型上测试（仅 2 组）。
    - 调度策略对比：Skrull vs Round-Robin，有/无回滚机制（4 组）。
    - 精度验证：训练损失曲线对比（1 组）。
- **充分性与客观性**：实验覆盖了不同数据分布（长尾与双峰）、不同模型尺寸（0.5B、7B）、不同调度粒度的影响，并提供了消融分析和参数敏感性分析。对比方法包括标准 DeepSpeed 和 Sorted Batching，公平性较好。但缺少与更广泛系统优化方法（如动态并行切换 [8]、Chunkflow [22]）的直接对比。

### 6. 论文的主要结论与发现

- **核心结论**：Skrull 在真实 Long-SFT 场景下平均加速比 DeepSpeed 提高 **3.76×**，最高达 **7.54×**；Qwen-0.5B 平均加速 5.50×，Qwen-7B 平均加速 2.03×。
- **两个组件均有效**：DACP 和 GDS 各自贡献显著，且联合使用效果最佳。
- **性能受 BatchSize、BucketSize、数据集分布影响**：更大 BatchSize 和适当 BucketSize 有利于扩大调度空间；长尾数据集（Wikipedia、LMsysChat1M）优化空间大于双峰数据集（ChatQA2）。
- **回滚机制至关重要**：无回滚机制下调度策略会导致 OOM；Skrull 的启发式算法优于简单轮询策略，在满足内存约束的同时实现更好的计算平衡。
- **不改变收敛性**：精度验证显示 Skrull 与标准训练损失曲线一致，不影响优化轨迹。

### 7. 优点

- **方法创新性强**：从数据调度这一新视角解决异构序列长度带来的效率问题，而非改动训练框架底层并行策略。
- **双层调度设计精巧**：DACP 细粒度处理长短序列分类与分配，GDS 粗粒度优化全局批次组合，二者联合建模为优化问题，并设计轻量启发式算法实现近零开销在线调度。
- **系统性实验设计与分析**：不仅报告平均/峰值加速比，还提供了消融、参数影响、调度策略对比、精度验证、LoRA 兼容性等全面评估，实验充分且结果可信。
- **对异构分布有通用性**：方法不仅适用于 Long-SFT，作者指出可推广到其他混合长短数据的训练场景（如 RLHF）。

### 8. 不足与局限

- **实验覆盖局限**：
    - 仅测试了 Qwen2.5 系列（0.5B、7B），未包含更大规模模型（如 70B 以上）或不同架构（Llama、Mistral）的评估。
    - 未与类似系统级优化方法（如动态并行切换、Chunkflow、LongAlign 的排序批次之外的更多方法）进行广泛直接对比。
    - 数据集仅涵盖三类，虽代表长尾与双峰分布，但缺乏更多样化的真实 Long-SFT 数据（如代码、多模态混合数据）。
- **硬件依赖性**：性能建模（BucketSize 确定、通信延迟曲线）依赖于离线 profiling，在不同硬件配置下可能需重新校准，迁移成本未讨论。
- **回滚机制可能引发重试**：虽然近零开销，但极端批次下回滚次数增加可能导致额外延迟，论文未分析最坏情况。
- **优化空间受 BatchSize 限制**：当全局批量过小时，调度空间有限，加速效果不明显（图 4a 显示 BatchSize 增大到一定程度后速度提升收敛）。
- **对双峰分布数据集增益较小**：当长序列占比较高（如 Qwen-7B + ChatQA2），由于 BucketSize 限制，许多长序列仍需分片，导致加速比仅 1.08× 左右，表明方法在处理严重偏长分布的批次时效率有限。
- **论文未提及代码开源情况**，可重复性受限（仅在论文末尾说明将尽快开源）。

（完）
