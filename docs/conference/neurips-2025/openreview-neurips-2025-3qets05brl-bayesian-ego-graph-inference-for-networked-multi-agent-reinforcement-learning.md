---
title: Bayesian Ego-graph Inference for Networked Multi-Agent Reinforcement Learning
title_zh: 面向网络化多智能体强化学习的贝叶斯自我图推断
authors: "Wei Duan, Jie Lu, Junyu Xuan"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=3qeTs05bRL"
tags: ["query:agents-os"]
score: 6.0
evidence: 面向异构多智能体环境的去中心化图策略
tldr: 现有网络化多智能体强化学习假设静态邻域，无法适应动态异构环境。本文提出随机图策略，每个智能体基于局部物理邻域采样子图进行决策，并引入去中心化演员-评论家框架学习动态图。该方法提升了在异构环境中的适应性，与智能体基础设施设计相关。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-3qets05brl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1425, \"height\": 409, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3qets05brl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1431, \"height\": 754, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3qets05brl/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1424, \"height\": 385, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3qets05brl/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1445, \"height\": 356, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3qets05brl/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1359, \"height\": 483, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3qets05brl/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1449, \"height\": 624, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3qets05brl/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1447, \"height\": 803, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3qets05brl/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1443, \"height\": 808, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3qets05brl/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1441, \"height\": 804, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3qets05brl/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1406, \"height\": 1662, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-3qets05brl/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1455, \"height\": 2043, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-3qets05brl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1044, \"height\": 216, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-3qets05brl/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1455, \"height\": 1095, \"label\": \"Table\"}]"
motivation: 静态邻域假设限制了多智能体在异构环境中的适应性。
method: 提出基于随机图的去中心化策略，结合贝叶斯推断学习动态子图。
result: 在动态异构环境中提升了协作性能。
conclusion: 动态图推断是去中心化多智能体系统的有效方法。
---

## Abstract
In networked multi-agent reinforcement learning (Networked-MARL), decentralized agents must act autonomously under local observability and constrained communication over fixed physical graphs. Existing methods often assume static neighborhoods, limiting adaptability to dynamic or heterogeneous environments. While centralized frameworks can learn dynamic graphs, their reliance on global state access and centralized infrastructure is impractical in real-world decentralized systems. We propose a stochastic graph-based policy for Networked-MARL, where each agent conditions its decision on a sampled subgraph over its local physical neighborhood. Building on this formulation, we introduce \textbf{BayesG}, a decentralized actor–critic framework that learns sparse, context-aware interaction structures via Bayesian variational inference. Each agent operates over an ego-graph and samples a latent communication mask to guide message passing and policy computation. The variational distribution is trained end-to-end alongside the policy using an evidence lower bound (ELBO) objective, enabling agents to jointly learn both interaction topology and decision-making strategies.
BayesG outperforms strong MARL baselines on large-scale traffic control tasks with up to 167 agents, demonstrating superior scalability, efficiency, and performance.

---

## 论文详细总结（自动生成）

# 面向网络化多智能体强化学习的贝叶斯自我图推断（BayesG）——详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：在网络化多智能体强化学习（Networked-MARL）中，智能体在固定物理通信图上只能局部观测并与邻居交互。现有方法通常假设静态邻域（即固定通信结构），无法适应动态或异构环境（如交通拥堵随时间变化）。虽然集中式训练方法可以学习动态图，但它们依赖全局状态和集中式基础设施，在真实去中心化系统中不实用。
- **研究动机**：能否让去中心化智能体仅在局部观测和任务反馈下，动态自适应地调整其交互结构？
- **整体含义**：作者提出一个去中心化的演员-评论家框架 **BayesG**，通过贝叶斯变分推断学习稀疏、上下文感知的交互图，使每个智能体在其自我图（ego-graph）上采样潜在通信掩码，从而高效协调并适应动态环境。该工作旨在解决网络化MARL中静态通信的效率瓶颈。

## 2. 论文提出的方法论

### 2.1 核心思想
- 每个智能体定义关于其物理邻域的**随机图策略**（graph-based policy）：先从一个学习到的分布中采样一个二元子图，再基于该子图编码的观测选择动作。
- 将学习交互结构视为**贝叶斯变分推断**问题：每个智能体维护一个二元掩码 \( Z_i \)（指示与哪些邻居通信）的变分后验分布 \( q(Z_i; \phi_i) \)，该分布通过ELBO目标与策略联合优化。

### 2.2 关键技术细节

1. **图策略定义**（Definition 3）：
   \[
   \pi_i(u_i, G_{V_i} | s_{V_i}; \theta_i, \phi_i) = \rho(G_{V_i} | s_{V_i}; \phi_i) \cdot \tilde{\pi}_i(u_i | \tilde{f}_i(s_{V_i}, G_{V_i}); \theta_i)
   \]
   - \( G_{V_i} \) 是采样得到的二元邻接矩阵，限于物理图的环境拓扑。
   - \( \tilde{f}_i \) 是基于图的编码器（使用GCN），\( \tilde{\pi}_i \) 是动作选择策略。

2. **变分后验**：
   \[
   q(Z_i; \phi_i) = \prod_{j \in N_i} \mathrm{Bern}(z_{ij}; \sigma(\phi_{ij}))
   \]
   每个 \( z_{ij} \) 表示是否与邻居 \( j \) 通信，通过Gumbel-Softmax重参数化实现可微采样。

