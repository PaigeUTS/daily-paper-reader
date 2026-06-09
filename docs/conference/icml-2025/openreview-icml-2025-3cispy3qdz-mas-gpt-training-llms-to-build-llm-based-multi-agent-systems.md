---
title: "MAS-GPT: Training LLMs to Build LLM-based Multi-Agent Systems"
title_zh: MAS-GPT：训练大语言模型以构建基于LLM的多智能体系统
authors: "Rui Ye, Shuo Tang, Rui Ge, Yaxin Du, Zhenfei Yin, Siheng Chen, Jing Shao"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=3CiSpY3QdZ"
tags: ["query:agents-os"]
score: 8.0
evidence: 通过LLM自动生成多智能体系统
tldr: 当前构建多智能体系统依赖人工配置或高级LLM多次调用，成本高且适应性差。本文将该过程重构为生成式语言任务，设计了一致性数据构建流程，训练出开源中型LLM MAS-GPT，能根据用户查询自动生成可执行的多智能体系统代码。实验表明该方法降低了构建成本并提升了适应性。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-3cispy3qdz/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 860, \"height\": 208, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3cispy3qdz/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 868, \"height\": 379, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3cispy3qdz/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1780, \"height\": 674, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3cispy3qdz/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1710, \"height\": 471, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3cispy3qdz/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1716, \"height\": 480, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3cispy3qdz/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1781, \"height\": 1055, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3cispy3qdz/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1666, \"height\": 2324, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3cispy3qdz/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1668, \"height\": 561, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-3cispy3qdz/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1766, \"height\": 426, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3cispy3qdz/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 860, \"height\": 132, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3cispy3qdz/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 854, \"height\": 758, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3cispy3qdz/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 859, \"height\": 240, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3cispy3qdz/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 855, \"height\": 133, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3cispy3qdz/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1743, \"height\": 1443, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3cispy3qdz/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1780, \"height\": 403, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3cispy3qdz/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1735, \"height\": 880, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3cispy3qdz/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1727, \"height\": 1765, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3cispy3qdz/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1227, \"height\": 170, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3cispy3qdz/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1585, \"height\": 1336, \"label\": \"Table\"}]"
motivation: 现有构建多智能体系统方法依赖人工或多次调用高级LLM，成本高且不灵活。
method: 将构建过程转化为生成式语言任务，设计一致性数据流程，训练MAS-GPT模型。
result: MAS-GPT能根据用户查询自动产生可执行的多智能体系统代码，降低构建成本。
conclusion: 本工作为自动化构建多智能体系统提供了新范式，提升了效率和适应性。
---

