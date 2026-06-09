---
title: "G-Designer: Architecting Multi-agent Communication Topologies via Graph Neural Networks"
title_zh: G-Designer：通过图神经网络设计多智能体通信拓扑
authors: "Guibin Zhang, Yanwei Yue, Xiangguo Sun, Guancheng Wan, Miao Yu, Junfeng Fang, Kun Wang, Tianlong Chen, Dawei Cheng"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=LpE54NUnmO"
tags: ["query:agents-os"]
score: 7.0
evidence: 自适应通信拓扑设计用于多智能体系统，与设计智能体基础设施一致
tldr: 多智能体通信拓扑选择困难，且固定拓扑易浪费token。本文提出G-Designer，利用图神经网络为每个任务自适应设计通信拓扑。方法在保持解答质量的同时减少不必要的通信开销，为智能体系统的通信拓扑优化提供了高效方案，有助于异构计算基础设施中智能体协作的优化。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-lpe54nunmo/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 822, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lpe54nunmo/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 853, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lpe54nunmo/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1762, \"height\": 1031, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lpe54nunmo/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 841, \"height\": 677, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lpe54nunmo/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 852, \"height\": 301, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lpe54nunmo/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 494, \"height\": 202, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lpe54nunmo/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 117, \"height\": 143, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lpe54nunmo/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 107, \"height\": 143, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lpe54nunmo/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 623, \"height\": 224, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lpe54nunmo/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 515, \"height\": 202, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-lpe54nunmo/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 515, \"height\": 239, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-lpe54nunmo/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1766, \"height\": 884, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lpe54nunmo/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 864, \"height\": 229, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lpe54nunmo/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 857, \"height\": 353, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lpe54nunmo/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1307, \"height\": 400, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lpe54nunmo/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 661, \"height\": 139, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-lpe54nunmo/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 907, \"height\": 1023, \"label\": \"Table\"}]"
motivation: 多智能体系统中通信拓扑选择混乱，固定拓扑导致token浪费。
method: 使用图神经网络动态生成任务相关的定制通信拓扑。
result: 实验表明G-Designer在降低通信开销的同时保持或提升任务性能。
conclusion: G-Designer为智能体系统提供了自适应的通信拓扑设计，提升资源效率。
---

## Abstract
Recent advancements in large language model (LLM)-based agents have demonstrated that collective intelligence can significantly surpass the capabilities of individual agents, primarily due to well-crafted inter-agent communication topologies. Despite the diverse and high-performing designs available, practitioners often face confusion when selecting the most effective pipeline for their specific task: \textit{Which topology is the best choice for my task, avoiding unnecessary communication token overhead while ensuring high-quality solution?} In response to this dilemma, we introduce G-Designer, an adaptive, efficient, and robust solution for multi-agent deployment, which dynamically designs task-aware, customized communication topologies. Specifically, G-Designer models the multi-agent system as a multi-agent network, leveraging a variational graph auto-encoder to encode both the nodes (agents) and a task-specific virtual node, and decodes a task-adaptive and high-performing communication topology. Extensive experiments on six benchmarks showcase that G-Designer is: \textbf{(1) high-performing}, achieving superior results on MMLU with accuracy at $84.50\\%$ and on HumanEval with pass@1 at $89.90\\%$; \textbf{(2) task-adaptive}, architecting communication protocols tailored to task difficulty, reducing token consumption by up to $95.33\\%$ on HumanEval; and \textbf{(3) adversarially robust}, defending against agent adversarial attacks with merely $0.3\\%$ accuracy drop.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：基于大语言模型（LLM）的多智能体系统通过精心设计的通信拓扑实现了超越单个智能体的集体智能。然而，实践中存在“拓扑选择困境”——不同任务（如简单的高中生物题 vs 困难的大学数学题）对拓扑结构的需求截然不同：简单任务使用复杂拓扑会浪费大量Token，而困难任务若使用简单拓扑则性能不足。现有方法（如Chain、Star、Tree、Complete Graph、GPTSwarm等）均是**输入无关**的静态或仅迭代优化结构，无法根据具体任务自适应调整。
- **核心问题**：如何为给定任务自动设计一种**高性能、低开销、鲁棒**的通信拓扑，使得智能体既能高效协作又不浪费Token。
- **整体含义**：G-Designer 提出了一种基于图神经网络（GNN）的自适应拓扑生成框架，首次将多智能体通信拓扑设计形式化为一个**任务感知的图生成问题**，并通过变分图自编码器与策略梯度优化实现动态定制。

