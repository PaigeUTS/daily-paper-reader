---
title: Multi-Agent Collaboration via Evolving Orchestration
title_zh: 基于演化编排的多智能体协作
authors: "Yufan Dang, Chen Qian, Xueheng Luo, Jingru Fan, Zihao Xie, Ruijie Shi, Weize Chen, Cheng Yang, Xiaoyin Che, Ye Tian, Xuantang Xiong, Lei Han, Zhiyuan Liu, Maosong Sun"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=L0xZPXT3le"
tags: ["query:agents-os"]
score: 7.0
evidence: 动态编排多智能体协作
tldr: 现有LLM多智能体协作依赖静态组织结构，难以适应复杂任务。本文提出傀儡师范式，由一个中央编排器动态指挥智能体，并通过强化学习训练编排器自适应排序和优先智能体。该方法提升了协作灵活性和可扩展性，为智能体异构计算基础设施的设计提供了参考。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-l0xzpxt3le/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1436, \"height\": 462, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l0xzpxt3le/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1445, \"height\": 410, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l0xzpxt3le/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 576, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l0xzpxt3le/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 775, \"height\": 618, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l0xzpxt3le/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1438, \"height\": 525, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l0xzpxt3le/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 564, \"height\": 610, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l0xzpxt3le/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 849, \"height\": 427, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l0xzpxt3le/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1443, \"height\": 1768, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l0xzpxt3le/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1424, \"height\": 1391, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l0xzpxt3le/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1445, \"height\": 1193, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-l0xzpxt3le/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1344, \"height\": 1090, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-l0xzpxt3le/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1445, \"height\": 755, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l0xzpxt3le/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 674, \"height\": 630, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-l0xzpxt3le/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1125, \"height\": 259, \"label\": \"Table\"}]"
motivation: 静态智能体组织架构无法适应任务复杂度和数量增长。
method: 提出傀儡师式编排范式，中央编排器动态指挥智能体，并使用强化学习训练。
result: 实现了灵活可演化的多智能体协作。
conclusion: 动态编排能有效提升多智能体系统的可扩展性和效率。
---

## Abstract
Large language models (LLMs) have achieved remarkable results across diverse downstream tasks, but their monolithic nature restricts scalability and efficiency in complex problem-solving. While recent research explores multi-agent collaboration among LLMs, most approaches rely on static organizational structures that struggle to adapt as task complexity and agent numbers grow, resulting in coordination overhead and inefficiencies. To this end, we propose a puppeteer-style paradigm for LLM-based multi-agent collaboration, where a centralized orchestrator ("puppeteer") dynamically directs agents ("puppets") in response to evolving task states. This orchestrator is trained via reinforcement learning to adaptively sequence and prioritize agents, enabling flexible and evolvable collective reasoning. Experiments on closed- and open-domain scenarios show that this method achieves superior performance with reduced computational costs. Analyses further reveal that the key improvements consistently stem from the emergence of more compact, cyclic reasoning structures under the orchestrator’s evolution. Our code is available at https://github.com/OpenBMB/ChatDev/tree/puppeteer.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义

研究动机：大型语言模型（LLM）在多个下游任务中表现优异，但其单体架构限制了在复杂问题求解中的可扩展性与效率。现有基于LLM的多智能体协作方法多依赖静态的组织结构（如预定义的图拓扑），随着任务复杂度与智能体数量的增长，这种刚性结构导致协调开销增加、系统性能下降、计算冗余和无效通信等问题。

核心含义：论文提出一种“傀儡师”范式（Puppeteer-style paradigm），由中央编排器（puppeteer）根据任务状态的演化动态地指挥多个智能体（puppets），并通过强化学习对编排策略进行训练，使系统能够自适应地排序和优先选择智能体，实现灵活且可演化的集体推理。该方法旨在同时最大化协作效果和计算效率。

## 2. 方法论

