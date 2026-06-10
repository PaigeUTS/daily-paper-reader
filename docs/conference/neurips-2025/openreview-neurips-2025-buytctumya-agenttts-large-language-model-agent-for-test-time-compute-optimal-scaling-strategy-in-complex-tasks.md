---
title: "AgentTTS: Large Language Model Agent for Test-time Compute-optimal Scaling Strategy in Complex Tasks"
title_zh: "AgentTTS: 大语言模型智能体的测试时计算最优缩放策略"
authors: "Fali Wang, Hui Liu, Zhenwei DAI, Jingying Zeng, Zhiwei Zhang, Zongyu Wu, Chen Luo, Zhen Li, Xianfeng Tang, Qi He, Suhang Wang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=BuYtcTUMyA"
tags: ["query:agents-os"]
score: 7.0
evidence: 跨异构子任务的测试时计算最优缩放
tldr: 针对多阶段复杂任务中异构子任务的计算资源分配问题，提出AgentTTS，为每个子任务选择最优模型和预算分配，实现测试时计算最优缩放。该方法有效应对组合搜索空间，提升整体性能，为AI操作系统管理异构计算资源提供参考。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-buytctumya/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1300, \"height\": 591, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-buytctumya/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 725, \"height\": 635, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-buytctumya/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1156, \"height\": 673, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-buytctumya/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1437, \"height\": 437, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-buytctumya/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1159, \"height\": 701, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-buytctumya/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 722, \"height\": 361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-buytctumya/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 579, \"height\": 308, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-buytctumya/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1458, \"height\": 1612, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-buytctumya/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1323, \"height\": 1358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-buytctumya/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1302, \"height\": 872, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-buytctumya/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1301, \"height\": 881, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-buytctumya/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1158, \"height\": 953, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-buytctumya/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1160, \"height\": 955, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-buytctumya/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1304, \"height\": 843, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-buytctumya/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1291, \"height\": 1045, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-buytctumya/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1451, \"height\": 2056, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-buytctumya/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 976, \"height\": 712, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-buytctumya/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1442, \"height\": 427, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-buytctumya/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1455, \"height\": 314, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-buytctumya/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 768, \"height\": 422, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-buytctumya/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 867, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-buytctumya/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 712, \"height\": 563, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-buytctumya/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1447, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-buytctumya/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1447, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-buytctumya/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 966, \"height\": 276, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-buytctumya/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1446, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-buytctumya/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1447, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-buytctumya/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1445, \"height\": 279, \"label\": \"Table\"}]"
motivation: 现有测试时缩放研究仅关注单阶段任务，多阶段复杂任务中异构子任务资源分配困难。
method: 提出针对多阶段任务的测试时计算最优缩放，为每个子任务选择模型和分配预算。
result: 在组合搜索空间下有效提升多阶段任务性能。
conclusion: AgentTTS为AI系统异构资源调度提供了可行策略。
---

## Abstract
Test-time scaling (TTS) enhances the performance of large language models (LLMs) by allocating additional compute resources during inference. However, existing research primarily investigates TTS in single-stage tasks; while many real-world problems are multi-stage complex tasks, composed of a sequence of heterogeneous subtasks with each subtask requires LLM of specific capability. Therefore, we study a novel problem: the test-time compute-optimal scaling in multi-stage complex tasks, aiming to select suitable models and allocate budgets per subtask to maximize overall performance. TTS in multi-stage tasks introduces two fundamental challenges: (i) The combinatorial search space of model and budget allocations, combined with the high cost of inference, makes brute-force search impractical. (ii) The optimal model and budget allocations across subtasks are interdependent, increasing the complexity of the compute-optimal search. To address this gap, we conduct extensive pilot experiments on four tasks across six datasets, deriving three empirical insights characterizing the behavior of LLMs in multi-stage complex tasks. Informed by these insights, we propose AgentTTS, an LLM-agent-based framework that autonomously searches for compute-optimal allocations through iterative feedback-driven interactions with the execution environment. Experimental results demonstrate that AgentTTS significantly outperforms traditional and other LLM-based baselines in search efficiency, and shows improved robustness to varying training set sizes and enhanced interpretability.

