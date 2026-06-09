---
title: Multi-agent Architecture Search via Agentic Supernet
title_zh: 基于代理超网络的多智能体架构搜索
authors: "Guibin Zhang, Luyang Niu, Junfeng Fang, Kun Wang, LEI BAI, Xiang Wang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=imcyVlzpXh"
tags: ["query:agents-os"]
score: 8.0
evidence: 自动化多智能体架构搜索与动态资源分配，与设计智能体异构计算基础设施相关
tldr: 多智能体系统通常手动设计且静态分配资源，难以适配不同难度和领域的查询。本文提出MaAS，通过优化代理超网络（agentic supernet）自动搜索架构，实现根据查询动态分配推理资源。实验证明该方法在多个任务上提升效率，为智能体系统的异构计算基础设施设计提供了自动化方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-imcyvlzpxh/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1733, \"height\": 562, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-imcyvlzpxh/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1741, \"height\": 632, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-imcyvlzpxh/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 833, \"height\": 407, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-imcyvlzpxh/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 856, \"height\": 869, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-imcyvlzpxh/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 838, \"height\": 1078, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-imcyvlzpxh/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1739, \"height\": 556, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-imcyvlzpxh/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 858, \"height\": 317, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-imcyvlzpxh/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1432, \"height\": 1256, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-imcyvlzpxh/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 674, \"height\": 561, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-imcyvlzpxh/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1772, \"height\": 1066, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-imcyvlzpxh/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 680, \"height\": 565, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-imcyvlzpxh/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1766, \"height\": 796, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-imcyvlzpxh/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 864, \"height\": 509, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-imcyvlzpxh/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1764, \"height\": 437, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-imcyvlzpxh/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 861, \"height\": 350, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-imcyvlzpxh/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1818, \"height\": 979, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-imcyvlzpxh/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 969, \"height\": 405, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-imcyvlzpxh/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1207, \"height\": 479, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-imcyvlzpxh/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1205, \"height\": 233, \"label\": \"Table\"}]"
motivation: 多智能体系统的手动设计繁琐，且静态架构无法灵活分配推理资源。
method: 引入代理超网络，学习架构的概率分布，并自动根据查询分配资源。
result: MaAS在多种基准上优于静态方法，显著降低部署开销。
conclusion: MaAS实现了智能体系统的自动化设计，有助于异构环境下资源的高效利用。
---

## Abstract
Large Language Model (LLM)-empowered multi-agent systems extend the cognitive boundaries of individual agents through disciplined collaboration and interaction, while constructing these systems often requires labor-intensive manual designs. Despite the availability of methods to automate the design of agentic workflows, they typically seek to identify a static, complex, one-size-fits-all system, which, however, fails to dynamically allocate inference resources based on the difficulty and domain of each query. To address this challenge, we shift away from the pursuit of a monolithic agentic system, instead optimizing the \textbf{agentic supernet}, a probabilistic and continuous distribution of agentic architectures. We introduce \textbf{MaAS}, an automated framework that samples query-dependent agentic systems from the supernet, delivering high-quality solutions and tailored resource allocation (\textit{e.g.}, LLM calls, tool calls, token cost). Comprehensive evaluation across six benchmarks demonstrates that MaAS \textbf{(I)} requires only $6\\sim45\\%$ of the inference costs of existing handcrafted or automated multi-agent systems, \textbf{(II)} surpasses them by $0.54\\%\sim11.82\\%$, and \textbf{(III)} enjoys superior cross-dataset and cross-LLM-backbone transferability.

---

## 论文详细总结（自动生成）

# 论文总结：Multi-agent Architecture Search via Agentic Supernet

## 1. 核心问题与整体含义（研究动机与背景）

现有基于大语言模型的多智能体系统（MAS）通常需手工设计，或通过自动化方法搜索一个**静态、固定**的复杂工作流。这类方法无法根据查询的**难度、领域和特性**动态调整推理资源——例如简单算术和复杂数论问题使用相同复杂的多智能体架构，导致资源浪费或性能不足。本文提出**MaAS（Multi-agent Architecture Search）**，将自动化设计范式从“寻找单一最优系统”转变为**优化一个概率连续分布**（称为**代理超网络，agentic supernet**），从而为每个查询自适应采样合适的架构，实现高精度与低成本的平衡。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
构建一个包含多个层（L层）的超网络，每层定义若干**智能体算子**（agentic operator，如 CoT、Debate、ReAct 等）及其出现的概率（受前层和输入查询条件）。训练时通过控制器网络和文本梯度联合优化分布参数和算子结构；推理时根据查询动态采样子图并执行。

### 关键技术细节
- **智能体算子定义**：每个算子 \(O = \{M_i\}_{i=1}^m, P, \{T_i\}_{i=1}^n\)，包含LLM实例、提示、工具等。
- **代理超网络**：\(A = \{\pi, O\}\)，\(\pi_\ell(O) = p(O|A_{1:\ell-1})\)，联合分布 \(p(G) = \prod_\ell \prod_{O\in O} \pi_\ell(O)^{I_{O\in V_\ell}}\)。
- **查询依赖采样**：使用**Mixture-of-Experts（MoE）风格网络**控制器 \(Q_\phi\)，按累积得分阈值激活算子，支持**早期退出（early-exit）算子 \(O_{\text{exit}}\)** 自适应深度。
- **优化目标**：\(\min_{\pi, O} \mathbb{E}_{(q,a)\sim D, \, G\sim Q_\phi}[-p(a|q,\pi,O) + \lambda \cdot C(G;q)]\)，其中 \(C\) 为token成本。
- **梯度估计**：
  - 分布 \(\pi\) 的梯度通过**经验贝叶斯蒙特卡洛**近似（式11），用成本感知重要性权重。
  - 算子 \(O\) 的梯度通过**文本梯度**（textual gradient）估计，即让LLM自动生成对提示、温度、节点结构的改进建议（式12）。

