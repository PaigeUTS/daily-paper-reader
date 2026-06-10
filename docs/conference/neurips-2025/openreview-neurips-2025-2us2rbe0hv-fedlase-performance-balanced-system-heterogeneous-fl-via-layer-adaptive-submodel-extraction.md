---
title: "FedLASE: Performance-Balanced System-Heterogeneous FL via Layer-Adaptive Submodel Extraction"
title_zh: "FedLASE: 通过层级自适应子模型提取实现性能均衡的系统异构联邦学习"
authors: "Qing Hu, Tianchi Liao, WU Shuyi, Zibin Zheng, Chuan Chen"
date: 2025-04-21
pdf: "https://openreview.net/pdf?id=2uS2RBE0hv"
tags: ["query:agents-os"]
score: 5.0
evidence: 针对异构联邦学习的层级自适应子模型提取
tldr: 联邦学习中客户端系统异构导致子模型性能差异大，本文提出FedLASE，通过层级自适应子模型提取，使不同资源水平的客户端获得性能均衡的子模型，提升整体联邦学习性能，可用于异构服务器场景。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-2us2rbe0hv/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1434, \"height\": 413, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-2us2rbe0hv/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1343, \"height\": 658, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-2us2rbe0hv/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1446, \"height\": 443, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-2us2rbe0hv/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1444, \"height\": 456, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-2us2rbe0hv/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1423, \"height\": 227, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-2us2rbe0hv/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1448, \"height\": 157, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-2us2rbe0hv/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1440, \"height\": 211, \"label\": \"Table\"}]"
motivation: 现有子模型提取方法在异构设备间性能差异大，影响联邦学习整体效果。
method: 提出层级自适应的子模型提取方法，根据设备资源水平均衡分配模型层数。
result: 在多个数据集上实现更均衡的性能，提升联邦学习系统整体精度。
conclusion: FedLASE有效缓解系统异构导致的性能偏差，适用于异构计算资源场景。
---

## Abstract
Federated Learning (FL) has gained significant attention for its privacy-preserving capabilities in distributed learning environments. However, the inherent system heterogeneity across edge devices brings significant challenges in deploying a unified global model. Although many submodel extraction methods are designed to address these challenges by selecting a subset of parameters from the global model to accommodate client constraints, our experiments show that existing submodel extraction methods exhibit significant performance discrepancies between submodels with different resource levels, limiting the overall performance of the federated learning system. To overcome these limitations, we propose FedLASE -- a novel Layer-Adaptive Submodel Extraction framework that selects important parameters while preserving the structural integrity of the client models, thereby achieving balanced performance across heterogeneous FL clients and improving the convergence. Specifically, our approach quantifies layer importance based on parameter importance and hierarchically extracts critical parameters within each layer while strictly satisfying resource constraints. Theoretically, we rigorously analyze the convergence of FedLASE and investigate the influence of system heterogeneity on its performance. Extensive experiments demonstrate the superiority of FedLASE over the state-of-the-art methods and its robustness across various system-heterogeneous scenarios.

---

## 论文详细总结（自动生成）

# 论文总结：FedLASE: 通过层级自适应子模型提取实现性能均衡的系统异构联邦学习

## 1. 核心问题与整体含义

**研究动机与背景**  
联邦学习（FL）面临严重的**系统异构**问题：不同客户端（如手机、IoT设备）拥有差异巨大的计算、存储和网络资源。现有子模型提取方法（如 HeteroFL、FedRolex、ScaleFL、FIARSE）虽然允许资源受限客户端从全局模型中选取子集进行训练，但实验表明这些方法在**不同资源水平客户端之间产生显著性能差距**（例如高资源客户端因数量少而更新不充分，性能反而低于低资源客户端），从而限制整个联邦系统的整体表现。作者指出，现有方法对所有参数等量齐观或仅做全局排序，忽略了**层间重要性差异**，导致关键层被过度剪枝，破坏子模型的结构完整性。

**论文目标**  
提出 FedLASE，一种**层级自适应的子模型提取框架**，在满足客户端资源约束的同时，保留每层中最重要的参数，使得不同资源水平的子模型获得均衡的性能，并提升收敛质量。

## 2. 方法论

**核心思想**  
FedLASE 结合**参数重要性**与**层重要性**，动态地为每个客户端分配各层的提取比例，确保关键结构组件（如第一层、最后一层、归一化层、偏置项）被完整保留，其余参数按层重要性比例在该层内选取 top-k 重要参数。

**关键技术细节**  
- **重要性度量**：参数重要性 = |θ_{l,i}|（参数绝对值），层重要性 S_l = mean_i |θ_{l,i}|，经对数归一化：  
  Ṡ_l = log(1+S_l) / Σ_j log(1+S_j)  
- **层自适应提取比例**：对于每个客户端 n，给定资源约束 r_n（可保留参数比例），可剪枝参数上限 d_n = r_n * d，减去必须保留的偏置等参数数量 d̃，剩余参数按层重要性比例分配：  
  r_{n,l_i} = Ṡ_{l_i} · (d_n - d̃) / Σ_i (Ṡ_{l_i} · d_{l_i})  
  然后在每层内按参数重要性排序，保留前 r_{n,l_i}·d_{l_i} 个参数。  
- **局部训练优化**：采用**直通估计器（STE）** 增强梯度，公式(2)对梯度进行缩放，使得重要参数梯度得到更大权重。  
- **模型聚合**：采用**重叠平均策略**，仅对参与训练的客户端更新过的参数进行平均，防止被剪枝参数影响全局模型。

