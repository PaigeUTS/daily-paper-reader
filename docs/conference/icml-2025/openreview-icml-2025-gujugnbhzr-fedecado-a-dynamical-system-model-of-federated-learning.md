---
title: "FedECADO: A Dynamical System Model of Federated Learning"
title_zh: FedECADO：联邦学习的动力系统模型
authors: "Aayushya Agarwal, Gauri Joshi, Lawrence Pileggi"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=gujuGnbhZr"
tags: ["query:agents-os"]
score: 7.0
evidence: 通过多速率积分方法处理异构计算
tldr: 针对联邦学习中异构计算和非独立同分布数据问题，提出FedECADO算法，基于动力系统建模，采用多速率积分和自适应步长选择同步客户端更新。该方法有效应对客户端计算异构性，提升模型性能。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-gujugnbhzr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 662, \"height\": 760, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gujugnbhzr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 582, \"height\": 261, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gujugnbhzr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 838, \"height\": 262, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gujugnbhzr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1713, \"height\": 613, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-gujugnbhzr/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1708, \"height\": 615, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-gujugnbhzr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 825, \"height\": 364, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gujugnbhzr/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1580, \"height\": 114, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gujugnbhzr/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1582, \"height\": 113, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gujugnbhzr/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1599, \"height\": 114, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gujugnbhzr/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1339, \"height\": 156, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gujugnbhzr/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1332, \"height\": 112, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gujugnbhzr/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1342, \"height\": 156, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-gujugnbhzr/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 750, \"height\": 112, \"label\": \"Table\"}]"
motivation: 联邦学习中异构数据分布和计算负载导致模型更新不一致，限制性能。
method: 提出FedECADO，基于动力系统表示，设计多速率积分方法自适应同步客户端更新。
result: FedECADO在异构计算场景下优于现有方法，提升模型收敛速度和精度。
conclusion: 动力系统方法可有效处理联邦学习中的异构计算挑战。
---

## Abstract
Federated learning harnesses the power of distributed optimization to train a unified machine learning model across separate clients. However, heterogeneous data distributions and computational workloads can lead to inconsistent updates and limit model performance. This work tackles these challenges by proposing FedECADO, a new algorithm inspired by a dynamical system representation of the federated learning process. FedECADO addresses non-IID data distribution through an aggregate sensitivity model that reflects the amount of data processed by each client. To tackle heterogeneous computing, we design a multi-rate integration method with adaptive step-size selections that synchronizes active client updates in continuous time. Compared to prominent techniques, including FedProx, FedExp, and FedNova, FedECADO achieves higher classification accuracies in numerous heterogeneous scenarios.

---

## 论文详细总结（自动生成）

# FedECADO: 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：联邦学习（FL）中，客户端之间的**数据异构（non-IID）** 和**计算能力异构**导致全局模型更新不一致，严重影响模型性能。传统方法（如FedAvg、FedProx）通常假设客户端同质，无法有效处理这些异质性。
- **整体含义**：该论文提出将联邦学习建模为**连续时间动力系统**（ODE），并借鉴**电路仿真**（ECADO）中的多速率积分和灵敏度分析方法，设计新算法FedECADO，旨在同步异构客户端更新并加速收敛，提升非IID场景下的模型精度。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
### 2.1 核心思想
- 将联邦学习的梯度下降过程视为**连续时间梯度流**（continuous-time gradient flow）ODE：$$\dot{x}(t) = -\sum_i p_i \nabla f_i(x(t))$$
- 引入**等效电路模型**（EC模型）：将全局模型状态 \(x_c\) 与客户端状态 \(x_i\) 通过“电感”耦合，形成二阶动力系统，加速收敛。
- 关键创新：**聚合灵敏度模型**（Aggregate Sensitivity Model）处理非IID数据；**多速率积分**（Multi-rate Integration）同步异构客户端计算。

### 2.2 关键技术细节
- **聚合灵敏度模型**：  
  针对非IID数据分布，在客户端本地ODE中引入**数据比例因子** \(p_i = |D_i|/|D|\)，并定义一阶灵敏度 \(G_i^{th} = \frac{1}{\Delta t} + p_i \nabla^2 f_i\)（用常数Hessian近似 \(\bar{H}_i\) 简化计算）。该灵敏度反映了客户端数据量对聚合更新的影响，在中央服务器更新时作为线性近似，改善Gauss-Seidel迭代的收敛性。
- **多速率积分与自适应步长**：  
  - 各客户端因计算能力不同，本地模拟时间窗口 \(T_i = \sum_k \Delta t_{ki}\) 各异（\(\Delta t_{ki}\) 为学习率，\(e_i\) 为本地epoch数），导致异步到达。  
  - 提出**线性插值/外推算子** \(\Gamma(x_i(t), \tau)\)，将各客户端最后状态同步到同一时间点 \(\tau\)，构造连续时间窗 \([t_0, t_0 + \max(T_i)]\) 上的统一ODE。  
  - 中央服务器使用**后向欧拉（BE）积分**求解更新（公式(33)），并基于**局部截断误差（LTE）** 自适应选择BE步长 \(\Delta t\)，保证数值精度（Algorithm 1）。  
  - 证明该多速率更新是一个**收缩映射**（Theorem 4.1），确保收敛到平稳点。