### 算法流程（文字描述）
1. 对训练集中每个查询 \(q\)：
   - 逐层使用控制器采样算子（若遇 early-exit 则提前停止），生成架构 \(G\)。
   - 执行 \(G\) 得到答案，接收环境反馈。
   - 计算分布损失（蒙特卡洛）和算子文本梯度。
   - 联合更新分布参数和算子。
2. 推理时，对每个新查询，同样采样并执行自适应架构。

## 3. 实验设计

### 数据集与场景
- **数学推理**：GSM8K、MATH（子集617题）、MultiArith、SVAMP（文中未列出但提及）。
- **代码生成**：HumanEval、MBPP。
- **工具使用**：GAIA（多领域，含网页浏览、文件读取等）。
- 每个数据集按 1:4 划分为训练/测试集。

### 基线方法
- **单智能体**：Vanilla、CoT、ComplexCoT、Self-Consistency。
- **手工多智能体**：MultiPersona、LLM-Debate、LLM-Blender、DyLAN、AgentVerse、MacNet。
- **自动化多智能体**：AutoAgents、GPTSwarm、ADAS、AgentSquare、AFlow。

### 评价指标
- 准确率 / Pass@1（代码）
- 推理成本（token数、API费用、时间）

## 4. 资源与算力

文中**未明确说明使用的GPU型号、数量或训练时长**。所有LLM通过API调用：
- 主力模型：`gpt-4o-mini-0718`（闭源），辅以 `Qwen-2.5-72b-instruct` 和 `llama-3.1-70b` 进行迁移实验。
- 训练成本示例（MATH基准）：
  - MaAS：训练总token 5.4M，费用 **3.38$**，耗时 **53分钟**。
  - 对比方法 AFlow：训练费用 22.50$，耗时 184分钟。
- 推理成本示例（MATH）：MaAS 0.42$，AFlow 1.66$，LLM-Debate 6.76$。

## 5. 实验数量与充分性

- **主要性能对比**（表1、表2）：在6个基准上与14种基线对比，MaAS平均领先0.54%～16.89%。
- **成本分析**（表3、图4）：详细对比训练/推理的token、费用、时间。
- **案例可视化**（图5、6）：展示针对不同难度查询的算子采样概率分布和生成的工作流。
- **参数敏感性**（图7）：分析层数 \(L\)、成本系数 \(\lambda\)、采样次数 \(K\)。
- **消融实验**（表4）：移除文本梯度、early-exit、成本约束，分别考察影响。
- **迁移性**（表7、8）：跨LLM骨干（从gpt-4o-mini到Qwen/Llama）和跨数据集（如MATH→GSM8K）验证。
- **归纳分析**（图8-10）：将未见过的 Debate 算子加入推理池，观察MaAS是否能合理调用。

**充分性评价**：实验覆盖多个领域（数学、代码、工具使用），对比基线全面（含手工与自动化），消融和迁移分析完整，但缺乏大规模真实世界任务验证。结论基于公开基准，客观公平。

## 6. 主要结论与发现

1. **高性能**：MaAS在数学推理、代码生成、工具使用基准上平均超越现有最佳方法 **0.54%～16.89%**。
2. **资源高效**：推理成本仅为对比方法的 **6%～45%**（如MATH上推理费用0.42$ vs AFlow 1.66$）。
3. **自适应分配**：代理超网络能学习根据查询难度动态选择架构深度和算子组合（简单查询早退出，复杂查询深入）。
4. **强迁移性**：跨数据集和跨LLM骨干无需重新训练即可保持性能提升。
5. **归纳能力**：对训练时未见的算子（Debate）仍能合理采样使用。

## 7. 优点

- **范式创新**：首次将多智能体系统设计从“搜索单一最优解”推广到“优化连续概率分布”，更符合实际动态需求。
- **联合优化**：同时优化架构分布和算子细节（提示、温度、结构），实现端到端自动化进化。
- **实用性强**：成本感知训练，推理时按需分配资源，显著降低部署开销。
- **实验严谨**：多维度对比、消融、迁移、归纳分析，证明方法鲁棒性。

## 8. 不足与局限

- **算子集合依赖专家预定义**：目前算子（如CoT、Debate等）需人工设计，未实现算子级别的完全自动发现。
- **未在大规模生产环境验证**：仅在学术基准上测试，真实复杂任务（如多轮交互、长上下文）效果未知。
- **成本分析受API定价影响**：文中费用基于特定时间点价格，可能不具长期通用性。
- **缺乏对异构LLM backbone的深入鲁棒性分析**：仅测试了三种开源/闭源模型，未探讨弱模型或不同系列模型下的退化风险。
- **未讨论失败案例或错误模式**：如采样到不合适架构时如何处理，缺乏消融中early-exit精度下降的具体原因分析。

（完）
