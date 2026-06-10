---
title: "FedEL: Federated Elastic Learning for Heterogeneous Devices"
title_zh: "FedEL: 异构设备的联邦弹性学习"
authors: "Letian Zhang, Bo Chen, Jieming Bian, Lei Wang, Jie Xu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=DfeHiyTz2W"
tags: ["query:agents-os"]
score: 5.0
evidence: 异构设备的联邦弹性学习
tldr: 联邦学习中设备异构导致训练延迟和不一致，本文提出FedEL，通过动态调整每个设备的模型大小实现弹性训练，在保持准确率的同时提升训练效率，有效缓解异构问题，可用于异构服务器资源管理。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfehiytz2w/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 784, \"height\": 710, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfehiytz2w/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 699, \"height\": 345, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfehiytz2w/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 654, \"height\": 335, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfehiytz2w/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 365, \"height\": 268, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfehiytz2w/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 361, \"height\": 261, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfehiytz2w/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 662, \"height\": 498, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfehiytz2w/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1452, \"height\": 340, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfehiytz2w/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 375, \"height\": 310, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfehiytz2w/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 389, \"height\": 308, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfehiytz2w/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1456, \"height\": 320, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfehiytz2w/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 364, \"height\": 294, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfehiytz2w/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 357, \"height\": 293, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfehiytz2w/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 745, \"height\": 290, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfehiytz2w/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1451, \"height\": 340, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfehiytz2w/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1448, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfehiytz2w/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1448, \"height\": 341, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfehiytz2w/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1389, \"height\": 565, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfehiytz2w/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1465, \"height\": 1071, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfehiytz2w/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1463, \"height\": 1064, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-dfehiytz2w/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1435, \"height\": 333, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-dfehiytz2w/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1443, \"height\": 317, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dfehiytz2w/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1099, \"height\": 265, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dfehiytz2w/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 761, \"height\": 225, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dfehiytz2w/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 576, \"height\": 145, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dfehiytz2w/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1430, \"height\": 435, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dfehiytz2w/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1449, \"height\": 434, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dfehiytz2w/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 476, \"height\": 155, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-dfehiytz2w/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1091, \"height\": 157, \"label\": \"Table\"}]"
motivation: 联邦学习中异构设备导致训练延迟和模型性能下降。
method: 提出弹性学习框架，根据设备能力动态调整模型大小。
result: 在保持准确率前提下提升训练效率，减少等待时间。
conclusion: FedEL为异构联邦学习提供了一种高效的弹性训练方案。
---

## Abstract
Federated learning (FL) enables distributed devices to collaboratively train machine learning (ML) models while maintaining data privacy. However, the heterogeneous hardware capabilities of participating devices often result in significant training delays, as straggler clients with limited resources prolong the aggregation process. Existing solutions such as client selection, asynchronous FL, and partial training partially address these challenges but encounter issues such as reduced accuracy, stale updates, and compromised model performance due to inconsistent training contributions.
To overcome these limitations, we propose FedEL, a federated elastic learning framework that enhances training efficiency while maintaining model accuracy. FedEL introduces a novel window-based training process, sliding the window to locate the training part of the model
and dynamically selecting important tensors for training within a coordinated runtime budget. This approach ensures progressive and balanced training across all clients, including stragglers. Additionally, FedEL employs a tensor importance adjustment module, harmonizing local and global tensor importance to mitigate biases caused by data heterogeneity. The experiment results shows that FedEL achieves up to 3.87× improvement in time-to-accuracy compared to baselines while maintaining or exceeding final test accuracy.

---

## 论文详细总结（自动生成）

# 论文详细总结：FedEL: Federated Elastic Learning for Heterogeneous Devices

## 1. 核心问题与整体含义（研究动机和背景）