### 核心思想
- 将多智能体协作重新概念化为一个由中央编排器驱动的序列化推理过程。编排器在每个推理步骤基于当前全局系统状态 \( S_t \) 和任务描述 \( \tau \) 选择下一个激活的智能体 \( a_t \)。
- 编排过程被形式化为马尔可夫决策过程：\( a_t \sim \pi(S_t, \tau) \)，满足马尔可夫性。
- 智能体以有向图建模（节点为智能体，边为信息流），但通过拓扑遍历策略将图“展开”为推理序列，避免对整个拓扑空间进行穷举搜索。

### 关键技术细节
- **动态编排**：中央编排器（采用神经网络评分、嵌入相似度或Bradley-Terry方式）根据当前状态从智能体空间 \( \mathcal{A} \) 中选择一个智能体，该智能体执行推理映射 \( f_{a_t} \) 后更新系统状态 \( S_{t+1} = \Phi(S_t, o_t) \)。过程持续直到触发终止条件（如选择到终止智能体或资源耗尽），最终通过聚合函数 \( F_{\text{agg}} \) 得到整体解。
- **自适应进化**：利用REINFORCE算法优化编排策略的参数 \( \theta \)。目标函数为最大化轨迹期望回报 \( J(\theta) = \mathbb{E}_{\pi_\theta}[R(\tau)] \)，梯度近似为 \( \nabla_\theta J(\theta) \approx \frac{1}{N}\sum_{n=1}^N \sum_{t=1}^T \nabla_\theta \log \pi_\theta(a_t|S_t) \cdot R(\tau) \)。
- **奖励设计**：综合考虑解质量和计算效率。终态奖励 \( R_t = r - \lambda \cdot C_T \)（r为正确性/质量得分，\( \lambda \) 控制效率权重，\( C_t = F \cdot \log(1 + t/\phi) \) 为基于FLOPs或token的步成本）。非终态采用折扣累积 \( R_t = \gamma R_{t+1} - \lambda C_t \)。

## 3. 实验设计

### 数据集与场景
- **闭域任务**（精确客观推理）：
  - GSM-Hard：含大数多步算术题，评估数学推理。
  - MMLU-Pro：多学科多项选择题，评估事实知识与逻辑推理。
- **开域任务**（创造性、开放性）：
  - SRDD：真实软件需求，要求构建完整软件，评估完整性、可执行性、一致性。
  - CommonGen-Hard：用不相关概念生成连贯句子，评估语法、相关性、逻辑一致性与概念覆盖率。

### Benchmark 对比方法
按模型参数量分为两个子空间：
- **Mimas 子空间**（小模型）：Qwen-2.5-7B/14B, LLaMA-3.1-8B/3.2-3B, Mistral-7B/Nemo-12B 等。
- **Titan 子空间**（大模型）：GPT-4-Turbo, GPT-4o-Mini, Gemini-1.5-Pro/Flash, Claude-3-Sonnet/Haiku, Qwen-2.5-72B, LLaMA-3.1-405B 等。

基线方法包括：
- **纯模型**：直接使用单模型生成（无智能体编排）。
- **单智能体方法**：Self-Refine（迭代自纠正）、AFlow（MCTS优化工作流）。
- **多智能体方法**：MacNet（静态有向无环图组织）、EvoAgent（进化算法自动生成MAS）。

### 论文自身配置
- **Puppeteer-Mono**：所有智能体由同一模型驱动（Titan用LLaMA-3.1-405B，Mimas用LLaMA-3.1-8B）。
- **Puppeteer（默认）**：智能体由多种异构模型驱动。
- 智能体配备不同推理模式（任务分解、反思、精炼、批评、修改、总结、终止）和外部工具（WebViewer, WikiSearch, BingSearch, arXivSearch, Code Interpreter, File Reader）。
- 动态协作采用多数投票聚合输出。策略初始化用Llama-3.1变体，默认超参数：episode长度4，并行探索3，λ=0.1，γ=0.99。

## 4. 资源与算力

