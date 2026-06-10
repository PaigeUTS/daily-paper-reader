---
title: Pragmatic Heterogeneous Collaborative Perception via Generative Communication Mechanism
title_zh: 基于生成通信机制的实用异构协作感知
authors: "Junfei Zhou, Penglin Dai, Quanmin Wei, Bingyi Liu, Xiao Wu, Jianping Wang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=CYG3kmFsgM"
tags: ["query:agents-os"]
score: 4.0
evidence: 异构多智能体协作与生成通信
tldr: 针对异构多智能体协作感知中领域差异和扩展性难题，本文提出生成通信机制GenComm，通过生成式方法对齐不同传感器和模型的特征，无需重新训练编码器。实验表明该方法在多个异构场景下提升了感知性能，且易于扩展到新智能体。该工作对于智能体异构计算基础设施的设计具有参考价值。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-cyg3kmfsgm/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1428, \"height\": 402, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cyg3kmfsgm/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1445, \"height\": 531, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cyg3kmfsgm/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1421, \"height\": 322, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cyg3kmfsgm/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 632, \"height\": 387, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cyg3kmfsgm/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1413, \"height\": 549, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cyg3kmfsgm/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1322, \"height\": 1145, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cyg3kmfsgm/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1378, \"height\": 332, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cyg3kmfsgm/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1348, \"height\": 951, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cyg3kmfsgm/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1333, \"height\": 666, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cyg3kmfsgm/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1408, \"height\": 900, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-cyg3kmfsgm/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1450, \"height\": 534, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cyg3kmfsgm/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1456, \"height\": 691, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cyg3kmfsgm/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 639, \"height\": 334, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cyg3kmfsgm/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1352, \"height\": 344, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cyg3kmfsgm/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1352, \"height\": 560, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cyg3kmfsgm/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1255, \"height\": 1060, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cyg3kmfsgm/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1429, \"height\": 175, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cyg3kmfsgm/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1419, \"height\": 361, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cyg3kmfsgm/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1383, \"height\": 137, \"label\": \"Table\"}]"
motivation: 异构智能体协作中传感器和模型差异导致域间隙，现有方法需要侵入式重训练或扩展性差。
method: 提出GenComm生成通信机制，通过生成式特征对齐实现无缝异构协作感知。
result: 在多个异构感知任务上验证了有效性和扩展性，优于基于适配和重建的方法。
conclusion: GenComm为异构智能体系统的高效协作提供了轻量级的通信方案。
---

## Abstract
Multi-agent collaboration enhances the perception capabilities of individual agents through information sharing. However, in real-world applications, differences in sensors and models across heterogeneous agents inevitably lead to domain gaps during collaboration. Existing approaches based on adaptation and reconstruction fail to support *pragmatic heterogeneous collaboration* due to two key limitations: (1) Intrusive retraining of the encoder or core modules disrupts the established semantic consistency among agents; and (2) accommodating new agents incurs high computational costs, limiting scalability. To address these challenges, we present a novel **Gen**erative **Comm**unication mechanism (GenComm) that facilitates seamless perception across heterogeneous multi-agent systems through feature generation, without altering the original network, and employs lightweight numerical alignment of spatial information to efficiently integrate new agents at minimal cost. Specifically, a tailored Deformable Message Extractor is designed to extract spatial message for each collaborator, which is then transmitted in place of intermediate features. The Spatial-Aware Feature Generator, utilizing a conditional diffusion model,  generates features aligned with the ego agent's semantic space while preserving the spatial information of the collaborators. These generated features are further refined by a Channel Enhancer before fusion. Experiments conducted on the OPV2V-H, DAIR-V2X and V2X-Real datasets demonstrate that GenComm outperforms existing state-of-the-art methods, achieving an 81\% reduction in both computational cost and parameter count when incorporating new agents. Our code is available at https://github.com/jeffreychou777/GenComm.

---

## 论文详细总结（自动生成）