---

## 论文详细总结（自动生成）

好的，以下是对给定论文《AgentTTS: Large Language Model Agent for Test-time Compute-optimal Scaling Strategy in Complex Tasks》的详细中文总结。

---

## 1. 论文的核心问题与整体含义

- **研究背景**：测试时缩放（Test-time Scaling, TTS）通过在推理阶段投入更多计算资源来提升大语言模型（LLM）的性能，在数学问题求解、代码生成等**单阶段任务**中已取得显著成效。
- **核心问题**：现实世界中许多问题是**多阶段复杂任务**（如检索-生成问答、瀑布式软件开发），由一系列异构子任务构成，每个子任务对模型能力有特定要求。论文研究了一个新问题：**多阶段复杂任务的测试时计算最优缩放**，旨在为每个子任务选择最合适的模型并分配预算，以最大化整体任务性能。
- **主要挑战**：
    1. **组合搜索空间巨大**：模型选择和预算分配的组合导致搜索空间呈指数级增长，暴力搜索不切实际。
    2. **子任务间依赖性**：前一子任务的计算分配会影响后续子任务的性能表现和最优预算，增加了搜索的复杂性。

## 2. 论文提出的方法论

- **核心思想**：通过大量预实验，总结出关于多阶段任务中测试时缩放行为的三个关键洞察（Insight）。基于这些洞察，设计一个LLM智能体（Agent）框架，通过与真实任务执行环境的反复交互，高效自主地搜索最优的预算和模型分配方案。

- **三个关键洞察**：
    1. **Insight 1 (模型偏好差异)**：不同子任务对模型大小和采样策略有不同偏好。
    2. **Insight 2 (收益递减)**：随着测试时计算量增加，性能先改善，但超越某个最优预算后，额外投入带来的收益会减少甚至为负。
    3. **Insight 3 (子任务依赖性)**：前序子任务的计算分配会影响下游子任务的缩放动态和计算需求。

- **核心框架 (AgentTTS)**：
    - **三大组件**：
        - **Agent (智能体)**：由LLM实现，负责生成候选配置和探索指南。
        - **Environment (环境)**：评估候选配置在真实任务平台上的性能。
        - **Archive (档案)**：存储生成的候选配置、反馈信息和探索指南。
    - **算法流程 (文字描述)**：
        1. **初始化**：Agent根据**Insight 1**生成一批初始候选试验，选择能体现不同子任务模型偏好的配置。
        2. **执行与反馈**：Environment执行这些试验，并将性能反馈返回给Agent。
        3. **迭代循环**：
            - Agent根据**Insight 2**和**Insight 3**，结合历史反馈，生成新的探索指南。
            - Agent依据探索指南，生成下一轮候选试验。
            - Environment执行新试验并返回反馈。
        4. **终止与输出**：重复上述过程直到满足预设停止条件，从Archive中输出性能最好的试验作为最优配置。

- **关键技术细节**：
    - **统一预算转换**：为了公平比较不同模型（不同大小）和任务（不同生成长度）的计算成本，论文提出了一个基于推理FLOPs的归一化预算函数，将所有配置的成本转换为等效的最小模型（3B）在基线上的采样次数。
    - **重复采样与融合**：采用并行缩放策略，即多次采样（多次推理）生成多个候选答案，然后用一个额外的llm提示（融合提示）将这些答案整合成最终输出。

## 3. 实验设计

- **数据集与场景**：在四个多阶段任务、六个数据集上进行评估：
    1. **检索增强问答**：2WikiMultiHopQA, HotpotQA。
    2. **知识图谱问答**：CWQ, WebQSP。
    3. **任务自动化**：TaskBench。
    4. **自动化软件开发**：ChatDev。
- **Benchmark与对比方法**：
    - **传统方法**：随机搜索（Random）、贝叶斯优化（Bayesian Optimization, BO）。
    - **基于LLM的方法**：LLM_ZS (零样本生成)、MLCopilot、AgentHPO。所有基线方法都被适配到他们的问题设定中。
