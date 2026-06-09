---
title: Mixture of Lookup Experts
title_zh: 混合查找专家
authors: "Shibo Jie, Yehui Tang, Kai Han, Yitong Li, Duyu Tang, Zhi-Hong Deng, Yunhe Wang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=wUEp13rqXP"
tags: ["query:agents-os"]
score: 5.0
evidence: 通过查找表减少VRAM使用，类似神经网络的计算内存架构
tldr: Mixture of Lookup Experts (MoLE)提出了一种新的MoE架构，在推理前将专家网络重新参数化为查找表，从而大幅降低VRAM占用和通信开销。该方法在保持模型质量的同时，解决了大模型部署中的内存瓶颈问题。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-wuep13rqxp/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 848, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wuep13rqxp/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1760, \"height\": 730, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-wuep13rqxp/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 828, \"height\": 412, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-wuep13rqxp/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1642, \"height\": 267, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wuep13rqxp/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1763, \"height\": 704, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wuep13rqxp/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1738, \"height\": 918, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wuep13rqxp/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1749, \"height\": 221, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wuep13rqxp/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1748, \"height\": 310, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wuep13rqxp/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1756, \"height\": 399, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wuep13rqxp/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1727, \"height\": 390, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wuep13rqxp/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1719, \"height\": 312, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-wuep13rqxp/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 778, \"height\": 783, \"label\": \"Table\"}]"
motivation: 标准MoE需要将所有专家加载到VRAM，限制了部署效率。
method: 将前馈网络在推理前重新参数化为查找表，通过检索替代计算。
result: 降低了VRAM使用和通信延迟，同时保持模型性能。
conclusion: MoLE为大规模MoE模型的高效推理提供了新思路。
---

## Abstract
Mixture-of-Experts (MoE) activates only a subset of experts during inference, allowing the model to maintain low inference FLOPs and latency even as the parameter count scales up. However, since MoE dynamically selects the experts, all the experts need to be loaded into VRAM. Their large parameter size still limits deployment, and offloading, which load experts into VRAM only when needed, significantly increase inference latency. To address this, we propose Mixture of Lookup Experts (MoLE), a new MoE architecture that is efficient in both communication and VRAM usage. In MoLE, the experts are Feed-Forward Networks (FFNs) during training, taking the output of the embedding layer as input. Before inference, these experts can be re-parameterized as lookup tables (LUTs) that retrieves expert outputs based on input ids, and offloaded to storage devices. Therefore, we do not need to perform expert computations during inference. Instead, we directly retrieve the expert's computation results based on input ids and load them into VRAM, and thus the resulting communication overhead is negligible. Experiments show that, with the same FLOPs and VRAM usage, MoLE achieves inference speeds comparable to dense models and significantly faster than MoE with experts offloading, while maintaining performance on par with MoE. Code: https://github.com/JieShibo/MoLE.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
通过查找表减少VRAM使用，类似神经网络的计算内存架构。

### 2. 核心内容
Mixture of Lookup Experts (MoLE)提出了一种新的MoE架构，在推理前将专家网络重新参数化为查找表，从而大幅降低VRAM占用和通信开销。该方法在保持模型质量的同时，解决了大模型部署中的内存瓶颈问题。

### 3. 对应检索需求
compute in memory architecture for neural networks。

### 4. 来源与原文
- Source：ICML-2025-Accepted
- OpenReview：[https://openreview.net/forum?id=wUEp13rqXP](https://openreview.net/forum?id=wUEp13rqXP)