# 基于生成通信机制的实用异构协作感知论文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：在真实世界的多智能体协作感知系统中，不同智能体（车辆、路侧单元等）通常配备异构的传感器（如不同线数的激光雷达、摄像头）和不同的模型架构（如PointPillar、SECOND、EfficientNet等）。这些异构性导致智能体间存在显著的“域间隙”（domain gap），即在特征层面语义不一致。
- **现有方法的不足**：现有基于“适应”（adaptation）和“重建”（reconstruction）的方法存在两大关键缺陷：  
  - **侵入性重训练**：需要重新训练编码器或核心模块，这会破坏智能体之间已经建立的语义一致性。  
  - **可扩展性差**：当新智能体加入协作时，需要高额的计算成本（参数和FLOPs），难以在实际场景中持续扩展。
- **整体含义**：本文旨在解决“**实用异构协作感知**”（Pragmatic Heterogeneous Collaborative Perception）的核心挑战——如何在最小成本下容纳新增的异构智能体，同时保持原有智能体间的语义一致性。

## 2. 论文提出的方法论

- **核心思想**：提出一种**生成式通信机制**（GenComm）。每个主车（ego agent）本地接收来自协作者的**空间消息**（spatial message），并通过条件扩散模型生成与主车语义空间对齐、同时保留协作者空间信息的特征，从而避免直接传输可能带有域差异的中间特征。
- **关键技术细节**：
  - **可变形消息提取器（Deformable Message Extractor, DME）**：利用可变形卷积自适应采样周围像素，从协作者的特征图中提取紧凑的空间消息（压缩至2通道），替代原始中间特征进行传输。
  - **空间感知特征生成器（Spatial-Aware Feature Generator, SAFG）**：基于条件扩散模型（U-Net），以协作者的空间消息作为条件，从高斯噪声逐步去噪生成与主车特征语义一致且保留协作者空间信息的特征。
  - **通道增强器（Channel Enhancer, CE）**：采用PConv和门控机制，在通道维度对生成的特征进行精炼，增强其与主车特征的一致性。
  - **轻量级数值对齐（Numerical Alignment）**：在异构协作阶段，仅为每个接收方训练一个轻量级的消息提取器（DME），以对齐空间消息的数值分布（如置信度），而不改变任何原始网络。
- **训练策略**：分为两阶段：
  - **阶段1**：在**同构**协作设置下端到端训练三个核心组件（DME、SAFG、CE）。
  - **阶段2**：在**异构**协作设置下，仅微调接收方专属的轻量级DME，对齐数值分布。
- **损失函数**：阶段1联合分类损失（focal loss）、回归损失（smooth L1）、生成损失（MSE）；阶段2仅使用分类和回归损失。

## 3. 实验设计

- **数据集**：三个数据集，覆盖仿真和真实场景。  
  - **OPV2V-H**：仿真数据集，基于CARLA，扩展了传感器配置，支持异构研究。  
  - **DAIR-V2X**：真实世界数据集，包含车-路协同（车有40线LiDAR，路侧有300线LiDAR）。  
  - **V2X-Real**：真实世界大规模数据集，含2辆车和2个RSU（共4个智能体），用于评估可扩展性。
- **异构智能体配置**：  
  - OPV2V-H上使用4种智能体：L64<sup>P</sup>（64线LiDAR+PointPillar）、CE（相机+EfficientNet）、L32<sup>S</sup>（32线LiDAR+SECOND）、CR（相机+ResNet-101）。  
  - DAIR-V2X类似。  
  - V2X-Real上使用4个不同深度的PointPillar智能体（深、中、浅、无主干）。
- **对比方法**：  
  - 适应型方法：MPDA（单阶段适配）、STAMP（两阶段适配，依赖协议语义空间）、BackAlign（来自HEAL，强制对齐语义空间）。  
  - 重建型方法：CodeFilling（基于共享码本索引重建特征）。  
- **评估指标**：AP50、AP70（OPV2V-H和DAIR-V2X）；AP30、AP50（V2X-Real）。还比较了通信量、参数量、FLOPs。