## 2. 方法论：核心思想、关键技术细节、公式/算法流程

- **核心思想**：将多智能体系统建模为一个**多智能体网络**，其中每个智能体及其属性（LLM基座、角色、状态、插件）作为节点，通信关系作为边。引入一个**任务特定的虚拟节点**（virtual node），通过变分图自编码器（VGAE）编码所有节点和任务信息，再解码出稀疏、高性能的通信拓扑。
- **关键技术细节**：
  1. **多智能体网络构建**：
     - 每个智能体 `vi` 包含 `{Base_i, Role_i, State_i, Plugin_i}`，通过轻量文本编码器（如all-MiniLM-L6-v2）获得节点特征 `xi`。
     - 将查询 `Q` 编码为任务虚拟节点 `xtask`，并与所有智能体节点双向连接。
     - 用户或LLM可提供一个简单的**锚点拓扑**（如链式结构）作为先验，记为 `A_anchor`。
  2. **通信拓扑生成**（VGAE编码-解码）：
     - **编码器**：两层GCN计算后验概率 `q(H|X, A_anchor)`，输出隐变量 `H`。
     - **解码器第一阶段（草图生成）**：通过 `ps(S|H)` 生成稠密草图邻接矩阵 `S`，其中 `ps(S_ij=1) = Sigmoid( FFN([h_i, h_j, h_task]) )` 经Gumbel-Softmax采样得到。
     - **解码器第二阶段（细化解码）**：对草图 `S` 施加**稀疏正则化**和**锚点正则化**，优化目标：
       ```
       min_{tilde{S}} 1/2 ||S - ZWZ^T||_F^2 + ζ||W||_* + 1/2 ||A_anchor - ZWZ^T||_F^2
       ```
       其中 `tilde{S} = ZWZ^T`，`||W||_*` 为核范数（用于稀疏化），前两项保持与草图相似，最后一项保持与锚点拓扑相似。最终得到稀疏的通信图 `G_com`。
  3. **策略优化**：
     - 在生成的拓扑 `G_com` 上执行多轮对话（K=3），通过聚合函数（如汇总代理）得到最终答案 `a^(K)`。
     - 优化目标：最大化任务效用 `u(G_com(Q))`。由于不可微分，使用策略梯度（REINFORCE）近似：
       ```
       ∇_Θ E[ u ] ≈ 1/M * Σ u(a_m) * ∇_Θ log P(G_m)
       ```
     - 总损失：`L = L_utility + L_anchor + L_sparse`。

- **算法流程**（文字描述）：
  1. 为用户输入的查询 `Q`，通过NodeEncoder将N个智能体和任务虚拟节点编码为特征矩阵 `X`。
  2. 设置锚点拓扑 `A_anchor`（实验中默认为链式）。
  3. VGAE编码得到隐表示 `H`。
  4. 解码器先生成草图 `S`，再经正则化得到稀疏通信图 `G_com`。
  5. 在 `G_com` 上执行K轮对话，得到输出 `a`。
  6. 用策略梯度更新图自编码器的参数（仅用少量查询样本训练，B'=40/80）。

## 3. 实验设计：数据集、Benchmark、对比方法

- **数据集**（三类六种）：
  - 通用推理：MMLU（153题，多选）
  - 数学推理：GSM8K（1319题）、MultiArith（600题）、SVAMP（1000题）、AQuA（254题）
  - 代码生成：HumanEval（164题，Pass@1）

- **基准（Benchmark）**：六个数据集上的准确率或Pass@1指标。

- **对比方法**：
  - **单智能体基线**：Vanilla、CoT、ComplexCoT、Self-Consistency (SC)、PHP。
  - **空间多智能体拓扑**：Chain、Star、Tree、Complete Graph、Random Graph、AutoGen、MetaGPT、LLM-Blender、LLM-Debate、DyLAN、GPTSwarm。
- **设置**：每个多智能体方法默认使用5个基于 `gpt-4-1106-preview` 的智能体（HumanEval部分测试MetaGPT），温度设为1；单智能体温度0。所有多智能体方法进行3轮对话。

## 4. 资源与算力