**理论分析**  
论文引入**模型缩减噪声假设**（Assumption 1），量化因子模型提取导致的误差，并证明在标准假设下 FedLASE 以 O(1/√T) 速率收敛到平稳点邻域，且系统异构性越强（资源水平低、数量多），收敛上界越大。

## 3. 实验设计

**数据集与模型**  
- 数据集：CIFAR-10、CIFAR-100（图像分类）  
- 模型：ResNet-18（主），ResNet-34（扩展），使用静态 BN 替代 batch norm。

**系统异构设置**  
定义异构系统为 {level_1,...,level_p}-{N_1,...,N_p}，其中 level 表示可保留全局模型比例，N_i 为该资源水平客户端数量。  
- 四等级：{1, 1/4, 1/16, 1/64}  
- 五等级：{1, 16/25, 9/25, 4/25, 1/25}  
- 客户端分配方案：例如 {5,10,25,60}（100客户端，高资源少、低资源多）等3种分配（四等级3种，五等级3种）。

**数据异构**  
- IID 与 Dirichlet 分布（α=0.1, 0.3）对比。

**对比方法（Baselines）**  
- Random（每层随机选取相同比例，保留首尾层）  
- HeteroFL、FedRolex、ScaleFL、FIARSE（均为子模型提取方法）

**设置**  
- 每轮选取10%客户端（100个中选10个）  
- 2000轮，每轮5个本地 epoch，batch size 20  
- SGD with momentum，学习率 {0.01,0.1}，动量 {0.0,0.8,0.9}  
- 报告最后20轮平均 top-1 准确率，重复3次取平均。

## 4. 资源与算力

**明确说明**（论文附录 F 实验计算资源部分）：  
- CPU：AMD Ryzen 9 9950X 16-Core (32线程)  
- 内存：128 GB  
- 磁盘：1.8 TB SSD  
- GPU：2 张 NVIDIA GeForce RTX 4090 (各24 GB)  
- 系统：Linux，PyTorch 2.5.1  
- 总训练时间：所有实验总计约 **3–4 周**。

## 5. 实验数量与充分性

**实验组数**：  
1. **主表（Table 1）**：CIFAR-100，2种异构系统×各自3种客户端分配（共6种场景），对比6种方法，报告局部准确率（AccL）和全局准确率（AccG）。  
2. **表2**：CIFAR-10 和 CIFAR-100，6种异构系统×6种方法，共72个条件。  
3. **表3**：数据异构实验（IID, Dir(0.3), Dir(0.1)），2个数据集×6种方法，共36个条件。  
4. **表4**：网络架构实验（ResNet-18 vs ResNet-34），2种异构系统×2数据集×6种方法，共48个条件。  
5. **消融/分析性实验**：图1展示收敛曲线（4个子图），复杂度分析（表5）。  
6. **理论证明**：收敛定理及推导。

**充分性评价**：实验覆盖了多种系统异构程度、多种客户端分布、多种数据分布、多种网络架构，结果统计了三重复现的平均值，对比方法全面。结论客观合理。但未报告误差棒（论文承认“No”），也未进行统计显著性检验，这在严谨性上略有不足，但性能提升幅度大（7%-16%），可信度较高。

## 6. 主要结论与发现

1. **FedLASE 在所有异构场景下均显著优于 SOTA 方法**：例如在 CIFAR-100 上，平均全局准确率比第二高方法高 9.56% 和 7.88%。  
2. **性能平衡性突出**：传统方法中高资源客户端性能反而低于低资源客户端，FedLASE 使得所有资源水平客户端性能接近，消除“富者更弱”现象。  
3. **鲁棒性**：在数据异构（IID → 高度非IID）下性能下降最小，且随系统异构变化波动极小（如 CIFAR-100 上不同客户端分布仅波动约1%）。  
4. **理论验证**：收敛率 O(1/√T)，且系统异构性越大收敛上界越大，与实验一致。  
5. **计算复杂度合理**：层内排序复杂度 O(Σ d_{li} log d_{li}) 低于全局排序 O(d log d)，未见明显额外开销。

## 7. 优点

- **创新点明确**：首次将层重要性引入子模型提取，强调结构完整性，而非全局统一剪枝。  
- **理论贡献**：首次分析系统异构性对收敛率的影响，提出模型缩减噪声假设。  
- **实验覆盖面广**：多种系统异构程度、客户端分布、数据分布、网络架构，结果一致性高。  
- **实用性**：方法简单（基于参数绝对值重要性），无需额外公共数据集，适合真实部署。  
- **性能均衡**：尤其解决了高资源客户端因数量少而训练不足的痛点。

## 8. 不足与局限

- **缺乏误差棒和统计显著性测试**：论文承认未提供 error bars，虽然性能提升大，但无法判断 variability。  
- **仅使用图像分类任务**（CIFAR-10/100），未在 NLP、推荐系统、多模态等任务上验证，泛化性存疑。  
- **模型规模有限**：仅测试 ResNet-18/34，未在更大的模型（如 ViT、ResNet-50/101）上验证。  
- **未对比知识蒸馏类方法**（如 FedDF、FedGKT），仅对比子模型提取类方法，可能范围不够完整。  
- **假设限制**：理论证明依赖于 L-smooth、有界梯度等假设，实际中可能不完全满足。  
- **参数重要性度量仅用绝对值**：未考虑二阶信息（如 Hessian）或基于梯度的显著性，可能不是最优。  
- **代码未开源**（论文称接受后公开），影响可复现性。  
- **对超参数敏感**：层重要性对数归一化中的对数底数（自然对数）固定，未探讨不同变换的影响。

（完）