## 4. 资源与算力

- 文中提到所有方法（包括基线和GenComm）均在**NVIDIA RTX 3090**上训练，并采用相同的设置确保公平。  
- **未明确说明**GPU数量、具体训练时长、是否使用多卡等细节。因此无法精确给出算力消耗，但可推测为单卡或少量GPU环境下的实验。

## 5. 实验数量与充分性

- **实验组数**：较多，包括：  
  - 静态异构协作实验（表1）：OPV2V-H和DAIR-V2X，含两种融合网络（AttFuse、V2X-ViT）下各方法对比。  
  - 动态扩展实验（表2）：OPV2V-H和V2X-Real上逐步增加智能体数量（从1到4）。  
  - 可扩展性分析：参数量和FLOPs对比（图1(d)和表2）。  
  - 鲁棒性分析（图3）：对位姿噪声和时间延迟的鲁棒性。  
  - 消融实验（表3和图4）：对DME、通道增强器、数值对齐以及消息通道大小的消融。  
  - 额外附录实验：DAIR-V2X上的位姿噪声鲁棒性（表A3）、延迟对比（表A4）、动态智能体参与影响（表A5）、消息退化影响（表A6）。
- **充分性评估**：实验覆盖了多个数据集、多种异构场景、多种基线方法，并进行了充分的消融和鲁棒性验证，设计相对全面且客观。数据集包含仿真和真实数据，增强了结论的可靠性。

## 6. 论文的主要结论与发现

- GenComm在**大多数静态和动态异构协作场景**下，**检测性能优于现有方法**（如STAMP、CodeFilling等），同时**通信量更低**（压缩至2通道，相比完整特征图减小64倍）。  
- 在**可扩展性**方面，GenComm当加入新智能体时，额外参数仅为0.31M、FLOPs仅0.615G，比STAMP降低81%，比其他方法降低62%以上，展示了极低的增量成本。  
- 对**位姿误差和时间延迟**具有更强的鲁棒性，性能下降更平缓。  
- 消融实验证实**可变形消息提取器、通道增强器、数值对齐**每个组件均对最终性能有贡献。

## 7. 优点

- **非侵入性**：仅需训练轻量级DME即可适配异构智能体，原始编码器、融合网络、任务头均保持不变，保留已建立的语义一致性。
- **生成式对齐**：通过条件扩散模型在**本地生成**对齐的特征，巧妙避免跨域传输特征带来的域间隙问题。
- **超低扩展成本**：新增智能体只需微调极小参数量的DME（0.31M），对比现有方法显著降低。
- **通信高效**：传输的仅是2通道空间消息（压缩率高达64倍），减少了带宽需求。
- **实验充分**：覆盖多数据集、多异构类型、多基线，并进行了鲁棒性和消融分析，可信度高。
- **实际部署思路清晰**：提出了一个三阶段真实部署流程（各厂商同构预训练 → 厂商间协商训练DME → 即插即用），具有应用潜力。

## 8. 不足与局限

- **依赖厂商间共识**：如Limitations所述，方法需要不同厂商（vendor）之间达成协作共识，实际中可能因商业竞争、安全风险等因素难以实现。
- **实验仅覆盖3D目标检测**：未验证在其他感知任务（如语义分割、跟踪）上的效果，通用性有待进一步证明。
- **扩散模型推理时延**：虽然总延迟可接受（20.7ms），但与部分方法（如BackAlign的0ms额外延迟）相比仍有引入，在极端实时场景下可能存在挑战。
- **数值对齐仅针对消息**：虽然空间消息域差异较小，但数值对齐仍可能无法完全消除所有数值偏差，在高噪声或极端异构条件下性能可能下降。
- **未提供统计误差棒**：文中未报告多次运行的平均值和标准差，实验结果的稳定性缺乏量化评估。
- **未讨论隐私或安全性**：生成式通信虽降低了原始特征泄露风险，但未涉及对抗攻击、投毒攻击等安全问题，实际部署中还需额外防范。

（完）
