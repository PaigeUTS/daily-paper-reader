---
title: "Heterogeneous Swarms: Jointly Optimizing Model Roles and Weights for Multi-LLM Systems"
title_zh: 异构群：联合优化多LLM系统中的模型角色与权重
authors: "Shangbin Feng, Zifeng Wang, Palash Goyal, Yike Wang, Weijia Shi, Huang Xia, Hamid Palangi, Luke Zettlemoyer, Yulia Tsvetkov, Chen-Yu Lee, Tomas Pfister"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=zYEZ5KqtDO"
tags: ["query:agents-os"]
score: 7.0
evidence: 在多LLM异构系统中联合优化模型角色与权重
tldr: 多LLM系统面临着模型角色分配和权重优化缺乏联合设计的问题。本文提出异构群算法，将多LLM系统表示为有向无环图，通过迭代的角色步和权重步联合优化模型角色与权重。实验表明该方法在多个任务上提升了系统效用（如准确率）。该工作为设计高效的异构多智能体系统提供了可扩展的框架，直接支持异构计算基础设施中智能代理的优化。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyez5kqtdo/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 593, \"height\": 243, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyez5kqtdo/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1441, \"height\": 610, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyez5kqtdo/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1442, \"height\": 492, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyez5kqtdo/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1447, \"height\": 600, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyez5kqtdo/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1097, \"height\": 408, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyez5kqtdo/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 564, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyez5kqtdo/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 719, \"height\": 421, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyez5kqtdo/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 698, \"height\": 428, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyez5kqtdo/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 703, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyez5kqtdo/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 703, \"height\": 437, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyez5kqtdo/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 566, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyez5kqtdo/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 704, \"height\": 427, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyez5kqtdo/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1444, \"height\": 1077, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyez5kqtdo/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1436, \"height\": 1068, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zyez5kqtdo/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1449, \"height\": 1459, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-zyez5kqtdo/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1415, \"height\": 518, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zyez5kqtdo/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1444, \"height\": 684, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zyez5kqtdo/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1425, \"height\": 107, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zyez5kqtdo/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1446, \"height\": 327, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zyez5kqtdo/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 586, \"height\": 319, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zyez5kqtdo/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 584, \"height\": 319, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zyez5kqtdo/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 722, \"height\": 145, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zyez5kqtdo/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 584, \"height\": 416, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zyez5kqtdo/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1015, \"height\": 310, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zyez5kqtdo/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 721, \"height\": 634, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zyez5kqtdo/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1392, \"height\": 510, \"label\": \"Table\"}]"
motivation: 现有方法缺乏对多LLM系统中模型角色和权重的联合优化，无法高效利用异构模型能力。
method: 将多LLM系统表示为有向无环图，通过角色步与权重步迭代优化模型角色分配与权重，使用粒子群算法优化邻接矩阵。
result: 在多个任务上通过优化角色和权重提升了系统效用（如准确率）。
conclusion: 该方法为设计高效异构多智能体系统提供了可扩展的框架。
---

## Abstract
We propose Heterogeneous Swarms, an algorithm to design multi-LLM systems by jointly optimizing model roles and weights. We represent multi-LLM systems as directed acyclic graphs (DAGs) of LLMs with topological message passing for collaborative generation. Given a pool of LLM experts and a utility function, Heterogeneous Swarms employs two iterative steps: role-step and weight-step. For role-step, we interpret model roles as learning a DAG that specifies the flow of inputs and outputs between LLMs. Starting from a swarm of random continuous adjacency matrices, we decode them into discrete DAGs, call the LLMs in topological order, evaluate on the utility function (e.g. accuracy on a task), and optimize the adjacency matrices with particle swarm optimization based on the utility score. For weight-step, we assess the contribution of individual LLMs in the multi-LLM systems and optimize model weights with swarm intelligence. We propose JFK-score to quantify the individual contribution of each LLM in the best-found DAG of the role-step, then optimize model weights with particle swarm optimization based on the JFK-score. Experiments demonstrate that Heterogeneous Swarms outperforms 17 role- and/or weight-based baselines by 18.5% on average across 12 tasks. Further analysis reveals that Heterogeneous Swarms discovers multi-LLM systems with heterogeneous model roles and substantial collaborative gains, and benefits from the diversity of language models.

---

## 论文详细总结（自动生成）

# 论文《Heterogeneous Swarms: Jointly Optimizing Model Roles and Weights for Multi-LLM Systems》详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：现有多LLM系统通常采用**固定角色**（例如通过手工设计提示词分配模型职责）或**固定权重**（例如静态模型合并或固定集成），无法灵活适应不同任务和上下文。这些方法将模型角色和权重视为分离的静态因素，导致系统在面对新任务时需要大量人工调优，难以自动化和规模化。
- **核心问题**：如何**联合优化**多LLM系统中每个模型的**角色**（即输入输出关系）和**权重**（即模型参数），使得系统能够根据目标效用函数（如任务准确率）自适应地发现最优协作结构。
- **整体含义**：论文提出**Heterogeneous Swarms**算法，将多LLM系统视为**有向无环图（DAG）**，通过交替优化图结构和模型权重，实现异构模型的灵活协作，从而提升系统在多样化任务上的表现。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：模型角色由DAG中的边定义（哪个LLM的输出作为哪个LLM的输入），模型权重通过粒子群优化（PSO）调整。角色步（role-step）优化DAG结构，权重步（weight-step）优化每个LLM的参数，二者交替迭代直至收敛。
- **关键技术细节**：
  - **角色步**：将角色学习视为图学习问题。初始化一组连续邻接矩阵（表示边存在的概率），通过提出的**G-Decode**算法将其解码为离散DAG（保证有向无环）。按拓扑序调用LLM，计算效用函数（如准确率），然后用PSO更新邻接矩阵，使候选图向更优方向移动。
  - **权重步**：使用**JFK-score**评估每个LLM在系统中的个体贡献。具体做法：将LLM随机分配到最佳DAG的各个位置，多次重复，统计每个LLM出现的频率及对应系统效用，加权平均得到贡献分数。然后通过PSO优化LLM的权重参数（使贡献大的模型更优）。
  - **优化流程**：算法交替执行角色步和权重步（算法3），直到效用不再提升或达到最大迭代次数。最终得到联合优化的DAG结构及模型权重。
  - **关键超参数**：PSO中的惯性系数、认知系数、社会系数、排斥系数等，通过网格搜索确定。

