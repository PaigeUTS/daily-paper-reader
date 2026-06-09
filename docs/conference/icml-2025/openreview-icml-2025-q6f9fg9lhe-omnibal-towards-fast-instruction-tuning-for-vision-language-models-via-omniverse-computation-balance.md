---
title: "OmniBal: Towards Fast Instruction-Tuning for Vision-Language Models via  Omniverse Computation Balance"
title_zh: "OmniBal: 通过全宇宙计算平衡实现视觉语言模型的快速指令微调"
authors: "Yongqiang Yao, Jingru Tan, Feizhao Zhang, Jiahao Hu, Yazhe Niu, JinXin, Bo Li, Pengfei Liu, Ruihao Gong, Dahua Lin, Ningyi Xu"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=q6f9Fg9LHe"
tags: ["query:agents-os"]
score: 6.0
evidence: 处理分布式训练中异构设备间的计算负载不均衡
tldr: 针对视觉语言指令微调大规模并行训练中视觉与语言部分异构导致的计算负载不均衡问题，提出OmniBal方法，从数据、模型和内存三个视角重新平衡跨设备计算负载，通过搜索方法优化数据分组和设备分配，显著提升训练效率且保持模型性能。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-q6f9fg9lhe/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1678, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q6f9fg9lhe/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1578, \"height\": 787, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q6f9fg9lhe/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1664, \"height\": 506, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-q6f9fg9lhe/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1579, \"height\": 380, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-q6f9fg9lhe/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 860, \"height\": 144, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q6f9fg9lhe/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 857, \"height\": 949, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q6f9fg9lhe/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1738, \"height\": 382, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q6f9fg9lhe/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1744, \"height\": 292, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q6f9fg9lhe/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1746, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q6f9fg9lhe/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1750, \"height\": 180, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q6f9fg9lhe/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 852, \"height\": 270, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q6f9fg9lhe/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 857, \"height\": 196, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q6f9fg9lhe/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 891, \"height\": 235, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q6f9fg9lhe/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1736, \"height\": 370, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q6f9fg9lhe/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1596, \"height\": 254, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q6f9fg9lhe/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1592, \"height\": 234, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q6f9fg9lhe/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1238, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q6f9fg9lhe/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1239, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q6f9fg9lhe/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1587, \"height\": 214, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q6f9fg9lhe/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1677, \"height\": 321, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-q6f9fg9lhe/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1675, \"height\": 336, \"label\": \"Table\"}]"
motivation: 大规模3D并行训练视觉语言模型时，视觉和语言部分的异构性导致计算负载不均衡，影响分布式训练效率。
method: 从数据、模型和内存三维度重新平衡计算负载：数据层面实例被重组为均衡迷你批次，模型和内存层面采用搜索方法优化设备间分配。
result: 在多个视觉语言微调任务上，OmniBal显著加速训练并保持模型精度，优于现有负载均衡方法。
conclusion: OmniBal为异构混合模型的高效并行训练提供了有效负载均衡方案，可推广至其他异构计算场景。
---

## Abstract
Vision-language instruction-tuning models have recently achieved significant performance improvements. In this work, we discover that large-scale 3D parallel training on those models leads to an imbalanced computation load across different devices. The vision and language parts are inherently heterogeneous:  their data distribution and model architecture differ significantly, which affects distributed training efficiency. To address this issue, we rebalance the computational load from data, model, and memory perspectives, achieving more balanced computation across devices.  Specifically, for the data, instances are grouped into new balanced mini-batches within and across devices. A search-based method is employed for the model to achieve a more balanced partitioning. For memory optimization, we adaptively adjust the re-computation strategy for each partition to utilize the available memory fully. These three perspectives are not independent but are closely connected, forming an omniverse balanced training framework. Extensive experiments are conducted to validate the effectiveness of our method. Compared with the open-source training code of InternVL-Chat, training time is reduced greatly, achieving about 1.8$\times$ speed-up. Our method's efficacy and generalizability are further validated across various models and datasets. Codes will be released at https://github.com/ModelTC/OmniBal.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
处理分布式训练中异构设备间的计算负载不均衡。

### 2. 核心内容
针对视觉语言指令微调大规模并行训练中视觉与语言部分异构导致的计算负载不均衡问题，提出OmniBal方法，从数据、模型和内存三个视角重新平衡跨设备计算负载，通过搜索方法优化数据分组和设备分配，显著提升训练效率且保持模型性能。

### 3. 对应检索需求
heterogeneous compute resources for servers。

### 4. 来源与原文
- Source：ICML-2025-Accepted
- OpenReview：[https://openreview.net/forum?id=q6f9Fg9LHe](https://openreview.net/forum?id=q6f9Fg9LHe)
