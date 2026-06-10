---
title: Approximate Gradient Coding for Distributed Learning with Heterogeneous Stragglers
title_zh: 面向异构延迟节点的分布式学习近似梯度编码
authors: "Heekang Song, Wan Choi"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=QlDyoo8qLY"
tags: ["query:agents-os"]
score: 6.0
evidence: 分布式学习中针对异构延迟节点的梯度编码
tldr: 现有梯度编码方法假设同构延迟模型，在真实异构系统中性能有限。本文提出优化梯度编码方案，显式考虑个体延迟概率，通过拉格朗日对偶得到最优编码系数，并设计数据分配策略减少冗余。该方法提升了异构计算资源下的分布式训练效率，与服务器异构计算需求相关。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-qldyoo8qly/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 864, \"height\": 371, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qldyoo8qly/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1136, \"height\": 463, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qldyoo8qly/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1102, \"height\": 962, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qldyoo8qly/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1099, \"height\": 475, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qldyoo8qly/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1193, \"height\": 898, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qldyoo8qly/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1102, \"height\": 482, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-qldyoo8qly/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 520, \"height\": 419, \"label\": \"Figure\"}]"
motivation: 现有梯度编码方法无法有效处理异构延迟节点。
method: 提出考虑个体延迟概率的优化梯度编码方案，推导闭式最优解。
result: 减少了冗余和计算负载，提升了异构环境中的训练效率。
conclusion: 所提方案有效提升了异构分布式学习的鲁棒性。
---

## Abstract
In this paper, we propose an optimally structured gradient coding scheme to mitigate the straggler problem in distributed learning. Conventional gradient coding methods often assume homogeneous straggler models or rely on excessive data replication, limiting performance in real-world heterogeneous systems. To address these limitations, we formulate an optimization problem minimizing residual error while ensuring unbiased gradient estimation by explicitly considering individual straggler probabilities. We derive closed-form solutions for optimal encoding and decoding coefficients via Lagrangian duality and convex optimization, and propose data allocation strategies that reduce both redundancy and computational load. We also analyze convergence behavior for $\lambda$-strongly convex and $\mu$-smooth loss functions. Numerical results show that our approach significantly reduces the impact of stragglers and accelerates convergence compared to existing methods.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：在分布式学习中，**异构延迟节点（heterogeneous stragglers）** 严重拖慢训练速度。现有梯度编码（Gradient Coding）方法要么假设所有工作节点具有相同的延迟概率（同构模型），要么依赖过高的数据复制，导致在真实异构系统中性能退化。
- **整体含义**：本文提出一种**针对异构延迟环境的近似梯度编码方案**，显式考虑每个工作节点不同的延迟概率，通过优化编码/解码系数最小化残差误差，同时保证梯度估计无偏，从而在低计算负载下显著提升分布训练效率。

### 2. 论文提出的方法论

#### 核心思想
- 将编码矩阵 **A** 和解码向量 **w** 的设计建模为优化问题：在**无偏梯度估计**的约束下，最小化残差误差的期望 $E_t[\|g(t) - \hat{g}(t)\|_2^2]$，其中每个工作节点 $i$ 独立的延迟概率 $p_i$。
- 利用梯度有界假设 $\|\nabla L(D_j, \beta_t)\|_2^2 \le C$，将原始问题转化为凸问题，并通过拉格朗日对偶性得到闭式最优解。

#### 关键技术细节
- **问题转化**：定义 $\tilde{w}_i = (1-p_i)w_i$，$\delta_i = p_i/(1-p_i)$，引入变量 $\alpha_j^i = \tilde{w}_i a_{i,j}$，原问题变为：
  - 最小化 $\sum_{i=1}^k \delta_i \left(\sum_{j=1}^n \alpha_j^i\right)^2$
  - 约束 $\sum_{i=1}^k \alpha_j^i = 1,\ \forall j$（无偏条件）
- **最优结构（Theorem 1）**：最优解满足 $\sum_j \alpha_j^i = Y_i = \frac{\delta_i^{-1} n}{\sum_{j=1}^k \delta_j^{-1}}$，且 $\sum_i \alpha_j^i = 1$。
- **两种具体构造方案（Scheme I & II）**：
  - **Scheme I（集中式共享）**：所有工作节点共享一个公共数据分区 $D_1$，其余分区各自独占。计算负载 $d = 1 + (k-1)/n < 2$。
  - **Scheme II（顺序/去中心化共享）**：每个工作节点与相邻节点共享一个分区，形成链式结构，同样 $d < 2$。
- **收敛性分析**：
  - $\lambda$-强凸损失：使用 $\gamma_t = 1/(\lambda t)$ 时，$E[\|\beta_T - \beta^*\|_2^2] = O(1/T)$。
  - $\mu$-光滑（非凸）损失：常学习率或衰减学习率下，平均梯度范数趋于零。
  - 同时满足强凸和光滑时，更细致的误差上界说明算法可渐进收敛到真解。

