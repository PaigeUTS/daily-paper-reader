---
title: Heterogeneous Graph Transformers for Simultaneous Mobile Multi-Robot Task Allocation and Scheduling under Temporal Constraints
title_zh: 异构图Transformer：面向时间约束下移动多机器人同步任务分配与调度
authors: "Batuhan Altundas, Shengkang Chen, Shivika Singh, Shivangi Deo, Minwoo Cho, Matthew Craig Gombolay"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=k1fbdnwjCH"
tags: ["query:agents-os"]
score: 4.0
evidence: 异构多机器人任务分配与调度，类比智能体编排
tldr: 针对大规模异构多机器人任务分配与调度问题，提出基于残差异构图Transformer的同步决策模型，编码智能体能力、旅行时间与时序约束，实现可扩展的高效协调，其核心思想可迁移至异构计算基础设施中的智能体资源调度。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-k1fbdnwjch/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1386, \"height\": 447, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-k1fbdnwjch/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 483, \"height\": 438, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-k1fbdnwjch/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 805, \"height\": 469, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-k1fbdnwjch/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1412, \"height\": 539, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-k1fbdnwjch/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1413, \"height\": 531, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-k1fbdnwjch/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1410, \"height\": 620, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-k1fbdnwjch/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1394, \"height\": 433, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-k1fbdnwjch/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1375, \"height\": 676, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-k1fbdnwjch/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 733, \"height\": 759, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-k1fbdnwjch/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1451, \"height\": 550, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-k1fbdnwjch/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1449, \"height\": 547, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-k1fbdnwjch/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1446, \"height\": 524, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-k1fbdnwjch/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1443, \"height\": 362, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-k1fbdnwjch/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1357, \"height\": 1931, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-k1fbdnwjch/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1445, \"height\": 961, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-k1fbdnwjch/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 924, \"height\": 2361, \"label\": \"Table\"}]"
motivation: 现有方法难以扩展且忽视智能体异构性。
method: 构建残差异构图Transformer，结合边与节点注意力。
result: 模型在复杂任务场景下实现可扩展的最优调度。
conclusion: 图Transformer有效解决异构多智能体调度问题。
---

## Abstract
Coordinating large teams of heterogeneous mobile agents to perform complex tasks efficiently has scalability bottlenecks in feasible and optimal task scheduling, with critical applications in logistics, manufacturing, and disaster response. Existing task allocation and scheduling methods, including heuristics and optimization-based solvers, often fail to scale and overlook inter-task dependencies and agent heterogeneity. We propose a novel Simultaneous Decision-Making model for Heterogeneous Multi-Agent Task Allocation and Scheduling (HM-MATAS), built on a Residual Heterogeneous Graph Transformer with edge and node-level attention. Our model encodes agent capabilities, travel times, and temporospatial constraints into a rich graph representation and is trainable via reinforcement learning. Trained on small-scale problems (10 agents, 20 tasks), our model generalizes effectively to significantly larger scenarios (up to 40 agents and 200 tasks), enabling fast, one-shot task assignment and scheduling. Our simultaneous model outperforms classical heuristics by assigning 164.10\% more feasible tasks given temporal constraints in 3.83\% of the time, metaheuristics by 201.54\% in 0.01\% of the time and exact solver by 231.73\% in 0.03\% of the time, while achieving $20\times$-to-$250\times$ speedup from prior graph-based methods across scales.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：大规模异构移动多机器人团队在时间约束下的任务分配与调度（HM-MATAS）面临**可扩展性瓶颈**。现有方法（启发式、精确求解器、元启发式）要么无法处理任务间依赖和智能体异构性，要么随问题规模增加计算成本爆炸。
- **意义**：该问题在物流、制造、灾难响应等领域具有关键应用。需要一种既能**同时决策分配与调度**、又能**编码异构性与时空约束**，且**可在小规模训练后直接泛化到大规模**的学习模型。
- **现状不足**：精确求解器（MILP）虽能保证最优但在中等规模即失效；图神经网络方法（如HetGAT）受限于消息聚合方式，无法有效建模异构动态关系；顺序决策模型计算复杂度高（O(|A||T|³)）。

## 2. 方法论：核心思想、关键技术细节
- **核心思想**：提出**TARGETNET**（Task-Agent Relational Graph Encoding for Team-based Navigation and Execution of Tasks），将HM-MATAS建模为**异构图**，使用**残差异构图Transformer（Residual Heterogeneous Graph Transformer）** 进行**一步式（one-shot）同步分配与调度**。
- **关键技术细节**：
  - **图表示**：包含Agent节点、Task节点、Assignment节点（每对agent-task）、State节点和Task Order节点；边编码旅行时间、执行时间、顺序约束和等待时间。
  - **边注意力机制**：在标准HGT基础上增加**边级别的注意力与消息传递**，使模型能同时利用节点特征和边特征更新目标节点与边，学习选择性忽略某些组件（通过移除softmax实现）。
  - **残差连接**：采用图原始残差（graph-raw residual），将初始输入特征追加到每一层，缓解深层GNN中的梯度消失。
  - **同步决策**：单次前向传播同时输出任务分配和排序，无需迭代环境交互。
  - **训练算法**：使用**REINFORCE**，奖励结合密集的可行性信号（每步+1/-1）和稀疏的最终优化奖励（归一化最小化makespan与可行任务数）。