## 3. 实验设计

- **数据集**：使用12个任务，分为4类：
  - **知识**：MMLU-pro、Knowledge Crosswords、COM2
  - **推理**：GSM8k、NLGraph、Normad
  - **智能体**：GAIA-text、AgentBench（知识图谱子任务、横向思维谜题子任务）
  - **杂项**：Qasper（长上下文）、AbstainQA（可靠性）、WoW（LLM裁判）
- **基准方法**：对比17种基线，涵盖5类：
  - **平凡基线**：最佳单模型、预测集成
  - **静态权重**：Data Merge、Uniform Soup、Dare-Ties
  - **动态权重**：Greedy Soup、Pack of LLMs、LoraHub、Model Swarms
  - **静态角色**：链式、星型结构
  - **动态角色**：GPT-Swarm、Meta-Agent、Agent-Prune、GNNs、AgentVerse、MACNet
- **模型与实现**：默认使用10个Gemma-7B微调变体（基于Tulu-v2领域微调），补充实验使用Mistral-7B。超参数通过网格搜索确定，报告最佳结果。

## 4. 资源与算力

- 文中明确说明：实验使用**16块A100 GPU，每块40GB显存**。
- 优化过程每迭代一次，角色步调用模型推理O(nN)次，权重步O(nM)次（n=10，N=10，M=10），整体计算成本与基线中动态方法相当。
- 未报告具体训练总时长，但给出了图7显示每轮迭代时间随GPU数量变化：使用10块GPU时每轮约需要一定时间（原文未给出数值，仅展示趋势）。

## 5. 实验数量与充分性

- **实验数量**：主实验在12个数据集上与17种基线对比；消融实验包括：移除角色步/权重步、稀疏化策略（阈值剪枝与L1正则化）、多样性分析（不同模型重复次数）、参数量缩放（模型数量2→10）、混合大小模型、与更大单模型对比、与增强推理方法对比（CoT/GoT）、泛化性测试（跨任务迁移）等。
- **充分性与公平性**：实验覆盖了知识、推理、智能体、多种杂项任务，基线涵盖当前主流方法。统计显著性用z检验标注。控制变量（如固定模型池为10个Gemma-7B）使对比公平。但未对不同随机种子进行重复实验报告方差（仅在表8脚注提及统计显著性）。

## 6. 主要结论与发现

- **性能优势**：Heterogeneous Swarms在11/12个数据集上取得最佳，平均超过第二名基线18.5%。
- **角色与权重的重要性随任务变化**：知识类任务中权重优化更重要，智能体类任务中角色优化更重要。联合优化能灵活适应两种场景。
- **协作增益**：通过定义协作增益（C-Gain）衡量系统是否超过个体累加效果，系统在所有任务上获得正向增益（平均0.213），尤其能解决部分单模型无法解决的问题。
- **多样性关键**：模型池多样性越高（10×1配置），性能提升越显著（相对提升89%）。
- **稀疏性与加速**：阈值剪枝或L1正则化可在轻微性能损失下显著减少边数，加速推理。
- **弱模型协作胜强模型**：通过多弱模型协作可超越最佳单模型，甚至超过参数更大的单独模型。

## 7. 优点

- **创新性**：首次联合优化多LLM系统的角色和权重，提出基于粒子群优化的图搜索算法（G-Decode）和个体贡献量化方法（JFK-score）。
- **灵活性**：角色由DAG学习自动发现，无需手工设计提示；权重通过PSO连续优化，可适应不同任务。
- **实验全面**：覆盖12个多样化任务，17个强基线，大量消融和扩展分析（缩放、迁移、多样性、稀疏化等），结果统计显著。
- **实用价值**：提供多种加速策略（稀疏化、Dropout），探讨不同模型大小混合协作，对实际部署有指导意义。

## 8. 不足与局限

- **架构限制**：默认要求所有LLM共享同一架构（Gemma-7B），以便权重步在相同参数空间优化。若模型异构，则权重步不可用，只能依赖角色步。
- **计算成本**：优化过程需多次调用LLM推理，计算开销较大（虽可通过稀疏化加速）。论文未与最简方案（如单一模型推理）公平比较总时间。
- **实验覆盖**：未在更大规模模型池（如>10个模型）上验证扩展性；未测试真实多轮人机对话或复杂智能体场景；仅使用Gemma和Mistral系列，泛化性可能受限。
- **随机性**：PSO和随机赋值引入随机性，但论文未报告多次重复实验的方差（仅主表未列误差棒，仅在一处脚注给出统计显著性），可重复性略受影响。
- **伦理风险**：指出若模型中混入恶意或偏见模型，可能通过DAG产生级联危害，但未提出具体防御机制。

（完）
