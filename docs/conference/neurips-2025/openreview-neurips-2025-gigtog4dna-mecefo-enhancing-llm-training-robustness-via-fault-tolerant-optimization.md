---
title: "MeCeFO: Enhancing LLM Training Robustness via Fault-Tolerant Optimization"
title_zh: MeCeFO：通过容错优化增强大语言模型训练的鲁棒性
authors: "Rizhen Hu, Yutong He, Ran Yan, Mou Sun, Binhang Yuan, Kun Yuan"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=gIGtOg4DNa"
tags: ["query:agents-os"]
score: 4.0
evidence: 分布式大模型训练的容错优化，应对硬件异构故障
tldr: 不相关
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-gigtog4dna/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1351, \"height\": 422, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gigtog4dna/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 895, \"height\": 243, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gigtog4dna/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 512, \"height\": 239, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gigtog4dna/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 688, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gigtog4dna/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 688, \"height\": 371, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gigtog4dna/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 694, \"height\": 389, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-gigtog4dna/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 697, \"height\": 380, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-gigtog4dna/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1109, \"height\": 217, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gigtog4dna/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1442, \"height\": 451, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gigtog4dna/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1437, \"height\": 202, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gigtog4dna/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1443, \"height\": 258, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gigtog4dna/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1437, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gigtog4dna/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1069, \"height\": 396, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gigtog4dna/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1030, \"height\": 179, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gigtog4dna/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1287, \"height\": 176, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gigtog4dna/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1438, \"height\": 234, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gigtog4dna/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1075, \"height\": 136, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-gigtog4dna/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1496, \"height\": 221, \"label\": \"Table\"}]"
motivation: 不相关。
method: 不相关。
result: 不相关。
conclusion: 不相关。
---

## Abstract
As distributed optimization scales to meet the demands of Large Language Model (LLM) training, hardware failures become increasingly non-negligible. Existing fault-tolerant training methods often introduce significant computational or memory overhead, demanding additional resources. To address this challenge, we propose **Me**mory- and **C**omputation- **e**fficient **F**ault-tolerant **O**ptimization (**MeCeFO**), a novel algorithm that ensures robust training with minimal overhead. When a computing node fails, MeCeFO seamlessly transfers its training task to a neighboring node while employing memory- and computation-efficient algorithmic optimizations to minimize the extra workload imposed on the neighboring node handling both tasks. MeCeFO leverages three key algorithmic designs: (i) Skip-connection, which drops the multi-head attention (MHA) module during backpropagation for memory- and computation-efficient approximation; (ii) Recomputation, which reduces activation memory in feedforward networks (FFNs); and (iii) Low-rank gradient approximation, enabling efficient estimation of FFN weight matrix gradients. Theoretically, MeCeFO matches the convergence rate of conventional distributed training, with a rate of $\mathcal{O}(1/\sqrt{nT})$, where $n$ is the data parallelism size and $T$ is the number of iterations. Empirically, MeCeFO maintains robust performance under high failure rates, incurring only a 4.18\% drop in throughput, demonstrating $5.0\times$ to $6.7\times$ greater resilience than previous SOTA approaches.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

大规模语言模型（LLM）训练依赖成千上万GPU组成的分布式集群，硬件故障不可避免（如Meta训练LLaMA 3 405B时平均每4小时一次硬件故障）。现有容错方法（基于检查点、重调度、冗余计算）引入显著的计算或内存开销，降低训练吞吐量。作者指出，这些方法强制精确复现每一步计算，而优化算法（如SGD、Adam）本身对梯度噪声具有鲁棒性，最终目标是模型泛化性能而非严格的计算轨迹。因此，论文提出**MeCeFO**（Memory- and Computation-efficient Fault-tolerant Optimization），通过策略性牺牲计算精度来降低容错开销，同时保持模型性能，实现高效鲁棒训练。

## 2. 论文提出的方法论

### 核心思想：邻居节点分担（Neighbor-Do-Both, NDB）

当节点故障时，同一数据并行（DP）组内的邻居节点接管故障节点的训练任务（包括前向、反向传播），同时负责自身任务。这导致邻居节点内存和计算负载翻倍，造成瓶颈。

### 三项关键技术减少开销

- **Skip-connection（技术I）**：在邻居节点上，对多头注意力（MHA）模块的反向传播中跳过连接，即不计算MHA的权重梯度和激活梯度（Wgrad和Dgrad），并释放MHA的激活内存。实验显示跳过MHA比跳过FFN对训练影响更小。
- **选择性激活重计算（技术II）**：对前馈网络（FFN）模块，邻居节点只保留FFN的输入激活，在反向传播时重计算其他中间激活。这降低了内存占用，但增加了约1/3的FFN计算量。
- **低秩梯度近似（技术III）**：为了补偿重计算带来的计算开销，对FFN权重矩阵的梯度计算采用低秩近似。通过每τ次迭代对权重矩阵进行SVD，取前r个右奇异向量V₁，将梯度近似为$G_W \approx G_y (x^\top V_1) V_1^\top$。当r远小于矩阵维度时，计算量大幅减少。

