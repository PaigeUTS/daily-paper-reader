---
title: Shortcut-connected Expert Parallelism for Accelerating Mixture of Experts
title_zh: 短路连接专家并行：加速混合专家模型
authors: "Weilin Cai, Juyong Jiang, Le Qin, junweicui, Sunghun Kim, Jiayi Huang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=GKly3FkxN4"
tags: ["query:agents-os"]
score: 4.0
evidence: MoE专家并行与通信优化，支持大模型训练
tldr: 针对混合专家模型（MoE）在分布式训练中通信瓶颈问题，提出ScMoE架构，通过短路连接和重叠并行策略解耦通信与计算，显著提升训练效率。实验表明该方法有效降低通信开销，加速大模型训练。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-gkly3fkxn4/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 871, \"height\": 503, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gkly3fkxn4/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 854, \"height\": 565, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gkly3fkxn4/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 843, \"height\": 470, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gkly3fkxn4/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1764, \"height\": 602, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gkly3fkxn4/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 799, \"height\": 625, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gkly3fkxn4/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 851, \"height\": 467, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gkly3fkxn4/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 868, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gkly3fkxn4/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1777, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gkly3fkxn4/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1774, \"height\": 510, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gkly3fkxn4/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 868, \"height\": 441, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gkly3fkxn4/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 856, \"height\": 686, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gkly3fkxn4/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 860, \"height\": 460, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gkly3fkxn4/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 863, \"height\": 452, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gkly3fkxn4/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 864, \"height\": 757, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gkly3fkxn4/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 868, \"height\": 758, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-gkly3fkxn4/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 858, \"height\": 345, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gkly3fkxn4/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1766, \"height\": 291, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gkly3fkxn4/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 855, \"height\": 457, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gkly3fkxn4/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 852, \"height\": 278, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gkly3fkxn4/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 669, \"height\": 244, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gkly3fkxn4/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 857, \"height\": 317, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gkly3fkxn4/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 852, \"height\": 257, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gkly3fkxn4/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1475, \"height\": 456, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gkly3fkxn4/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 870, \"height\": 600, \"label\": \"Table\"}]"
motivation: MoE模型中的全对全通信成为瓶颈，现有方法受限于通信与计算的顺序依赖。
method: 设计ScMoE架构，引入短路连接和重叠并行，解耦通信与计算顺序。
result: ScMoE显著降低通信延迟，加速MoE模型训练。
conclusion: ScMoE通过架构与并行策略创新，有效提升MoE训练效率。
---

## Abstract
Expert parallelism has emerged as a key strategy for distributing the computational workload of sparsely-gated mixture-of-experts (MoE) models across multiple devices, enabling the processing of increasingly large-scale models. However, the All-to-All communication inherent to expert parallelism poses a significant bottleneck, limiting the efficiency of MoE models. Although existing optimization methods partially mitigate this issue, they remain constrained by the sequential dependency between communication and computation operations. 
To address this challenge, we propose ScMoE, a novel shortcut-connected MoE architecture integrated with an overlapping parallelization strategy. ScMoE decouples communication from its conventional sequential ordering, enabling up to 100\% overlap with computation.
Compared to the prevalent top-2 MoE baseline, ScMoE achieves speedups of $1.49\times$ in training and $1.82\times$ in inference.
Moreover, our experiments and analyses indicate that ScMoE not only achieves comparable but in some instances surpasses the model quality of existing approaches.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
MoE专家并行与通信优化，支持大模型训练。

### 2. 核心内容
针对混合专家模型（MoE）在分布式训练中通信瓶颈问题，提出ScMoE架构，通过短路连接和重叠并行策略解耦通信与计算，显著提升训练效率。实验表明该方法有效降低通信开销，加速大模型训练。

### 3. 对应检索需求
How does heterogeneous computing support large model training?

### 4. 来源与原文
- Source：ICML-2025-Accepted
- OpenReview：[https://openreview.net/forum?id=GKly3FkxN4](https://openreview.net/forum?id=GKly3FkxN4)