文中在附录C中明确说明：
- **GPU 型号与数量**：NVIDIA A800，8 块 GPU。
- **峰值显存使用**：每GPU 28.8–78.4 GB（因基准和任务复杂度而异）。
- **训练时间**：2–6 小时（因基准差异）。需注意：该时间是编排器在线训练的总体时间，包含多智能体推理与参数更新，难以与仅推理的基线直接比较。

## 5. 实验数量与充分性

- **主要实验**：在4个数据集（GSM-Hard, MMLU-Pro, SRDD, CommonGen-Hard）上，分别在Titan和Mimas两个子空间下测试了Puppeteer（默认）和Puppeteer-Mono，并对比了初始阶段与进化阶段的表现。共报告约20组性能结果（表1）。
- **消融与额外实验**：
  - 超参数λ的影响（0.03 vs 0.10对token消耗和准确率的影响，图3）。
  - 拓扑约束（深度、宽度）对效果与效率的影响（图7）。
  - 在ALFWorld（具身环境）上的扩展实验（附录A.4）。
  - 图拓扑演化分析：图密度分布、循环分布（图6）。
  - 性能-成本权衡曲线（图9）和token消耗、智能体数量变化趋势（图2/8）。
- **公平性**：所有基线在相同设置下重新运行（文中有述），采用†标记统计显著性。实验覆盖了闭域和开域、不同模型规模、单模型与异构模型、初始与进化阶段，对比了代表性基线，充分且客观。

## 6. 主要结论与发现

- **性能提升且效率更优**：Puppeteer在进化阶段一致取得最高的平均性能，且token消耗和智能体数量随学习过程下降（图2），说明性能提升不以额外计算开销为代价，而是同时实现效果与效率的改进。
- **拓扑结构演化规律**：编排器引导下，多智能体拓扑趋向紧凑（图密度增加）和循环化（循环结构增多）。这种紧凑、循环的推理结构是性能提升的关键来源。
- **奖励设计有效**：通过调整λ可灵活控制准确性与效率的权衡；纳入效率惩罚使得系统自然趋向更短的推理链或更低成本的智能体选择。
- **异构模型优势**：Puppeteer（异构）通常优于Puppeteer-Mono（单模型），表明异构智能体的互补协作能进一步提升性能。
- **可迁移性**：在ALFWorld具身任务上也展示了适用性（附录A.4）。

## 7. 优点

- **方法创新**：将多智能体协作从静态结构转向动态、可学习的编排，结合RL实现自适应进化，使系统能主动修剪无用智能体、提升效率。
- **奖励设计巧妙**：同时考虑解质量和计算成本，并支持通过超参数λ灵活调节权衡，实现了效果与效率的联合优化。
- **实验覆盖全面**：涵盖闭域/开域、不同模型规模、单模型/多模型、初始/进化阶段、多种基线，并附带消融与结构分析，结论可信度高。
- **分析深入**：通过图密度、循环分布等定量指标揭示了进化过程中拓扑结构的变化规律，解释了性能提升来源，增强了方法的可解释性。
- **代码开源**：提供代码仓库，有助于复现和进一步研究。

## 8. 不足与局限

- **奖励粒度粗糙**：当前仅依靠最终输出质量和总token数作为奖励信号，缺乏中间步骤的细粒度监督。引入步骤级正确性反馈可能进一步提升优化效率。
- **智能体与工具固定**：假设预定义的智能体集和工具集，无法在推理过程中动态添加或修改智能体/工具，限制了应对新任务的灵活性。
- **偶发协调问题**：有时出现智能体间的误协调或“欺骗性一致”（deceptive agreement），需要更鲁棒的交互协议和激励机制。
- **计算资源比较困难**：由于编排器采用在线RL（推理与训练交替），与仅基于推理的基线（如AFlow）的计算成本难以直接对比，文中未提供严格的效率公平比较（如总FLOPs）。
- **超参数敏感**：λ、深度/宽度上限等需针对任务调整，未自动适应不同难度的任务或弱模型场景（附录A.2提及部分任务性能-成本未显著提升可能与超参数设置有关）。

（完）
