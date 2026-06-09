---
title: "KABB: Knowledge-Aware Bayesian Bandits for Dynamic Expert Coordination in Multi-Agent Systems"
title_zh: KABB：多智能体系统中基于知识感知贝叶斯强盗的动态专家协调
authors: "Jusheng Zhang, Zimeng Huang, Yijia Fan, Ningyuan Liu, Mingyan Li, Zhuojie Yang, Jiawei Yao, Jian Wang, Keze Wang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=AKvy9a4jho"
tags: ["query:agents-os"]
score: 4.0
evidence: 多智能体系统中动态专家协调
tldr: Knowledge-Aware Bayesian Bandits (KABB)提出了一个知识感知的贝叶斯强盗框架，用于多智能体系统中专家的动态协调。通过语义理解、双适应机制和知识感知汤普森采样，KABB实现了成本与性能的最优平衡，显著提升了多智能体协作效率。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-akvy9a4jho/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 786, \"height\": 884, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-akvy9a4jho/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1710, \"height\": 978, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-akvy9a4jho/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 819, \"height\": 685, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-akvy9a4jho/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 844, \"height\": 680, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-akvy9a4jho/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 839, \"height\": 675, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-akvy9a4jho/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 859, \"height\": 727, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-akvy9a4jho/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1764, \"height\": 955, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-akvy9a4jho/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 781, \"height\": 323, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-akvy9a4jho/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1398, \"height\": 203, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-akvy9a4jho/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1531, \"height\": 321, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-akvy9a4jho/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1532, \"height\": 286, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-akvy9a4jho/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 610, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-akvy9a4jho/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 725, \"height\": 605, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-akvy9a4jho/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1279, \"height\": 369, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-akvy9a4jho/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1783, \"height\": 1813, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-akvy9a4jho/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1782, \"height\": 2086, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-akvy9a4jho/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1783, \"height\": 1694, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-akvy9a4jho/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1785, \"height\": 1796, \"label\": \"Table\"}]"
motivation: 多智能体系统面临静态假设和协调低效的问题。
method: 引入知识距离模型、双适应机制和知识感知汤普森采样。
result: 实现了成本-性能最优平衡，保持高性能。
conclusion: KABB增强了多智能体系统的协调能力。
---

## Abstract
As scaling large language models faces prohibitive costs, multi-agent systems emerge as a promising alternative, though challenged by static knowledge assumptions and coordination inefficiencies. We introduce Knowledge-Aware Bayesian Bandits (KABB), a novel framework that enhances multi-agent system coordination through semantic understanding and dynamic adaptation. The framework features three key innovations: a customized knowledge distance model for deep semantic understanding, a dual-adaptation mechanism for continuous expert optimization, and a knowledge-aware Thompson Sampling strategy for efficient expert selection. Extensive evaluation demonstrates KABB achieves an optimal cost-performance balance, maintaining high performance while keeping computational demands relatively low in multi-agent coordination.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
多智能体系统中动态专家协调。

### 2. 核心内容
Knowledge-Aware Bayesian Bandits (KABB)提出了一个知识感知的贝叶斯强盗框架，用于多智能体系统中专家的动态协调。通过语义理解、双适应机制和知识感知汤普森采样，KABB实现了成本与性能的最优平衡，显著提升了多智能体协作效率。

### 3. 对应检索需求
How to design heterogeneous computing infrastructure for intelligent agents?

### 4. 来源与原文
- Source：ICML-2025-Accepted
- OpenReview：[https://openreview.net/forum?id=AKvy9a4jho](https://openreview.net/forum?id=AKvy9a4jho)