联邦学习（FL）允许分布式设备协作训练模型，同时保护数据隐私。然而，设备硬件能力异构会导致“掉队者”（straggler）问题：慢速设备拖长聚合时间，降低整体训练效率。现有解决方案（客户端选择、异步FL、部分训练）存在以下局限：
- 客户端选择：可能忽略慢速设备上的独特数据，导致全局模型精度下降。
- 异步FL：慢速设备的更新频率低且可能过时，影响收敛。
- 部分训练（如宽度/深度缩放）：导致通道不匹配、特征提取层训练不足，模型性能受损。

因此，需要一种新范式，能在资源异构下实现高效且精度不降的FL。

## 2. 方法论：核心思想与关键技术细节

### 2.1 核心思想
FedEL（Federated Elastic Learning）基于 **ElasticTrainer**（单设备上的弹性张量选择方法），但针对FL场景进行改进，提出两个关键模块：
1. **滑动窗口训练**：将DNN划分为多个块，每个FL轮次滑动窗口选择一部分块进行训练，确保整个模型逐步均衡地得到训练。
2. **张量重要性调整**：结合全局模型重要性（使用前后两轮模型差值和学习率估算）与本地重要性，减弱非独立同分布（non-IID）数据导致的偏差。

### 2.2 关键技术细节
- **滑动窗口机制**：
  - 模型被分为B个块（如VGG16每层一个块，ResNet50每个残差结构一个块）。
  - 离线时用ElasticTrainer的时间分析器测量每个张量的训练时间，聚合成块级时间。
  - 初始窗口从第一个块开始，包含累积训练时间略超过阈值\(T_{th}\)的块。
  - 每轮滑动：前沿（Front Edge）向后移动包含更深块，尾沿（End Edge）在块内无重要张量时收缩。
  - 每个窗口末尾附加轻量级输出层（早退），使窗口可独立训练。
- **张量重要性调整**：
  - 全局重要性：\(I_g = \frac{(w_{r+1} - w_r)^2}{\eta_n}\)，其中\(w_{r+1}\)是聚合后的全局模型，\(\eta_n\)是学习率。
  - 调整后本地重要性：\(I_{n,r+1} = \beta \cdot I_{n,r+1} + (1-\beta) \cdot I_g\)，\(\beta\)为平衡参数（默认0.6）。
- **算法流程**（见论文Algorithm 1）：
  - 离线：每个客户端运行TensorTimeProfiling。
  - 在线每轮：客户端接收全局模型 → 评估本地重要性 → 计算全局重要性 → 调整重要性 → 滑动窗口 → 在窗口内用ElasticTrainer选择重要张量 → 训练并上传更新 → 服务器聚合。

### 2.3 公式/算法（文字说明）
优化目标：在训练时间约束\(T_{th}\)下，最大化所选张量的重要性之和。ElasticTrainer用动态规划从最后张量开始反向选择，直至累计时间达到\(T_{th}\)。FedEL修改其起点为当前窗口的最后张量，并在张量超出窗口范围时停止。

---

## 3. 实验设计

### 3.1 数据集、模型与任务
- **图像分类**：CIFAR-10（VGG16）、Tiny ImageNet（VGG16）
- **语音识别**：Google Command Speech（ResNet50）
- **自然语言处理**：Reddit（轻量级Albert）— 下一个词预测（困惑度）。
- 数据划分：Dirichlet分布（\(\alpha=0.1\)）模拟non-IID。

### 3.2 场景与基准（Benchmark）
- **小规模实际设备**：10台边缘设备（5台NVIDIA Jetson Xavier + 5台Jetson Orin），通过WiFi连接PC服务器。
- **大规模模拟**：基于Orin的离线时间分析，模拟四种设备类型（1×、1/2、1/3、1/4 Orin速度），共100个客户端，每轮随机选25%参与。

### 3.3 对比方法（Baselines）
- FedAvg, ElasticTrainer, HeteroFL, DepthFL, PyramidFL, TimelyFL, FIARSE。

### 3.4 评估指标
- 精度（Accuracy）、训练时间（Wall-clock time）、加速比（Time-to-accuracy提升倍数）、内存占用、能耗。

---

## 4. 资源与算力

