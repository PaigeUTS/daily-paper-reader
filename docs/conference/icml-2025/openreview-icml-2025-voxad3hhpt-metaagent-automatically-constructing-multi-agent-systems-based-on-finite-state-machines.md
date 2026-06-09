---
title: "MetaAgent: Automatically Constructing Multi-Agent Systems Based on Finite State Machines"
title_zh: MetaAgent：基于有限状态机的多智能体系统自动构建
authors: "Yaolun Zhang, Xiaogeng Liu, Chaowei Xiao"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=vOxaD3hhPt"
tags: ["query:agents-os"]
score: 7.0
evidence: 自动构建多智能体系统
tldr: 面对手动设计多智能体系统场景受限和自动设计方法工具集成不足的问题，MetaAgent提出了一种基于有限状态机的框架。给定任务描述后，该系统自动设计多智能体架构并通过优化算法迭代改进，最终生成可部署的系统。实验证明，该方法在多个任务上取得了优于手动设计的性能，为智能体操作系统的自动化构建提供了关键技术支撑。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-voxad3hhpt/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1743, \"height\": 753, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-voxad3hhpt/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1702, \"height\": 829, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-voxad3hhpt/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1743, \"height\": 922, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-voxad3hhpt/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1813, \"height\": 2157, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-voxad3hhpt/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1821, \"height\": 1895, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-voxad3hhpt/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1820, \"height\": 2062, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-voxad3hhpt/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1828, \"height\": 1394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-voxad3hhpt/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1810, \"height\": 889, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-voxad3hhpt/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1555, \"height\": 464, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-voxad3hhpt/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 757, \"height\": 347, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-voxad3hhpt/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1434, \"height\": 399, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-voxad3hhpt/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1453, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-voxad3hhpt/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1406, \"height\": 235, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-voxad3hhpt/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1606, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-voxad3hhpt/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 808, \"height\": 456, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-voxad3hhpt/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1020, \"height\": 941, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-voxad3hhpt/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 586, \"height\": 242, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-voxad3hhpt/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 409, \"height\": 205, \"label\": \"Table\"}]"
motivation: 现有手动设计的多智能体框架场景受限，自动设计方法存在工具集成不足等问题。
method: 提出基于有限状态机的框架，根据任务描述自动生成多智能体系统并通过优化算法改进。
result: 实验表明自动生成的多智能体系统在多种任务上表现出色。
conclusion: 为多智能体系统的自动化构建提供了有效方法。
---

## Abstract
Large Language Models (LLMs) have demonstrated the ability to solve a wide range of practical tasks within multi-agent systems. However, existing human-designed multi-agent frameworks are typically limited to a small set of pre-defined scenarios, while current automated design methods suffer from several limitations, such as the lack of tool integration, dependence on external training data, and rigid communication structures. In this paper, we propose \textbf{MetaAgent}, a  \textbf{finite state machine} based framework that can automatically generate a multi-agent system. Given a task description, MetaAgent will design a multi-agent system and polish it through an optimization algorithm. When the multi-agent system is deployed, the finite state machine will control the agent's actions and the state transitions. To evaluate our framework, we conduct experiments on both text-based tasks and practical tasks. The results indicate that the generated multi-agent system surpasses other auto-designed methods and can achieve a comparable performance with the human-designed multi-agent system, which is optimized for those specific tasks.

---

## 论文详细总结（自动生成）

### 论文核心问题与整体含义（研究动机和背景）

- **研究动机**：现有手动设计的多智能体系统（如 MetaGPT、ChatDev）通常针对特定场景，泛化能力弱且需要大量人工迭代。自动设计方法（如 SPP、AutoAgents、EvoAgent）存在工具集成缺失、依赖外部训练数据、通信结构僵化（多为线性或简单辩论）等问题，缺乏灵活的错误回溯和迭代优化机制。
- **整体含义**：论文旨在提出一个能 **自动构建、泛化且实用的多智能体系统** 框架，降低人工成本，同时提升系统在复杂任务中的鲁棒性和性能。

### 论文提出的方法论

- **核心思想**：将多智能体系统建模为 **有限状态机（FSM）**，通过 LLM 自动设计智能体角色、状态划分及转移条件，并通过优化算法合并冗余状态，最终生成可部署的系统。
- **关键技术细节**：
    1. **智能体设计**：由设计 LLM 根据任务描述生成智能体列表（名称、系统提示词、可用工具，如代码解释器、搜索引擎）。
    2. **状态与转移条件设计**：基于智能体，LLM 规划不同情境下的状态（每个状态包含：任务求解智能体、状态指令、条件验证器、监听器列表）。转移条件为自然语言描述，条件验证器判断是否满足转移。
    3. **优化算法**：迭代合并可合并的状态对（基于角色区分度、信息传递必要性、工具可统一性），减少状态数量，提升系统鲁棒性。无需外部数据。
    4. **部署阶段**：从初始状态开始，智能体执行指令，条件验证器检查输出是否符合转移条件；若满足则转移并传递信息（支持循环回溯）；若不满足则空转移（在当前状态重新执行），直至达到最终状态或超过最大迭代次数。