## Abstract
LLM-based multi-agent systems (MAS) have shown significant potential in tackling diverse tasks.
However, to design effective MAS, existing approaches heavily rely on manual configurations or multiple calls of advanced LLMs, resulting in inadaptability and high inference costs.
In this paper, we simplify the process of building an MAS by reframing it as a generative language task, where the input is a user query and the output is a corresponding MAS.
To address this novel task, we unify the representation of MAS as executable code and propose a consistency-oriented data construction pipeline to create a high-quality dataset comprising coherent and consistent query-MAS pairs.
Using this dataset, we train MAS-GPT, an open-source medium-sized LLM that is capable of generating query-adaptive MAS within a single LLM inference. The generated MAS can be seamlessly applied to process user queries and deliver high-quality responses. Extensive experiments on 9 benchmarks and 5 LLMs show that the proposed MAS-GPT consistently outperforms 10+ baseline MAS methods on diverse settings, indicating MAS-GPT's high effectiveness, efficiency and strong generalization ability.
The codes are released at \url{https://github.com/rui-ye/MAS-GPT}.

---

## 论文详细总结（自动生成）

### 1. 核心问题与整体含义
- **研究动机**：现有的基于LLM的多智能体系统（MAS）设计要么依赖人工配置（如MetaGPT、ChatDev），导致系统一成不变、不适应多样化任务；要么通过多次调用高级LLM（如AFlow、DyLAN）自动调整，但推理成本高昂（数十次API调用），且多依赖验证集。
- **整体含义**：本文提出新范式——将构建MAS视为生成式语言任务，使得根据用户查询生成对应MAS像查询ChatGPT一样简单。训练得到的MAS-GPT能够在单次LLM推理中输出可执行MAS代码，显著降低构建成本并提升适应性，推动MAS在真实场景中的规模化应用。

### 2. 方法论
- **核心思想**：将构建MAS从人工/多步优化转变为“输入查询 → 输出可执行MAS代码”的端到端生成任务。
- **关键技术细节**：
  - **统一MAS表示**：将MAS定义为一个Python `forward` 函数，其中agent的提示词设为变量，LLM调用设为函数调用，agent间交互通过字符串拼接实现（图2）。
  - **一致性导向数据构建流水线**（图3左）：
    1. **查询池与MAS池构建**：收集多样化可验证查询，实现40+种基础MAS（含CoT、角色扮演、代码执行等元素）。
    2. **查询-MAS对评估**：对每对查询与MAS执行推理，根据答案正确性打分（1或0）。
    3. **组间一致性选择**：对相似查询（基于元数据或嵌入聚类）分组，每组选择累积得分最高的MAS作为共享代表，增强跨查询一致性，便于模型学习通用模式。
    4. **组内一致性精炼**：用高级LLM（GPT-4o）调整MAS使其更贴合查询（如去除无关agent），并生成推理语句解释关联；若精炼后性能不下降则保留，否则回退原MAS。
  - **训练**：使用SFT在开源中型LLM `Qwen2.5-Coder-32B-Instruct` 上微调，输入为系统提示+用户查询，输出为推理语句+MAS代码。

### 3. 实验设计
- **数据集/场景**：
  - 训练数据：从MATH、GSM8K、MBPP、MMLU、SciQ等选取约11k条可验证查询。
  - 测试基准：9个benchmarks，涵盖数学（MATH、GSM8K、GSM-Hard、AIME-2024）、代码（HumanEval、HumanEval+）、通用QA（MMLU）、科学（GPQA、SciBench）。其中AIME-2024、HumanEval+、GPQA、SciBench为域外分布。
- **对比方法**：10+基线，包括Single、Chain-of-Thought、Self-Consistency、LLM-Debate、Self-Refine、Quality-Diversity、SPP、AgentVerse、GPTSwarm、DyLAN、AFlow（任务特定优化）。
- **驱动LLM**：Llama-3-70B-Instruct、Qwen2.5-72B-Instruct、GPT-4o-mini、o1-preview、DeepSeek-R1。

### 4. 资源与算力
- 训练MAS-GPT使用 **16张A100 GPU**，有效batch size为32，训练3个epoch，学习率1e-5。
- 数据构建阶段使用 **Llama-3-70B-Instruct** 进行推理评估，但文中未明确其使用的GPU数量或时长。
- **注意**：文中未提供训练总时长或具体GPU小时数，仅指出训练是一次性成本；推理时仅需单次32B模型调用，成本可控。

### 5. 实验数量与充分性
- **大规模实验**：共涉及9个benchmarks、5种不同规模的驱动LLM、10+基线方法，并在多个域外任务上评估，覆盖数学、代码、科学、通用知识。
- **消融实验**：
  - 验证组间一致性选择（对比随机映射）在MATH上提升8.39%。
  - 验证组内精炼中的MAS调整（Refine-A）与推理过程（Refine-R）各自的贡献。
  - 数据量扩展实验（0→100→1000→10000），展示性能随数据量增长趋势。
  - 模型规模扩展实验（7B、14B、32B），证明更大模型更优。
- **充分性与公平性**：所有对比方法在相同驱动LLM下执行，测试集与训练集分布分离；MAS-GPT的MAS生成不依赖验证集，避免“过拟合”到特定领域。
- **结论**：实验设计全面、客观，结果一致证明MAS-GPT的有效性与泛化性。

### 6. 主要结论与发现
- **有效性**：MAS-GPT在平均性能上显著优于10+基线（表1），尤其在域外任务（GPQA、SciBench）上仍表现最佳。
- **兼容性**：无论驱动LLM是Llama-3、Qwen2.5还是GPT-4o-mini，MAS-GPT均持续领先（表3）。
- **增强强推理模型**：在AIME-2024上，MAS-GPT为o1-preview带来13.3%的绝对提升，为DeepSeek-R1带来10.0%的提升。
- **生成能力**：MAS-GPT并非简单记忆训练数据，而是生成新颖、查询依存的多智能体结构（表5及附录B案例）。
- **扩展性**：数据量和模型大小增加均能持续提升性能，表明该方法具有良好扩展潜力。

### 7. 优点
- **方法创新**：首次将MAS构建转化为单次LLM推理的生成任务，降低应用门槛。
- **统一表示**：使用Python代码表示MAS，天然可执行，便于集成多种工具（如代码执行、测试）。
- **数据构建**：提出组间与组内一致性导向的流水线，有效增强模型学习模式，减少混淆。
- **实验覆盖广**：9个基准、5种LLM、10+对比，验证了强泛化性；同时进行充分消融和扩展分析。
- **开源可复现**：代码已公开，有利于社区进一步研究和应用。

### 8. 不足与局限
- **MAS池多样性有限**：初始仅40+种MAS设计，依赖人工实现，可能未覆盖所有有效结构；训练集也可能因组间选择偏好某些高性能MAS而产生偏差。
- **缺乏工具集成**：当前仅基于代码执行，未整合多模态处理、网页搜索等外部工具，限制处理复杂任务的能力。
- **仅使用SFT**：未探索强化学习（RL）等方法让MAS-GPT自主探索和迭代优化，作者也指出这是未来方向。
- **训练资源开销**：虽然一次性，但构建高质量数据（使用大模型推理和精炼）及训练32B模型仍需要较多计算资源。
- **应用限制**：生成的MAS代码依赖于预设的 `utils.py` 函数（如 `call_llm`），需确保运行环境支持；存在代码执行失败的风险（图5a显示少量失败）。

（完）
