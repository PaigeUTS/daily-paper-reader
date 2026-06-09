---
title: On the Resilience of LLM-Based Multi-Agent Collaboration with Faulty Agents
title_zh: 关于带故障智能体的LLM多智能体协作的韧性研究
authors: "Jen-tse Huang, Jiaxu Zhou, Tailin Jin, Xuhui Zhou, Zixi Chen, Wenxuan Wang, Youliang Yuan, Michael Lyu, Maarten Sap"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=bkiM54QftZ"
tags: ["query:agents-os"]
score: 4.0
evidence: 带故障智能体的LLM多智能体系统韧性，与智能体系统相关
tldr: 该论文研究了LLM多智能体系统在存在笨拙或恶意智能体时的韧性，分析了不同系统结构（如链式、循环）的影响。提出AutoTransform和AutoInject两种模拟故障方法，并探索提升韧性的策略。实验揭示了结构对故障鲁棒性的关键作用。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-bkim54qftz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 806, \"height\": 777, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bkim54qftz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1511, \"height\": 1289, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bkim54qftz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1721, \"height\": 431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bkim54qftz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 871, \"height\": 867, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bkim54qftz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1716, \"height\": 392, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bkim54qftz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 862, \"height\": 951, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-bkim54qftz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 863, \"height\": 265, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bkim54qftz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 861, \"height\": 329, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bkim54qftz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 859, \"height\": 354, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bkim54qftz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1099, \"height\": 427, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bkim54qftz/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1307, \"height\": 514, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bkim54qftz/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1507, \"height\": 536, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bkim54qftz/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1355, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bkim54qftz/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1690, \"height\": 412, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bkim54qftz/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1277, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bkim54qftz/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1175, \"height\": 229, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bkim54qftz/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1750, \"height\": 1697, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bkim54qftz/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1748, \"height\": 1656, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bkim54qftz/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1758, \"height\": 723, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bkim54qftz/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1752, \"height\": 1073, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bkim54qftz/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1754, \"height\": 1727, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bkim54qftz/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1742, \"height\": 886, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bkim54qftz/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1745, \"height\": 1024, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bkim54qftz/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1731, \"height\": 455, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bkim54qftz/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1742, \"height\": 558, \"label\": \"Table\"}]"
motivation: 多智能体系统中故障智能体对整体性能的影响尚不明确。
method: 提出AutoTransform和AutoInject模拟故障，分析不同结构的韧性。
result: 揭示了不同系统结构对故障的鲁棒性差异。
conclusion: 结构设计对提升多智能体系统韧性至关重要。
---

## Abstract
Large language model-based multi-agent systems have shown great abilities across various tasks due to the collaboration of expert agents, each focusing on a specific domain. However, the impact of clumsy or even malicious agents—those who frequently make errors in their tasks—on the overall performance of the system remains underexplored. This paper investigates: (1) What is the resilience of various system structures (e.g., A$\rightarrow$B$\rightarrow$C, A$\leftrightarrow$B$\leftrightarrow$C) under faulty agents, on different downstream tasks? (2) How can we increase system resilience to defend against these agents? To simulate faulty agents, we propose two approaches—AutoTransform and AutoInject—which introduce mistakes into the agents' responses. Experiments on four downstream tasks using six systems show that the "hierarchical" structure, i.e., A$\rightarrow$(B$\leftrightarrow$C), exhibits superior resilience with the lowest performance drop of 5.5%, compared to 10.5% and 23.7% of other two structures. To further improve resilience, we introduce (1) Challenger, that introduces a mechanism for each agent to challenge others' outputs, and (2) Inspector, an additional agent to review and correct messages, recovering up to 96.4% errors made by faulty agents. Our code and data are available at https://github.com/CUHK-ARISE/MAS-Resilience.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
带故障智能体的LLM多智能体系统韧性，与智能体系统相关。

### 2. 核心内容
该论文研究了LLM多智能体系统在存在笨拙或恶意智能体时的韧性，分析了不同系统结构（如链式、循环）的影响。提出AutoTransform和AutoInject两种模拟故障方法，并探索提升韧性的策略。实验揭示了结构对故障鲁棒性的关键作用。

### 3. 对应检索需求
Agents operating system for server infrastructure。

### 4. 来源与原文
- Source：ICML-2025-Accepted
- OpenReview：[https://openreview.net/forum?id=bkiM54QftZ](https://openreview.net/forum?id=bkiM54QftZ)
