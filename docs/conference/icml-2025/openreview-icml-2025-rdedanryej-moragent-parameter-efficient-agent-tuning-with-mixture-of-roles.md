---
title: "MoRAgent: Parameter Efficient Agent Tuning with Mixture-of-Roles"
title_zh: MoRAgent：基于角色混合的参数高效智能体微调
authors: "Jing Han, Binwei Yan, Tianyu Guo, Zheyuan Bai, Mengyu Zheng, Hanting Chen, Ying Nie"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=rdeDanrYEj"
tags: ["query:agents-os"]
score: 4.0
evidence: 针对智能体任务的参数高效微调
tldr: 针对大型语言模型在智能体任务中微调效率低的问题，MoRAgent提出了一种基于角色混合的参数高效微调方法。该方法将智能体所需能力分解为推理器、执行器和总结器三种角色，分别负责理解查询、调用函数和总结信息。实验表明，这种角色分解策略在保持性能的同时大幅减少了可训练参数数量，为智能体系统的构建提供了高效的模型定制方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-rdedanryej/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1645, \"height\": 658, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rdedanryej/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1691, \"height\": 789, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rdedanryej/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 817, \"height\": 752, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rdedanryej/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 851, \"height\": 328, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rdedanryej/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 824, \"height\": 531, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-rdedanryej/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 501, \"height\": 556, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-rdedanryej/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1765, \"height\": 588, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rdedanryej/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 854, \"height\": 536, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rdedanryej/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 820, \"height\": 364, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rdedanryej/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 794, \"height\": 336, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rdedanryej/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 800, \"height\": 334, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rdedanryej/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 854, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-rdedanryej/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 857, \"height\": 372, \"label\": \"Table\"}]"
motivation: 针对智能体任务中参数高效微调方法研究不足的问题。
method: 提出Reason+Action范式下的角色分解策略，将智能体能力分解为推理器、执行器和总结器三种角色。
result: 在多个智能体任务上验证了参数高效微调的有效性。
conclusion: 证明了角色分解方法能显著提升智能体任务的微调效率。
---

## Abstract
Despite recent advancements of fine-tuning large language models (LLMs) to facilitate agent tasks, parameter-efficient fine-tuning (PEFT) methodologies for agent remain largely unexplored. In this paper, we introduce three key strategies for PEFT in agent tasks: 1) Inspired by the increasingly dominant \textit{Reason+Action} paradigm, we first decompose the capabilities necessary for the agent tasks into three distinct roles: reasoner, executor, and summarizer. The reasoner is responsible for comprehending the user's query and determining the next role based on the execution trajectory. The executor is tasked with identifying the appropriate functions and parameters to invoke. The summarizer conveys the distilled information from conversations back to the user. 2) We then propose the Mixture-of-Roles (MoR) framework, which comprises three specialized Low-Rank Adaptation (LoRA) groups, each designated to fulfill a distinct role. By focusing on their respective specialized capabilities and engaging in collaborative interactions, these LoRAs collectively accomplish the agent task. 3) To effectively fine-tune the framework, we develop a multi-role data generation pipeline based on publicly available datasets, incorporating role-specific content completion and reliability verification.
We conduct extensive experiments and thorough ablation studies on various LLMs and agent benchmarks, demonstrating the effectiveness of the proposed method. This project is publicly available at https://mor-agent.github.io

---

## 论文详细总结（自动生成）

### 1. 检索相关性
针对智能体任务的参数高效微调。

### 2. 核心内容
针对大型语言模型在智能体任务中微调效率低的问题，MoRAgent提出了一种基于角色混合的参数高效微调方法。该方法将智能体所需能力分解为推理器、执行器和总结器三种角色，分别负责理解查询、调用函数和总结信息。实验表明，这种角色分解策略在保持性能的同时大幅减少了可训练参数数量，为智能体系统的构建提供了高效的模型定制方案。

### 3. 对应检索需求
Agents operating system for server infrastructure。

### 4. 来源与原文
- Source：ICML-2025-Accepted
- OpenReview：[https://openreview.net/forum?id=rdeDanrYEj](https://openreview.net/forum?id=rdeDanrYEj)