### 2.3 算法流程（Algorithm 2 简化文字描述）
1. 初始化全局状态 \(x_c\)、本地状态 \(x_i\)、流向量 \(I_{iL}=0\)。  
2. 预计算每个客户端的常数灵敏度模型 \(\bar{G}_i^{th}\)。  
3. 每轮通信：  
   - 活跃客户端并行运行本地ODE（Forward Euler），模拟 \(e_i\) 个epoch，得到最终状态 \(x_i(t+T_i)\) 和模拟时长 \(T_i\)。  
   - 中央服务器在时间窗 \([t, t+\max(T_i)]\) 上：  
     - 根据LTE自适应选择BE步长 \(\Delta t\)。  
     - 对每个时间点 \(\tau\)，用线性算子 \(\Gamma\) 估算客户端状态。  
     - 求解线性方程组（公式(33)）更新中央状态 \(x_c\) 和流向量 \(I_{iL}\)。  
4. 返回 \(x_c\)。

## 3. 实验设计
### 3.1 数据集与场景
- **非IID场景（表1）**：CIFAR-10，100个客户端，Dirichlet分布（Dir(0.1)），活跃率0.1。  
- **异步计算场景（表2）**：CIFAR-10，IID分布，每个客户端学习率 \(lr_i \sim U[10^{-4},10^{-3}]\)，epoch数 \(e_i \sim U[1,10]\)。  
- **两者结合（表3、4、5）**：  
  - ResNet-34 / CIFAR-100（表3），100客户端，Dirichlet分布 + 随机学习率。  
  - ResNet-18 / TinyImageNet（表4），60 epochs。  
  - LSTM / Sentiment140（表5），10客户端，10 epochs。  
- **缩放实验**：附录D中增加了更多数据集和模型，验证可扩展性。

### 3.2 Benchmark与对比方法
- 对比方法：FedProx、FedNova、FedExp、FedDecorr、FedRS。  
- 对比ECADO原始版本（附录F）。  
- 所有实验重复20次（表1-3给出均值和标准差）。

### 3.3 运行时间分析（表6）
- 报告归一化每epoch运行时间：FedECADO约1.06（略慢1-2%），与FedNova、FedProx相当。

## 4. 资源与算力
- **未明确说明**使用的GPU型号、数量或训练时长。论文仅提及“运行时与baselines相当”，未提供具体硬件配置或训练时间细节。

## 5. 实验数量与充分性
- **数量**：共7个表格（Table 1-7）和多个附图，覆盖四个数据集（CIFAR-10、CIFAR-100、TinyImageNet、Sentiment140），三种模型（VGG-11、ResNet-18/34、LSTM），三种异构场景。  
- **充分性**：实验设计**较为充分**：单独验证了非IID和异步计算的效果，再验证两者结合；多次随机重复报告均值和标准差，保证了统计显著性；对比了主流方法；附录还提供了运行时对比和与ECADO的消融。  
- **客观性与公平性**：对比方法均使用公开实现，超参数设置未详细列出但可能保持公平；唯一不足是未对比最新方法如SCAFFOLD、FedADAM等，且未提供完整消融实验（如移除灵敏度模型或多速率积分的性能下降）。

## 6. 论文的主要结论与发现
- FedECADO在**非IID数据分布**和**异步计算**两种异构场景下，均比现有方法获得更高的分类准确率（例如非IID场景下比FedNova高7%，比FedProx高13%）。  
- 在**两者同时存在**的复杂场景下（表3-5），FedECADO仍显著领先（CIFAR-100上比FedNova高约11.8%）。  
- 多速率积分和自适应步长有效同步了异构客户端，且不影响收敛性（证明为收缩映射）。  
- 运行时仅略慢约1-2%，计算开销可接受。

## 7. 优点
- **方法论创新**：将电路仿真中的**多速率积分**和**灵敏度分析**引入联邦学习，为处理异质性提供了全新视角。  
- **理论保证**：证明多速率更新为收缩映射，保证收敛；自适应步长基于局部截断误差，具有数值稳定性。  
- **实验全面**：覆盖多种数据集、模型和异构类型，多次重复确保鲁棒性。  
- **实用性**：通信开销低（只多传输模拟时间 \(T_i\)），服务器端BE矩阵因活跃客户端数小而可预LU分解，实现高效。

## 8. 不足与局限
- **实验覆盖**：未在更大规模（如1000+客户端）或更复杂模型（如Transformer）上测试；未与SCAFFOLD、FedDANE等最新方法对比。  
- **偏差风险**：常数Hessian近似假设所有客户端Hessian变化缓慢，在深度非凸任务中可能不准确。  
- **应用限制**：仅关注图像分类和文本情感分析任务，未验证在回归、强化学习等场景的有效性。  
- **算力信息缺失**：未报告GPU型号、数量、训练时间，影响复现和效率评估。  
- **理论局限**：收缩映射证明依赖于线性插值/外推和局部Lipschitz假设，未严格处理非凸全局收敛性（仅收敛到平稳点）。

（完）