- **显存开销**：训练时使用GPU，文中给出表5：当智能体数量从5增加到1000时，GPU内存仅从2.7GB增长到3.8GB，说明G-Designer在训练阶段**资源友好**。
- **Token消耗与时间**：表2对比GSM8K上各方法的训练/推理Token数和时间：
  - G-Designer：训练Token 2.7×10^6，推理Token 8.2×10^6，总体Token 8.5×10^6；训练时间0.3h，推理时间2.3h。
  - 相比DyLAN（总体Token 2.2×10^7，训练2.8h，推理4.6h）和GPTSwarm（总体1.4×10^7，训练2.1h，推理2.8h），G-Designer效率和性能均更优。
- **GPU型号、具体数量**：文中未明确说明GPU型号与数量，仅提到训练内存需求低。

## 5. 实验数量与充分性

- **实验数量**：
  - **主实验结果**（表1）：在6个数据集上与17种基线进行全面对比，涵盖单智能体和多智能体方法。
  - **效率分析**（表2，图4）：展示Token消耗、时间与性能的关系。
  - **可扩展性**（表6）：从5个智能体扩展到20个智能体，对比Chain、Complete Graph、GPTSwarm。
  - **鲁棒性测试**（图5）：对5个智能体中1个实施系统提示攻击，对比10种方法前后准确率。
  - **消融实验**（表3）：4种变体（w/o SR, w/o Anchor, w/o NodeEncoder, w/o v_task）在MMLU和GSM8K上测试。
  - **案例研究**（图6）：展示不同难度任务下的拓扑设计结果。
- **充分性与公平性**：
  - 实验覆盖了主流基线、多种任务类型（通用、数学、代码），并包含消融、鲁棒、扩展性分析，较为充分。
  - 对比方法均采用相同智能体数量、相同基础模型（gpt-4/gpt-3.5），训练Token与推理Token均公开对比，具有公平性。
  - 但训练仅使用少量查询（B'=40/80），可能低估跨领域泛化时的不稳定性；且部分基线（如MetaGPT）仅在HumanEval上报告结果，其他任务未覆盖。

## 6. 主要结论与发现

1. **高性能**：G-Designer在6个数据集中的5个上取得最优（MMLU 84.50%，HumanEval 89.90% pass@1），平均准确率89.84%，超过所有对比方法。
2. **任务自适应**：拓扑结构随任务难度动态调整（简单任务用稀疏链式，困难任务用更稠密图），例如在HumanEval上最多减少95.33%的Token消耗。
3. **鲁棒性**：面对单节点系统提示攻击，准确率仅下降0.3%（而Chain下降11.0%，DyLAN下降6.2%），得益于节点编码可检测恶意输入并剪枝相应边。
4. **Token经济性**：在全部四个测试基准上，G-Designer以最低Token消耗获得最高性能，例如在SVAMP上仅用DyLAN的23.7% Token。
5. **可扩展性**：20个智能体时，使用仅GPTSwarm 6.11%的Token，性能超GPTSwarm 2.44%。

## 7. 优点

- **方法创新**：首次将多智能体拓扑设计建模为**任务感知的图生成问题**，引入虚拟任务节点实现自适应，兼顾性能与效率。
- **设计优雅**：VGAE + 双层解码（草图+稀疏化） + 锚点正则化，既保持灵活性又避免偏离实际直觉。
- **鲁棒性突出**：动态调整拓扑能力使其天然防御部分节点被攻击，远超静态拓扑。
- **资源友好**：训练显存需求极低（1000智能体仅3.8GB），训练Token和推理Token均显著少于同类自适应方法（如GPTSwarm）。
- **实验全面**：覆盖多领域任务、多种基线、消融、鲁棒、可扩展性、案例研究，结论可信。

## 8. 不足与局限

- **实验覆盖**：训练集仅用40-80个查询进行优化，虽在多个数据集上测试，但跨领域泛化风险仍存在（例如数学与代码任务混合训练的效果未探讨）。
- **依赖基础模型**：所有实验基于GPT-4和GPT-3.5，对小规模开源模型（如LLaMA）的性能未知；方法假设所有智能体调用相同LLM，现实中可能有异构LLM。
- **偏差风险**：锚点拓扑固定为链式，虽经正则化可调整，但可能引入初始偏好，影响极端情况下的最优性。
- **计算开销**：虽然训练阶段GPU内存低，但推理阶段仍需多次LLM调用（多轮对话+拓扑生成），在实际延迟敏感场景可能受限。
- **攻击场景单一**：鲁棒性测试仅针对单节点系统提示攻击，未考虑更复杂的对抗模式（如多节点同时攻击、数据中毒等）。
- **可复现性**：代码已开源，但超参数（如温度τ、系数ζ）仅在特定任务下调优，未见完整灵敏度分析。

（完）