- **公式与算法**（文字描述）：
  - 节点更新：聚合来自邻居节点的注意力加权消息和来自边特征的注意力加权消息，见原式(2)。
  - 边更新：独立使用边注意力加权消息，见原式(3)。
  - 多头部边缘消息：M_iE(e) = W_iME * h^{l-1}_e，组合后通过可权重矩阵投影。
  - 边缘注意力：使用边缘键K_iE和节点查询Q_iE计算，不应用softmax以允许零权重。
  - 整体梯度：∇θJ(θ) = E[ Σ_t (折扣累计回报) * (log分配概率 + log调度概率) ]，见原式(6)。

## 3. 实验设计
- **数据集/场景**：合成数据，包含四种规模（见表1）：
  - 小规模：10 agent, 20 task
  - 中规模：10 agent, 50 task
  - 大规模：20 agent, 100 task
  - 超大规模：40 agent, 200 task
  
  障碍物地图使用RRT*预计算旅行时间；时间窗口、等待约束按比例生成，并通过MILP验证可行性。大规模和超大规模由多个中规模子问题组合而成。

- **Benchmark与对比方法**：
  - **精确求解器**：Gurobi MILP（时间上限12小时）
  - **启发式**：Earliest Deadline First (EDF)、Constraint-Aware EDF (CA-EDF)
  - **元启发式**：遗传算法（Gen-Random, Gen-EDF，1代和3代变异，种群100）
  - **图神经网络基线（顺序决策）**：HetGAT、Res-HetGAT、Seq-TARGETNET及其多种消融变体（去残差/去边特征）
  - **本文模型（同步决策）**：TARGETNET及其消融变体（TARGETNET\R、\E、\ER）
- **评估指标**：最优性率（相对于MILP）、可行任务百分比、训练速度、推理速度（秒）。

## 4. 资源与算力
- 文中明确说明：小规模至大规模实验在**Mac Studio（Apple M1芯片，32GB RAM）** 上运行；超大规模实验在**AMD EPYC 7452处理器（Ubuntu 20.04.6）** 的高性能服务器上运行。
- **未提及GPU型号或数量**，也无具体训练时长统计，仅报告了训练速度（每episode时间）和推理时间。因此**算力资源相对基础，主要依赖CPU**。

## 5. 实验数量与充分性
- **训练集**：200个小规模问题（10/20），每个模型使用3个不同随机种子初始化并并行训练，最终报告**最佳种子**的性能。
- **测试集**：每种规模分别200/200/30/10个问题（小到超大），保证了统计显著性。
- **实验组数**：包含主对比实验、消融实验（残差、边特征）、敏感性分析（时间窗口松紧、等待约束比例、机器人速度快慢）。
- **公平性**：所有可比方法使用相同图表示和训练设置；学习模型均在相同小规模数据上训练后直接测试所有规模；性能统计带标准差；种子敏感性单独报告以防止偶然性。
- **充分性**：实验设计较为全面，覆盖了多种约束变化和规模外推，消融验证了各组件贡献，对比了精确、启发、元启发、GNN基线。

## 6. 主要结论与发现
- **性能超越**：TARGETNET在全部规模上优于所有非精确基线，在小规模上相比HetGAT可行任务分配提升36.35%，相比CA-EDF提升13.27%；在超大规模上比MILP（12小时部分解）可行任务多231.73%，比HetGAT多47.05%。
- **计算效率**：推理速度比顺序GNN方法快**20–250倍**，在超大规模上仅需约8秒，而顺序方法需要数千秒。比启发式快3.9–26.18倍。
- **泛化能力**：训练于10 agent/20 task，可直接泛化到40 agent/200 task，无需重新训练。
- **消融分析**：同时使用边特征和残差连接对性能提升和稳定性至关重要；去除边特征后性能下降16.91%–34.75%。

## 7. 优点
- **方法创新**：首次将**同步决策（one-shot）** 与**异构图Transformer + 边注意力**结合用于大规模HM-MATAS，避免了顺序决策的累积计算。
- **强泛化性**：小规模训练即可外推至大规模，展示了图神经网络在组合优化中的归纳能力。
- **速度与质量的平衡**：在保证高质量调度（接近最优）的同时实现毫秒/秒级推理，适合实时部署。
- **消融与敏感性实验充分**：清晰证明了各组件贡献，并在约束变化下保持鲁棒性。

## 8. 不足与局限
- **环境假设静态**：预计算运动规划未考虑动态障碍或智能体间碰撞避免，实际部署可能偏离预期旅行时间。
- **可解释性差**：图模型和注意力机制难以被人类验证，在安全关键系统中缺乏透明性。
- **依赖问题验证**：训练数据生成需借助MILP验证可行性，限制了完全无监督训练的可能。
- **种子敏感性**：虽然TARGETNET比其他模型更鲁棒，但不同随机种子仍会导致性能差异，需多种子择优。
- **忽略agent-agent交互**：当前模型仅考虑agent-task和task-task关系，未对多机器人路径冲突进行建模。

（完）