**收敛性分析**：在标准假设（L-平滑、有界方差、梯度误差有界）下，MeCeFO（采用动量SGD）的收敛率为$\mathcal{O}(1/\sqrt{nT})$，与标准分布式SGD匹配。

完整算法流程见论文Algorithm 1-3，包括前向、反向传播中的分支判断（标准节点 vs 邻居节点）。

## 3. 实验设计

- **数据集**：C4（Colossal Clean Crawled Corpus），用于预训练。
- **模型**：LLaMA三种规模：350M、1B、7B（Decoder-only Transformer）。
- **基准方法**：
  - **Bamboo**（NSDI 23）：基于冗余计算。
  - **Oobleck**（SOSP 23）：基于预计算管道模板动态调整。
  - 对比指标：吞吐量（tokens/s）、验证困惑度、零样本评估、GLUE微调性能。
- **故障场景**（表1）：
  - 低频：每2小时故障，每4小时恢复。
  - 中频：每1小时故障，每3小时恢复。
  - 高频：每0.5小时故障，每2小时恢复。
- **消融实验**：验证各关键技术的贡献（附录C.1）。
- **其他评估**：不对称故障（固定子集故障）、更高故障频率、DeepSeek-V3风格模型（MLA+MoE-1.2B）、梯度误差分布验证（图4-7）。

## 4. 资源与算力

- **硬件**：32块NVIDIA A100 GPU，分为4个节点（每个节点8块）；节点内通信NVLink（600 GB/s），节点间InfiniBand（200 GB/s）。
- **训练配置**：
  - LLaMA-350M：全局batch size 8192，6,000步。
  - LLaMA-1B：全局batch size 4096，20,000步。
  - LLaMA-7B：全局batch size 1024，60,000步。
  - 优化器：AdamW，余弦学习率衰减。
- 论文未明确给出各模型的总训练时长（小时数），但提供了迭代次数可供估算。

## 5. 实验数量与充分性

实验较为充分且设计合理：

- **主要对比实验**（表2-5）：三大模型 × 三种故障频率 × 三种方法，覆盖吞吐量、困惑度、零样本（4个任务）、GLUE微调（8个子任务）。
- **消融实验**（表6）：逐步添加三项技术，展示对内存和吞吐量的贡献（如去掉所有技术后OOM，加入全部后接近无故障性能）。
- **额外验证**：
  - 不对称故障场景（表7）。
  - 更高故障频率（比例相同，表8）。
  - 不同模型结构（MLA+MoE，表10）。
  - 梯度假设验证（图4-7）。
- **公平性**：基线方法使用公开实现，超参数针对无故障优化；故障模型模拟在相同集群上运行。作者声明了代码开源链接。

总体而言，实验覆盖了多种规模、多种故障强度、多种评估维度，足以支撑主要结论。

## 6. 论文的主要结论与发现

- 在高频故障下，MeCeFO在LLaMA-7B上吞吐量仅下降4.18%，而Bamboo下降20.84%，Oobleck下降28.09%，MeCeFO的鲁棒性比SOTA高5.0×~6.7×。
- 模型性能（验证困惑度、零样本、GLUE微调）与无故障基线几乎一致，最大困惑度增加仅2.19%（1B模型高频）。
- 理论上，MeCeFO保持标准的$\mathcal{O}(1/\sqrt{nT})$收敛率。
- 消融实验证实三项关键技术缺一不可，共同实现接近无故障的效率。

## 7. 优点

- **创新性**：首次将内存/计算高效训练技术（skip-connection、激活重计算、低秩近似）系统性应用于分布式容错场景，利用优化算法的鲁棒性放松了精确计算的要求。
- **理论保证**：给出了完整的收敛性分析，证明了与标准分布式SGD相同的收敛率。
- **实验全面**：涵盖多种模型规模、故障频率、评估任务，并提供消融和额外验证。
- **实用性**：实现简单，仅需节点级修改，可与其他系统级容错方法互补。
- **开源代码**：提供了GitHub仓库。

## 8. 不足与局限

- **实验规模**：仅在32块A100上模拟故障，未在更大集群（>100 GPU）上验证；实际大规模集群故障模式可能更复杂（如网络分区、多个同时故障）。
- **故障模型**：假设故障独立且事件驱动，但实际中可能有关联故障；恢复时间也与集群规模相关。
- **理论假设**：收敛分析依赖“梯度误差有界”（Assumption 3），该假设在深层网络下可能不成立；论文虽在7B模型上验证了误差分布（图6-7），但仅限C4数据集。
- **扩展性讨论有限**：论文说明了可扩展到TP，但未给出TP下的具体实验结果；对异构集群的适配也未深入。
- **基线对比**：Bamboo和Oobleck本身吞吐量低于MeCeFO的无故障基线（部分因冗余或调度开销），但对比中未讨论这些方法的额外优势（如保证计算精确性）。
- **消融实验仅在一个节点故障下进行**，未测试多节点同时故障或级联故障场景。
- **未提供训练总能耗或GPU小时数**，难以评估实际成本效益。

（完）
