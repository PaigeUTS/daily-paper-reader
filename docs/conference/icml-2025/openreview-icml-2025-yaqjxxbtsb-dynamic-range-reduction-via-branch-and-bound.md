---
title: Dynamic Range Reduction via Branch-and-Bound
title_zh: 通过分支定界降低动态范围
authors: "Thore Gerlach, Nico Piatkowski"
date: 2025-01-19
pdf: "https://openreview.net/pdf?id=yaqjXxbtSB"
tags: ["query:agents-os"]
score: 4.0
evidence: 降低数值精度以适配硬件加速器，与计算内存架构相关
tldr: 本文提出一种基于分支定界的算法，用于降低QUBO问题的动态范围，从而减少对数值精度的需求。该方法有助于在GPU和FPGA等硬件加速器上实现更快、更低延迟的AI推理，支持计算内存架构的设计。
source: ICML-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-yaqjxxbtsb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 843, \"height\": 418, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yaqjxxbtsb/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 872, \"height\": 201, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yaqjxxbtsb/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1786, \"height\": 401, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yaqjxxbtsb/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 875, \"height\": 246, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yaqjxxbtsb/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 872, \"height\": 198, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yaqjxxbtsb/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 874, \"height\": 202, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yaqjxxbtsb/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 831, \"height\": 383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yaqjxxbtsb/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1694, \"height\": 384, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yaqjxxbtsb/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1703, \"height\": 368, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-yaqjxxbtsb/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1699, \"height\": 637, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-yaqjxxbtsb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1732, \"height\": 389, \"label\": \"Table\"}]"
motivation: QUBO问题需要高数值精度，给硬件求解器带来挑战。
method: 提出分支定界算法，以动态范围作为复杂度度量减少精度需求。
result: 在子集和、聚类等任务上成功降低了动态范围。
conclusion: 该方法可增强专用硬件加速器的处理速度。
---

## Abstract
A key strategy to enhance specialized hardware accelerators, such as GPUs and FPGA, is to reduce the numerical precision in arithmetic operations, which increases processing speed and lowers latency---both crucial for real-time AI applications.
In this work, we consider NP-hard Quadratic Unconstrained Binary Optimization (QUBO) problems, which arise in machine learning and beyond. 
We show that these problems often require high numerical precision, posing challenges for hardware solvers. 
We introduce a principled Branch-and-Bound algorithm for reducing the precision requirements of QUBO problems by utilizing the dynamic range as a measure of complexity. Experiments demonstrate that our method reduces the dynamic range in subset sum, clustering, and vector quantization problems, thereby increasing their solvability on actual quantum annealers and FPGA-based digital annealers.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
降低数值精度以适配硬件加速器，与计算内存架构相关。

### 2. 核心内容
本文提出一种基于分支定界的算法，用于降低QUBO问题的动态范围，从而减少对数值精度的需求。该方法有助于在GPU和FPGA等硬件加速器上实现更快、更低延迟的AI推理，支持计算内存架构的设计。

### 3. 对应检索需求
compute in memory architecture for neural networks。

### 4. 来源与原文
- Source：ICML-2025-Rejected-Public
- OpenReview：[https://openreview.net/forum?id=yaqjXxbtSB](https://openreview.net/forum?id=yaqjXxbtSB)