论文明确说明：
- **小规模实验**：5台Xavier NX（算力较弱） + 5台Orin（较强），PC服务器，WiFi连接。
- **大规模模拟**：PC配备NVIDIA 3090 GPU（用于训练模拟），基于Orin profiling数据缩放。
- **训练时长**：以CIFAR-10为例，FedAvg需119.8h，FedEL仅63.8h（加速1.87×）；Tiny ImageNet上FedAvg 563.1h，FedEL 156.8h（3.59×）。
- 未明确给出GPU数量或集群配置，但模拟是在单台3090上完成。

---

## 5. 实验数量与充分性

### 5.1 实验数量
- **主要对比实验**：4个数据集 × 两个场景（10设备/100设备），共约8组完整对比（表1）。
- **消融实验**：
  - 平衡参数\(\beta\)的影响（图11、图15，5个取值）。
  - 运行时阈值\(T_{th}\)的影响（图12、图16，3个取值）。
  - 窗口滑动机制（FedEL-C对比FedEL，图13、图17）。
  - 张量选择可视化（图10、图18-20）。
  - 内存和能耗对比（图8、图9）。
  - 附加实验：与FedProx/FedNova结合（表3）、不同参与率（表5、表6）、不同电源模式（表7）、系统开销（表8）。
- **统计分析**：置信区间箱线图（图21）。

### 5.2 充分性与公平性
- 实验覆盖了图像、语音、NLP三类任务，模型包括CNN和Transformer。
- 对比了7种代表性基线方法，且设置了相同约束（如\(T_{th}\)设为最快设备的全模型训练时间）。
- 消融实验验证了每个组件的必要性。
- 统计显著性提供了误差棒。
- **公平性**：基线方法参数按原论文设置；FedEL的超参数（\(\beta=0.6\)）通过实验选择，但未对所有基线做完全相同的调优，存在一定潜在偏差。

---

## 6. 主要结论与发现

1. **速度提升**：FedEL在保持或超过最终精度的前提下，时间-精度加速比达到1.87×~3.87×（与FedAvg相比）。
2. **精度保持**：最终精度与FedAvg持平或更高（例如CIFAR-10: 56.51% vs FedAvg 56.13%）。
3. **内存与能耗**：内存降低32.7%，能量消耗降低49.59%。
4. **适配性**：可灵活集成到FedProx、FedNova等聚合算法中；适用于多种模型和任务。
5. **自适应选择**：滑动窗口和重要性调整使模型能够根据设备和数据特征动态选择训练部分，减轻掉队者和非IID影响。

---

## 7. 优点

- **创新性**：提出滑动窗口+弹性张量选择，系统性地解决了异构FL中训练覆盖不均衡和重要性偏差问题。
- **实用性**：在真实设备上验证（Jetson），并扩展到大规模模拟，实验设置贴近实际。
- **通用性**：不依赖特定模型架构，支持CNN和Transformer；兼容早退（early exit）。
- **效率**：不仅加速训练，还降低内存和能耗，适合边缘设备。
- **理论支撑**：提供了收敛性分析和证明（附录E），表明收敛率与标准FL同阶，仅增加有界偏置项。

---

## 8. 不足与局限

1. **硬件异构程度有限**：实际设备仅两种（Xavier和Orin），模拟缩放基于Orin profiling，可能无法完全反映极端异构（如手机、树莓派等）。
2. **未考虑网络带宽异构**：仅关注计算异构，未将通信时间纳入约束（论文承认此局限，见附录D）。
3. **未包含隐私保护分析**：虽然声称可与差分隐私兼容，但未实验验证。
4. **超参数敏感性**：平衡参数\(\beta\)和阈值\(T_{th}\)需要调优，不同任务可能需不同设置。
5. **额外系统开销**：滑动窗口和张量重要性调整增加少量前期处理时间（表8显示<2.5%），但对资源极有限的设备可能仍有影响。
6. **大规模模拟假设简化**：模拟中设备类型仅四种，且假设计算时间完美缩放，真实网络延迟、CPU/GPU竞争等因素未建模。

（完）