3. **ELBO目标**（Definition 5）：
   \[
   \mathcal{L}_{\text{ELBO}} = \mathbb{E}_{q(Z_i;\phi_i)}\left[ -\mathcal{L}_{\theta,\phi} + \sum_{j \in N_i} \big( (\lambda + \sigma(\phi_{ij}))\log\sigma(\phi_{ij}) + (2-\lambda-\sigma(\phi_{ij}))\log(1-\sigma(\phi_{ij})) \big) \right]
   \]
   - \( \mathcal{L}_{\theta,\phi} \) 是图条件下的演员损失（包含策略梯度和熵正则）。
   - 后两项来自先验和熵正则，鼓励稀疏性与探索。

4. **训练流程**：联合优化策略网络（\( \theta_i \)）、值网络（\( \omega_i \)）和变分参数（\( \phi_i \)）。每个智能体独立使用A2C算法，但通过共享ELBO目标实现结构学习。

## 3. 实验设计

### 3.1 场景/数据集
- 使用**SUMO**微观交通模拟器，构建五个自适应交通信号控制（ATSC）基准：
  - **ATSC_Grid**：5×5 合成网格网络（25个路口）。
  - **Monaco**：真实28个路口布局。
  - **NewYork33**、**NewYork51**、**NewYork167**：分别包含33、51、167个真实曼哈顿信号路口（大规模）。
- 每个MDP步骤对应固定控制间隔（5秒或20秒），状态包括车道密度、队列长度、等待时间；动作是信号相位切换；奖励为负的停驶车辆数。

### 3.2 基准方法
- **非通信基线**：IA2C、ConseNet、FPrint、LToS。
- **通信基线**：CommNet、NeurComm。
- 所有方法使用统一A2C骨干网络，保证公平比较。

### 3.3 实现细节
- 策略与评论家网络结构类似，每实验5个随机种子。
- 变分掩码输入使用观测、策略指纹和轨迹特征的GCN编码。

## 4. 资源与算力

- **论文未明确说明**使用的GPU型号、数量或具体训练时长。只在附录中描述了训练步骤数（例如百万级），但未提及硬件配置。因此无法从文中获知具体算力投入。

## 5. 实验数量与充分性

- **主要实验**：在5个场景上对比6个基线（图2训练曲线），每个种子重复5次，展示均值和方差。
- **定性可视化**：网格地图的交通密度对比（图3）。
- **案例研究**：学习到的交互图在特定时间步的解释（图4），展示自适应方向性协调。
- **消融实验**（图5）：
  - 图掩码策略：无掩码、随机掩码、学习掩码（BayesG）。
  - 掩码输入特征：仅状态、仅轨迹、仅策略、三者组合。
- **额外分析**：附录中提供训练损失分解（图7-9）和更多时间点可视化（图10-11）。
- **充分性评估**：实验覆盖了从合成小规模到真实大规模场景，对比了多种通信/非通信方法，消融实验验证了各组件贡献。实验设计较为全面、客观，但未包含与其他图学习方法的直接比较（如DGN、DICG等，因为它们属于CTDE设置，被排除）。

## 6. 论文的主要结论与发现

- **性能优势**：BayesG在所有五个环境中几乎一致优于所有基线，尤其在大型场景（NewYork167）中提升显著，并显示出更快的收敛速度（图2）。
- **自适应交互**：学习到的潜在通信图能够动态优先关注拥堵区域的上游交叉口，实现方向性、任务驱动的协调（图4）。
- **稀疏性有效性**：消融实验表明，学习到的掩码显著优于随机掩码和无掩码（图5左），且结合多种输入特征（状态+轨迹+策略）效果最佳（图5右）。
- **稳定性和可解释性**：训练损失（附录E）显示联合优化过程稳定，学习到的图具有明确物理含义。

## 7. 优点

- **新颖的贝叶斯变分框架**：在去中心化且受物理拓扑约束的环境下，同时学习策略和图结构，并能表达不确定性。
- **端到端优化**：通过ELBO目标将图推理嵌入到A2C训练中，无需两阶段或外部图学习器。
- **可伸缩性**：在多达167个智能体的真实交通网络上取得SOTA，验证了大规模适用性。
- **可解释性**：学习到的边缘概率能直观反映智能体间的协调模式，便于理解行为。
- **公平基线**：所有基线使用统一骨干，通信方法均遵守物理拓扑，确保对比公平。

## 8. 不足与局限

- **固定物理拓扑假设**：本方法假设环境图是静态且已知的，对于图结构动态变化的场景（如自组网）可能不适用。
- **局部可观测性限制**：每个智能体仅基于自我图内的局部数据推断掩码，无法直接捕捉长距离依赖。
- **超参数敏感**：Gumbel-softmax温度及稀疏先验 \( \lambda \) 会影响图学习质量，需仔细调参。
- **计算开销**：相比非通信方法，变分采样和GCN编码增加了训练成本（但文中未量化评估）。
- **实验覆盖广度**：仅在交通控制领域验证，未在更通用的MARL测试床（如SMAC、MPE）中测试，限制了泛化性。
- **缺乏与CTDE图方法的直接对比**：虽然因设置不同而排除，但仍需讨论在哪些条件下性能会低于那些方法。

（完）
