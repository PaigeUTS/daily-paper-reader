---
title: QoS-Efficient Serving of Multiple Mixture-of-Expert LLMs Using Partial Runtime Reconfiguration
title_zh: 基于运行时部分重配置的多个混合专家大语言模型的QoS高效服务
authors: "HamidReza Imani, Jiaxin Peng, Peiman Mohseni, Abdolah Amirany, Tarek El-Ghazawi"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=g45SHBmZLz"
tags: ["query:agents-os"]
score: 6.0
evidence: 在单个GPU上高效服务MoE大语言模型，服务器资源管理
tldr: 该论文针对在单个GPU上高效服务多个微调MoE大语言模型的问题，提出了基于相似性的专家合并技术和运行时部分重配置方法，通过共享相似专家降低内存占用，并动态替换非专家层以保证输出质量。实验表明该方法能显著提升服务效率，为资源受限环境下的模型部署提供了新思路。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-g45shbmzlz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 697, \"height\": 856, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-g45shbmzlz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1548, \"height\": 521, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-g45shbmzlz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1548, \"height\": 698, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-g45shbmzlz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1614, \"height\": 598, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-g45shbmzlz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1680, \"height\": 672, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-g45shbmzlz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 878, \"height\": 1032, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-g45shbmzlz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 868, \"height\": 1494, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-g45shbmzlz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 873, \"height\": 301, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-g45shbmzlz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 731, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-g45shbmzlz/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1676, \"height\": 375, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-g45shbmzlz/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1239, \"height\": 729, \"label\": \"Table\"}]"
motivation: 多个微调MoE大模型在单GPU上部署面临高内存需求，传统虚拟化技术效果有限。
method: 提出基于专家相似性的合并策略减少内存，并引入运行时部分重配置动态替换非专家层。
result: 在单个GPU上成功服务多个MoE模型，降低了内存占用且不影响输出质量。
conclusion: 该方法为多模型共享资源提供了一种高效且QoS感知的解决方案。
---

## Abstract
The deployment of mixture-of-experts (MoE) large language models (LLMs) presents significant challenges due to their high memory demands. These challenges become even more pronounced in multi-tenant environments, where shared resources must accommodate multiple models, limiting the effectiveness of conventional virtualization techniques. This paper addresses the problem of efficiently serving multiple fine-tuned MoE-LLMs on a single GPU. We propose a serving system that employs \textit{similarity-based expert consolidation} to reduce the overall memory footprint by sharing similar experts across models. To ensure output quality, we introduce \textit{runtime partial reconfiguration}, dynamically replacing non-expert layers when processing requests from different models. As a result, our approach achieves competitive output quality while maintaining throughput comparable to serving a single model, and incurs only a negligible increase in time-to-first-token (TTFT). Experiments on a server with a single NVIDIA A100 GPU (80GB) using Mixtral-8x7B models demonstrate an 85\% average reduction in turnaround time compared to NVIDIA's multi-instance GPU (MIG). Furthermore, experiments on Google's Switch Transformer Base-8 model with up to four variants demonstrate the scalability and resilience of our approach in maintaining output quality compared to other model merging baselines, highlighting its effectiveness.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
在单个GPU上高效服务MoE大语言模型，服务器资源管理。

### 2. 核心内容
该论文针对在单个GPU上高效服务多个微调MoE大语言模型的问题，提出了基于相似性的专家合并技术和运行时部分重配置方法，通过共享相似专家降低内存占用，并动态替换非专家层以保证输出质量。实验表明该方法能显著提升服务效率，为资源受限环境下的模型部署提供了新思路。

### 3. 对应检索需求
heterogeneous compute resources for servers。

### 4. 来源与原文
- Source：ICML-2025-Accepted
- OpenReview：[https://openreview.net/forum?id=g45SHBmZLz](https://openreview.net/forum?id=g45SHBmZLz)
