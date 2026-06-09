---
title: Attention-Level Speculation
title_zh: 注意力级投机并行
authors: "Jack Cai, Ammar Vora, Randolph Zhang, Mark O'Connor, Mark C. Jeffrey"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=4OszSYdsgO"
tags: ["query:agents-os"]
score: 4.0
evidence: 大语言模型推理的投机并行，与AI工作负载效率相关
tldr: 该论文提出注意力级投机并行方法ALSpec，通过预测自注意力输出来提前执行后续操作，实现注意力与非注意力计算的重叠。在128K上下文长度下，注意力延迟降低5倍，端到端解码延迟降低1.65倍，且不牺牲质量。该方法为长上下文LLM推理提供了高效并行范式。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1769, \"height\": 552, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1526, \"height\": 294, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 706, \"height\": 567, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 867, \"height\": 385, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 837, \"height\": 1079, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 601, \"height\": 495, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1591, \"height\": 223, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1697, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 838, \"height\": 533, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1426, \"height\": 804, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1420, \"height\": 804, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1733, \"height\": 734, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1746, \"height\": 752, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-4oszsydsgo/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1722, \"height\": 904, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1602, \"height\": 561, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 774, \"height\": 269, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1600, \"height\": 294, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 904, \"height\": 767, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 905, \"height\": 938, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 750, \"height\": 800, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 743, \"height\": 719, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 924, \"height\": 1011, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 900, \"height\": 954, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 750, \"height\": 582, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-4oszsydsgo/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 742, \"height\": 555, \"label\": \"Table\"}]"
motivation: 传统张量并行在扩展多设备时收益递减，需新型并行策略降低注意力延迟。
method: 提出注意力级投机并行，基于预测执行重叠计算。
result: 长上下文下注意力延迟降低5倍，解码延迟降低1.65倍。
conclusion: 投机执行为LLM高效推理开辟了新途径。
---

## Abstract
As Large Language Models (LLMs) grow in size and context length, efficient inference strategies are essential to maintain low-latency token generation. Unfortunately, conventional tensor and data parallelism face diminishing returns when scaling across multiple devices. We propose a novel form—attention-level speculative parallelism (ALSpec)—that predicts self-attention outputs to execute subsequent operations early on separate devices. Our approach overlaps attention and non-attention computations, reducing the attention latency overhead at 128K context length by up to 5x and improving end-to-end decode latency by up to 1.65x, all without sacrificing quality. We establish the fundamental pillars for speculative execution and provide an execution paradigm that simplifies implementation. We show that existing attention-approximation methods perform well on simple information retrieval tasks, but they fail in advanced reasoning and math. Combined with speculative execution, we can approximate up to 90% of self-attention without harming model correctness. Demonstrated on Tenstorrent's NPU devices, we scale up LLM inference beyond current techniques, paving the way for faster inference in transformer models.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
大语言模型推理的投机并行，与AI工作负载效率相关。

### 2. 核心内容
该论文提出注意力级投机并行方法ALSpec，通过预测自注意力输出来提前执行后续操作，实现注意力与非注意力计算的重叠。在128K上下文长度下，注意力延迟降低5倍，端到端解码延迟降低1.65倍，且不牺牲质量。该方法为长上下文LLM推理提供了高效并行范式。

### 3. 对应检索需求
heterogeneous computing infrastructure for AI workloads。

### 4. 来源与原文
- Source：ICML-2025-Accepted
- OpenReview：[https://openreview.net/forum?id=4OszSYdsgO](https://openreview.net/forum?id=4OszSYdsgO)