- **与传统结构的关系**：线性、辩论、协调器三种结构均可视为 FSM 的特化版本。FSM 通过自定义条件验证器和任意状态回溯，提供了最大灵活性。

### 实验设计

- **使用的数据集/场景**：
    - **文本任务**：Trivial Creative Writing（100个故事生成任务，每个含多个问题）、GPQA(Diamond)（198个研究生级科学选择题）。
    - **机器学习任务**：ML Bench（5个数据集：Titanic、House Prices、SCTP、ICR、SVPC），要求训练并报告指标。
    - **软件开发任务**：5个代表性软件（2048游戏、贪吃蛇、打砖块、Excel应用、天气应用），设计客观检查点（可访问性、功能完整性等）。
- **Benchmark**：对比方法包括：
    - 基础提示方法：Direct、CoT、CoT-SC、llm-debate、Self-Refine。
    - 自动设计方法：SPP、AutoAgents、EvoAgent（仅部分对比）。
    - 人工设计框架：MetaGPT、AutoGen、OpenInterpreter、TaskWeaver、DataInterpreter。
- **评估指标**：
    - 文本任务：成功率（故事覆盖答案比例 / 正确率）。
    - ML Bench：归一化性能分数（NPS，基于 F1、准确率、RMSE 等）。
    - 软件开发：每个软件4个客观检查点，通过率。

### 资源与算力

- **论文未明确说明 GPU 型号、数量、训练时长**。实验基于 GPT-4o（温度=0），所有生成和推理均通过 OpenAI API 完成，未涉及自训练。文中仅提及 token 成本分析（如 ML Bench 5任务总 token 消费约 46k，软件开发约 48k），未涉及硬件算力。

### 实验数量与充分性

- **实验组数**：
    - 文本任务：3组（Writing、GPQA）+ 消融。
    - ML Bench：5个数据集 + 转移实验（基础模型质量）。
    - 软件开发：5个任务 + 消融。
    - 消融实验：工具使用、回溯、优化（共4项消融，每项分别针对不同任务）。
    - 总计约 **15+ 组不同场景下的定量结果**，以及定性案例分析。
- **充分性判断**：
    - **充分**：覆盖了文本、代码、ML 三大类任务，对比了多种基线（包括人工设计、自动设计），并进行了全面的消融研究（工具、回溯、优化）和基础模型质量分析。
    - **客观公平**：使用固定种子（温度=0）保证可重复性，基准数据集和检查点设计明确。但未在开源 LLM（如 LLaMA）上验证，可能与实际部署环境有偏差。

### 论文的主要结论与发现

- MetaAgent 自动生成的 FSM 多智能体系统在 **所有测试任务上超越其他自动设计方法**，且与人工设计的 SOTA 系统（如 DataInterpreter、MetaGPT）性能相当甚至更优：
    - 文本任务：比最优提示方法（SPP）高出 **9%**（Writing：0.86 vs 0.79；GPQA：0.60 vs 0.45）。
    - ML Bench：平均 NPS 0.83，达到 DataInterpreter（0.86）的 **97%**，并超越所有其他自动设计方法（SPP 0.16，AutoAgents 0.00）。
    - 软件开发：平均通过率 0.85，超越 MetaGPT（0.35）、SPP（0.15）、AutoAgents（0.20）。
- **关键特性贡献**：工具使用、回溯、优化分别带来 8%-58% 的性能提升（消融实验证实）。
- **成本效率**：MetaAgent 的部署 token 成本低于 MetaGPT 和 AutoAgents，且设计阶段成本可控。

### 优点

1. **自动化程度高**：仅需任务描述，即可自动生成完整的 FSM 多智能体系统，无需人工干预。
2. **结构灵活**：FSM 支持空转移（迭代优化）和任意状态回溯，比线性/辩论结构更适应复杂任务。
3. **无需外部数据**：优化过程仅依赖 LLM 判断，不依赖标注数据或大量迭代。
4. **工具集成**：自动为智能体分配代码解释器、搜索引擎等工具，扩展能力边界。
5. **实验充分**：多领域任务 + 消融 + 成本分析，结论扎实。

### 不足与局限

1. **依赖基础模型质量**：研究表明执行器（Executor）的 LLM 性能对结果影响更大（GPT3.5 替换 GPT4o 导致大幅下降），弱模型下框架可能失效。
2. **设计阶段可能产生冗余**：初始 FSM 状态数过多，虽有优化但仍可能因 LLM 决策误差导致次优结构。
3. **实验覆盖有限**：未涉及多模态任务、真实协作场景（如多人机交互）、工业级复杂软件系统。仅测试了小型游戏和简单 ML 任务。
4. **缺乏社区通用性**：测试仅限 GPT-4o，未在开源模型（如 LLaMA、Qwen）上验证，通用性存疑。
5. **稳定性风险**：条件验证器依赖 LLM 的语义理解，可能因 LLM 幻觉导致转移误判，论文未分析此类错误模式。

（完）
