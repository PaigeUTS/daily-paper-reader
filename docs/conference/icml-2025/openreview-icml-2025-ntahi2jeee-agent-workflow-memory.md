---
title: Agent Workflow Memory
title_zh: 智能体工流记忆
authors: "Zora Zhiruo Wang, Jiayuan Mao, Daniel Fried, Graham Neubig"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=NTAhi2JEEE"
tags: ["query:agents-os"]
score: 4.0
evidence: 智能体学习可复用工流以处理复杂任务，与智能体基础设施相关
tldr: Agent Workflow Memory (AWM)通过从历史经验中归纳可复用的工流，指导智能体在网页导航等复杂任务中的决策。该方法支持离线和在线场景，显著提升智能体在长周期任务中的表现，为构建更自主的智能体基础设施提供了新思路。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-ntahi2jeee/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 867, \"height\": 479, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ntahi2jeee/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 860, \"height\": 535, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ntahi2jeee/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 853, \"height\": 266, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ntahi2jeee/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 703, \"height\": 416, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ntahi2jeee/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 864, \"height\": 276, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-ntahi2jeee/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1417, \"height\": 709, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-ntahi2jeee/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1485, \"height\": 425, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ntahi2jeee/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1247, \"height\": 369, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ntahi2jeee/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 841, \"height\": 330, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ntahi2jeee/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1422, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ntahi2jeee/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 512, \"height\": 169, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ntahi2jeee/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 883, \"height\": 218, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ntahi2jeee/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 797, \"height\": 223, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ntahi2jeee/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 834, \"height\": 208, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ntahi2jeee/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1058, \"height\": 171, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ntahi2jeee/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1594, \"height\": 305, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ntahi2jeee/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1592, \"height\": 210, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ntahi2jeee/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 890, \"height\": 291, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-ntahi2jeee/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 791, \"height\": 206, \"label\": \"Table\"}]"
motivation: 语言模型智能体在长周期任务中表现不佳。
method: 从训练示例或测试查询中诱导常用工流，并选择性提供给智能体。
result: 在网页导航基准上提升了任务成功率。
conclusion: AWM使智能体能像人类一样复用经验。
---

## Abstract
Despite the potential of language model-based agents to solve real-world tasks such as web navigation, current methods still struggle with long-horizon tasks with complex action trajectories. In contrast, humans can flexibly solve complex tasks by learning reusable task workflows from past experiences and using them to guide future actions. To build agents that can similarly benefit from this process, we introduce Agent Workflow Memory (AWM), a method for inducing commonly reused routines, i.e., workflows, and selectively providing workflows to the agent to guide subsequent generations. AWM flexibly applies to both offline and online scenarios, where agents induce workflows from training examples beforehand or from test queries on the fly. We experiment on two major web navigation benchmarks — Mind2Web and WebArena — that collectively cover 1000+ tasks from 200+ domains across travel, shopping, and social media, among others. AWM substantially improves the baseline results by 24.6% and 51.1% relative success rate on Mind2Web and WebArena while reducing the number of steps taken to solve WebArena tasks successfully. Furthermore, online AWM robustly generalizes in cross-task, website, and domain evaluations, surpassing baselines from 8.9 to 14.0 absolute points as train-test task distribution gaps widen.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
智能体学习可复用工流以处理复杂任务，与智能体基础设施相关。

### 2. 核心内容
Agent Workflow Memory (AWM)通过从历史经验中归纳可复用的工流，指导智能体在网页导航等复杂任务中的决策。该方法支持离线和在线场景，显著提升智能体在长周期任务中的表现，为构建更自主的智能体基础设施提供了新思路。

### 3. 对应检索需求
How to design heterogeneous computing infrastructure for intelligent agents?

### 4. 来源与原文
- Source：ICML-2025-Accepted
- OpenReview：[https://openreview.net/forum?id=NTAhi2JEEE](https://openreview.net/forum?id=NTAhi2JEEE)
