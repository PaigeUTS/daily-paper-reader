---
title: "MxMoE: Mixed-precision Quantization for MoE with Accuracy and Performance Co-Design"
title_zh: MxMoE：面向MoE的混合精度量化与性能和精度协同设计
authors: "Haojie Duanmu, Xiuhong Li, Zhihang Yuan, Size Zheng, Jiangfei Duan, Xingcheng Zhang, Dahua Lin"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=pXoZLGMNDm"
tags: ["query:agents-os"]
score: 6.0
evidence: 感知异质计算特征的MoE混合精度量化
tldr: 针对MoE模型部署中的计算异构性，提出MxMoE混合精度量化框架，结合参数敏感性、专家激活动态和硬件资源自动生成高效配置。该工作支持大模型在异构算力上的高效推理。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-pxozlgmndm/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1777, \"height\": 640, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pxozlgmndm/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 707, \"height\": 513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pxozlgmndm/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 870, \"height\": 434, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pxozlgmndm/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 702, \"height\": 494, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pxozlgmndm/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1794, \"height\": 681, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pxozlgmndm/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 866, \"height\": 488, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-pxozlgmndm/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1761, \"height\": 1151, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pxozlgmndm/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 857, \"height\": 235, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pxozlgmndm/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 855, \"height\": 240, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pxozlgmndm/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1388, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pxozlgmndm/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 852, \"height\": 447, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pxozlgmndm/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 916, \"height\": 256, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pxozlgmndm/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1445, \"height\": 2311, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pxozlgmndm/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1444, \"height\": 679, \"label\": \"Table\"}]"
motivation: MoE模型参数大、计算量大，且各专家激活频率异质。
method: 提出MxMoE框架，综合考虑敏感性、激活频率和硬件资源，自动导出混合精度配置。
result: MxMoE在保持精度的同时显著降低模型大小和计算开销。
conclusion: 混合精度量化可有效应对MoE模型的异构计算特性。
---

## Abstract
Mixture-of-Experts (MoE) models face deployment challenges due to their large parameter counts and computational demands. We explore quantization for MoE models and highlight two key insights: 1) linear blocks exhibit varying quantization sensitivity, and 2) divergent expert activation frequencies create heterogeneous computational characteristics. Based on these observations, we introduce MxMoE, a mixed-precision optimization framework for MoE models that considers both algorithmic and system perspectives. MxMoE navigates the design space defined by parameter sensitivity, expert activation dynamics, and hardware resources to derive efficient mixed-precision configurations. Additionally, MxMoE automatically generates optimized mixed-precision GroupGEMM kernels, enabling parallel execution of GEMMs with different precisions. Evaluations show that MxMoE outperforms existing methods, achieving 2.4 lower Wikitext-2 perplexity than GPTQ at 2.25-bit and delivering up to 3.4x speedup over full precision, as well as up to 29.4% speedup over uniform quantization at equivalent accuracy with 5-bit weight-activation quantization. Our code is available at https://github.com/cat538/MxMoE.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
感知异质计算特征的MoE混合精度量化。

### 2. 核心内容
针对MoE模型部署中的计算异构性，提出MxMoE混合精度量化框架，结合参数敏感性、专家激活动态和硬件资源自动生成高效配置。该工作支持大模型在异构算力上的高效推理。

### 3. 对应检索需求
How does heterogeneous computing support large model training?

### 4. 来源与原文
- Source：ICML-2025-Accepted
- OpenReview：[https://openreview.net/forum?id=pXoZLGMNDm](https://openreview.net/forum?id=pXoZLGMNDm)