- **评估方式**：所有方法在包含50个样本的训练集上搜索50轮，然后在包含500个样本的测试集上评估找到的最佳配置。

## 4. 资源与算力

- **算力信息**：
    - 所有试验均在**NVIDIA H100 80GB HBM3 GPU**上进行。
    - 搜索过程使用 **GPT-o3-mini** 作为LLM搜索代理。
    - **未明确说明**：没有提供训练整个框架或进行所有实验所需的总GPU小时数或具体数量。论文主要关注搜索效率，并以“搜索时间（小时）”作为性能指标。

## 5. 实验数量与充分性

- **实验数量**：
    - **主实验**：在6个数据集上评估，展示了AgentTTS与5种基线方法的搜索轨迹和最终测试性能。
    - **消融实验**：在2WikiMultiHopQA数据集上，分别移除三个洞察（Insight 1, 2, 3）进行验证。
    - **鲁棒性分析**：改变训练集大小（50, 75, 100样本）。
    - **预算敏感性**：在低、中、高三种预算设置下评估。
    - **温度影响**：研究了温度参数对性能的影响。
    - **不同成本度量**：除了FLOPs，还使用API价格作为成本度量进行了验证。
- **充分性与公平性**：
    - **充分**：实验覆盖了多个不同特性的多阶段任务，对比了多种类型的基线，并进行了详尽的消融和鲁棒性分析，实验设计较为全面。
    - **客观公平**：所有对比方法在相同的搜索轮次和训练/测试集划分下评估，并针对问题设置进行了适配。实验结果以图表和表格形式清晰展示，并强调了AgentTTS在搜索效率和最终性能上的优势。

## 6. 论文的主要结论与发现

1. **AgentTTS在搜索效率上显著优于所有基线**：无论是在低、中、高预算下，还是不同训练集大小下，AgentTTS都能用更少的试验找到更优或更稳定的配置。
2. **三个洞察是性能提升的关键**：消融实验证明，缺少任何一个洞察都会导致搜索效率下降，其中Insight 1对找到最优配置至关重要。
3. **良好的泛化性与鲁棒性**：在不同预算设置、训练集大小以及成本度量（API价格）下，AgentTTS均表现出优于基线的性能和稳定性。
4. **增强的可解释性**：Agent生成的探索指南能够清晰解释其决策逻辑，例如为何为特定子任务选择特定模型或预算。

## 7. 优点

- **问题新颖且有价值**：首次系统研究了多阶段复杂任务的测试时计算最优缩放问题，切中实际应用痛点。
- **洞见驱动，方法巧妙**：不是盲目地进行超参数搜索，而是基于实证洞察来指导搜索，兼具理论依据和实际效果。
- **框架设计优雅**：Agent、Environment、Archive的三组件设计清晰，结合了LLM的推理规划能力和真实环境的反馈，形成了一个高效的闭环优化系统。
- **实验评估全面且深入**：覆盖多种任务、多种基线，并有详尽的消融和鲁棒性分析，论证充分。
- **可解释性强**：Agent生成文本指南的机制使得整个搜索过程透明，易于理解和分析。

## 8. 不足与局限

- **实验覆盖的局限**：
    - 所有任务均为静态多阶段任务。论文在局限性部分也承认，未考虑动态多阶段任务（如根据输入动态决定子任务）的适用性。
    - 实验仅在基于文本的LLM推理任务上进行，未在需要其他模态（如视觉）的复杂任务中验证。
- **方法的局限性**：
    - 对整个AgentTTS框架的搜索过程本身需要消耗大量计算资源（调用GPT-o3-mini），虽然论文展示了其优于其他搜索方法，但框架本身的运行成本未被直接讨论。
    - 搜索过程需要一个单独的LLM作为Agent（GPT-o3-mini），这增加了部署和维护的复杂度。
    - 论文未报告多次运行结果的误差线或方差，这在基于随机采样的方法中是一个常见的关注点。
- **潜在的偏差与风险**：论文在局限性部分指出，该方法依赖的重复采样放大了LLM的潜在问题，如幻觉，可能导致错误信息被高效传播。

（完）