### 3. 实验设计

- **数据集**：大型 **COCO** 数据集（目标检测）。
- **模型**：**MobileNetV3**（约 5.4M 参数），附加实验中使用了 **RetinaNet**（约 34M 参数）。
- **延迟模型**：每个工作节点 $i$ 的延迟概率 $p_i = e^{-\psi_i(\tau_{th}-1)}$，其中 $\psi_i \sim \text{Uniform}(0.1, 2)$，$\tau_{th}$ 为响应时间阈值。
- **对比方法（Benchmarks）**：
  - **GD**（集中式理想梯度下降）
  - **IS-SGD**（忽略延迟的分布式 SGD）
  - **BGC**（伯努利梯度编码）
  - **EHD**（ErasureHead）
  - **OD**（Optimal Decoding）
  - **SGC**（Stochastic Gradient Coding）
- **实验设置**：工作节点数 $k=10$ 和 $k=100$，响应时间阈值 $\tau_{th}=1.1$ 和 $1.5$。每次结果平均 10 次运行。

### 4. 资源与算力

- 论文在 **附录 D** 中明确说明使用的 GPU 资源：
  - 1 × NVIDIA GeForce RTX 3060 (12 GB)
  - 6 × NVIDIA GeForce GTX 1080 (8 GB each)
  - 12 × NVIDIA Tesla P100 (16 GB each)（通过 Kaggle Cloud 提供）
- **未明确说明**总训练时长或单次实验耗时，但提到由于显存限制使用了梯度累积技术。

### 5. 实验数量与充分性

- **主要实验**：图 3 展示了 4 种组合（$k=10,100$ × $\tau_{th}=1.1, 1.5$）的训练迭代损失曲线。
- **计算负载对比**：图 4 展示了损失 vs 计算负载 $d$ 的关系。
- **检测结果可视化**：图 5 展示了一张图片的物体检测结果，定性对比各方法。
- **额外实验**：
  - 图 6：使用 RetinaNet 模型（约 6.3 倍于 MobileNetV3）验证方法在更大模型上的有效性。
  - 图 7：使用 Adam 优化器，测试提出的“两轨解码”（two-track decoding）在自适应梯度方法中的表现。
- **充分性评价**：实验覆盖了不同节点数、不同延迟阈值、不同模型和不同优化器，对比了 6 种现有方法，并包含了定性可视化。结果客观地展示了提出方法在收敛速度和鲁棒性上的优势。但缺少对更多真实异构延迟分布（如非指数分布）的测试，以及更大规模集群（如 $k>100$）的实验。

### 6. 论文的主要结论与发现

- 提出的 **最优结构梯度编码（Optimally Structured Gradient Coding）** 在异构延迟环境中显著优于所有基准方法，收敛速度接近理想 GD。
- 在计算负载 $d<2$ 的低冗余条件下即可获得鲁棒性能，而许多对比方法需要 $d \approx 2.25$ 甚至更高。
- 无偏估计加残差最小化是鲁棒收敛的关键，仅保证无偏（如 SGC）仍不如同时优化方差。
- 扩展实验表明方法对更大模型（RetinaNet）和自适应优化器（Adam，配合两轨解码）依然有效。

### 7. 优点

- **理论完整性**：从问题建模到最优闭式解，再到收敛性分析（强凸、光滑、非凸），理论推导严谨。
- **实用性强**：计算负载低（<2），显式处理异构延迟，对真实部署友好。
- **可扩展性**：提出了两轨解码以适应 Adam 等自适应优化器，以及可推广到 mini-batch SGD 的讨论。
- **实验充分**：在多个设置下对比多种基线，包括定性可视化，结果说服力强。

### 8. 不足与局限

- **初始通信开销大**：每个数据分区需复制到 $d_i$ 个工作节点，训练开始前网络负担重。
- **依赖先验延迟概率 $p_i$**：实际中难以精确估计，论文虽提议了基于历史频率的 MLE 或参数拟合，但未在实验中评估该估计方法的鲁棒性。
- **对自适应优化器的适配复杂**：标准方案直接用于 Adam 时性能下降，需额外设计两轨解码（附录 C.4.2），增加了实现复杂度。
- **实验覆盖范围有限**：未测试非指数分布的延迟模型、更大规模集群（如 $k>100$）或更复杂的任务（如 NLP 大模型），可能遗漏某些现实瓶颈。
- **偏差风险**：对比方法 BGC、EHD、OD、SGC 的计算负载被固定为 $d\approx 2.25$，而本文方法 $d<2$，在公平性上略有不足（计算资源不同），但作者在解释中强调低负载是优点。

（完）
