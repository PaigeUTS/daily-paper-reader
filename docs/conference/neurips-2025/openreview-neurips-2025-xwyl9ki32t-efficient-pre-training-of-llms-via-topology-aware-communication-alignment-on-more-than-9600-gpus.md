---
title: Efficient Pre-Training of LLMs via Topology-Aware Communication Alignment on More Than 9600 GPUs
title_zh: 通过拓扑感知通信对齐在超过9600个GPU上高效预训练LLM
authors: "Guoliang HE, YOUHE JIANG, Wencong Xiao, Jiang Kaihua, Shuguang Wang, Jun Wang, Du Zixian, Zhuo Jiang, Xinlei Zhang, Binhang Yuan, Eiko Yoneki"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=xWYL9Ki32T"
tags: ["query:agents-os"]
score: 9.0
evidence: 大规模GPU集群上拓扑感知的LLM预训练调度
tldr: 针对大规模LLM预训练中通信模式复杂、带宽竞争严重的问题，本文提出Arnold调度系统，通过将通信模式与数据中心拓扑对齐来优化资源调度。在超过9600个GPU的集群上验证了有效性，显著提升了训练效率并降低了通信开销。该工作为大规模异构计算基础设施支持大模型训练提供了实用方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-xwyl9ki32t/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 701, \"height\": 349, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xwyl9ki32t/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1384, \"height\": 633, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xwyl9ki32t/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1291, \"height\": 330, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xwyl9ki32t/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1423, \"height\": 349, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xwyl9ki32t/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1294, \"height\": 279, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xwyl9ki32t/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 735, \"height\": 435, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xwyl9ki32t/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1151, \"height\": 371, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xwyl9ki32t/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 867, \"height\": 350, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xwyl9ki32t/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 864, \"height\": 345, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xwyl9ki32t/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 575, \"height\": 214, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xwyl9ki32t/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 982, \"height\": 394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xwyl9ki32t/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 724, \"height\": 329, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xwyl9ki32t/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1435, \"height\": 460, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xwyl9ki32t/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 853, \"height\": 535, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-xwyl9ki32t/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 853, \"height\": 311, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-xwyl9ki32t/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 741, \"height\": 186, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xwyl9ki32t/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 651, \"height\": 144, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xwyl9ki32t/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 417, \"height\": 338, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xwyl9ki32t/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 420, \"height\": 334, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xwyl9ki32t/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 273, \"height\": 218, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-xwyl9ki32t/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 714, \"height\": 216, \"label\": \"Table\"}]"
motivation: 大规模LLM预训练中通信模式复杂，资源调度低效导致带宽争用和训练性能下降。
method: 提出Arnold系统，通过拓扑感知的通信对齐策略优化GPU间数据传输调度。
result: 在超过9600个GPU的集群上实现了训练效率的显著提升，减少了通信瓶颈。
conclusion: 该工作为在大规模异构集群上高效进行LLM预训练提供了可部署的调度框架。
---

## Abstract
The scaling law for large language models (LLMs) depicts that the path towards machine intelligence necessitates training at large scale. Thus, companies continuously build large-scale GPU clusters, and launch training jobs that span over thousands of computing nodes. However, LLM pre-training presents unique challenges due to its complex communication patterns, where GPUs exchange data in sparse yet high-volume bursts within specific groups. Inefficient resource scheduling exacerbates bandwidth contention, leading to suboptimal training performance. This paper presents Arnold, a scheduling system summarizing our experience to effectively align LLM communication patterns to data center topology at scale. In-depth characteristic study is performed to identify the impact of physical network topology to LLM pre-training jobs. Based on the insights, we develop a scheduling algorithm to effectively align communication patterns to physical network topology in data centers. Through simulation experiments, we show the effectiveness of our algorithm in reducing the maximum spread of communication groups by up to $1.67$x. In production training, our scheduling system improves the end-to-end performance by $10.6\%$ when training with more than $9600$ Hopper GPUs, a significant improvement for our training pipeline.

---

## 论文详细总结（自动生成）

# 高效预训练LLM: 基于拓扑感知通信对齐的调度系统（Arnold）

## 1. 核心问题与整体含义（研究动机和背景）

- **背景**：LLM 依靠扩展法则（Scaling Law）需要大规模训练，公司构建数千GPU节点的集群。然而，LLM预训练具有独特的通信模式，GPU在特定组内稀疏但高容量地突发交换数据。
- **问题**：现有的集群调度器（如Best-fit、GPU-packing等）未考虑LLM通信模式与数据中心多级Fat-Tree拓扑的对齐，导致跨交换机通信增加、带宽竞争，训练性能次优。
- **目标**：设计一个调度系统Arnold，使LLM预训练作业的通信模式与数据中心物理拓扑有效对齐，从而提升大规模训练性能。

## 2. 方法论：核心思想、关键技术细节、算法流程

- **核心思想**：拓扑感知的通信对齐。通过分析通信操作性能（NCCL测试）和端到端训练表现，发现PP组通信往往是瓶颈，DP和PP组存在折衷。调度算法旨在最小化DP组和PP组在minipod上的最大扩展。
- **关键技术细节**：
  - **工作负载表示**：使用通信矩阵，行代表PP组，列代表DP组。每个节点附加权重、DP和PP通信量（通过分析模型估算）。
  - **调度目标函数**：最小化加权最大扩展，公式（2）：
    `MIN [α max_i(D(*)) + β max_j(D(*))]`
    其中D度量通信组跨越的minipod数量。通过领域特定简化（通信组同质同步），转化为类装箱MIP问题（公式4-10），引入辅助变量T表示最大扩展，通过混合整数规划求解。
  - **平衡DP和PP折衷**：亲和参数α和β基于先验表征数据库，根据模型配置和GPU类型查找最佳匹配。例如24B dense模型α=0（PP优先），MoE模型α=0.3, β=0.7。
  - **资源管理**：制定排队策略（Algorithm 1），为即将到来的LPJ保留节点；同时利用ML驱动的JCT预测器（GBM，RMSE 1.61）将短作业调度到保留区以提高利用率。
- **算法流程**：用户指定GPU数量和并行度 → 计算通信矩阵 → 根据先验知识确定α, β → 求解MIP得到minipod分配 → 在minipod内分配连续rank以减少跨交换机通信 → 保留资源并管理作业队列。

## 3. 实验设计

- **模拟实验**：
  - 场景：三种网络拓扑和作业配置（小、中、大规模），如表1所示。
  - 基准方法：Best-fit、Random-fit、GPU-packing（修改为minipod粒度）、Topo-aware（层次双递归二分映射）。
  - 指标：加权最大扩展、调度延迟。
- **真实集群实验**：
  - 环境：H800 GPU集群，超过2000节点，InfiniBand网络（400GB/s），NVLink（400GB/s）。
  - 对比系统：MegaScale（SOTA生产系统）。
  - 作业：一个MoE变体模型，先208 GPU验证，再9600+ GPU（1200+节点）全规模训练。
  - 额外实验：L20 GPU集群（不同GPU类型）、开源模型Llama3 8B + RoCE网络。
- **消融实验**：不同α值对调度效果的影响；资源管理策略（No-Reserve、No-JCT对比）；JCT预测器精度对比（GBM vs DNN）；各kernel级的性能分解。

## 4. 资源与算力

| 资源信息 | 具体内容 |
|---------|---------|
| GPU 型号 | NVIDIA H800（主要实验）、L20（附加实验） |
| GPU 数量 | 模拟中最多1019节点；真实实验使用208和9600+ GPUs |
| 节点配置 | 每个节点8个GPU，绑定8个InfiniBand NIC |
| 网络带宽 | 节点内NVLink 400GB/s，节点间InfiniBand 400GB/s |
| 训练时长 | 全规模LPJ运行超过一个月 |
| 模型参数量 | 超过400B参数（商业敏感未公开具体值） |
| 其他资源 | 使用三个层次的叶脊Spine交换机（CLOS拓扑）；每个交换机32端口 |

## 5. 实验数量与充分性

- **模拟实验**：3种设置×多种α值（0.2,0.5,0.8）共9组对比，每种方法重复多次？论文未提随机种子，但MIP求解是确定性的。此外测试了调度延迟（不同节点数）。
- **真实实验**：2个规模（208 GPU, 9600+ GPU）；对dense和MoE两种模型对比；L20集群上额外验证；开源Llama3 8B上验证；资源管理策略对比（3种）。
- **消融实验**：PP-aligned vs DP-aligned vs unaligned；不同模型规模缩放；JCT预测方法对比；NCCL变量对计算核影响。
- **充分性判断**：实验覆盖了从模拟到真实场景、从小规模到超大规模、从私有模型到开源模型、从H800到L20 GPU，对比多个基线。但缺乏更多SOTA调度器的直接对比（如Gandiva、AntMan等曾用于DL但不是LLM特定）；MegaScale内部参数未公开可能不公平，但作者声明相同其他配置。
- **客观性**：指标明确（PetaFlops、加权扩展等），多步稳定测量，有分解分析解释现象。总体充分。

## 6. 主要结论与发现

1. **性能提升显著**：在9600+ GPU上，Arnold相比MegaScale提升端到端训练性能10.6%；208 GPU上提升5.7%。模拟中降低通信组最大扩展最多1.67x。
2. **PP对齐通常更优**：对于dense模型，PP对齐比DP对齐带来更大性能提升（平均2.3%）；对于MoE模型，两者共同优化，PP贡献更大。
3. **模型规模越大收益越明显**：随着模型层数增加，通信占比增大，最优对齐带来的改进持续增加（如2x、3.5x模型规模下改进达3.4%）。
4. **拓扑对齐影响计算核性能**：由于NCCL流与计算流竞争GPU SM，改善通信后可能引起计算核轻微降速，但总体正向。
5. **资源管理有效**：所设计的排队策略和JCT预测可降低保留空闲率，同时保证LPJ按计划获取资源。

## 7. 优点

- **新颖性**：首次针对LLM预训练的特定通信模式（DP组和PP组）提出拓扑感知调度，并明确量化了DP-PP折衷。
- **实用性强**：方法已部署生产环境，与MegaScale等系统兼容且透明给用户，可直接叠加其他优化。
- **算法可扩展**：MIP求解可在秒级完成（1000+节点时），具有在线调度可行性。
- **实验全面**：从个体通信操作性能到端到端训练，从小规模验证到超大规模部署，覆盖多种模型、硬件、网络类型。
- **深度分析**：发现拓扑对齐的副作用（计算核受流竞争影响），促进更全面理解系统行为。

## 8. 不足与局限

- **失败恢复昂贵**：硬件故障时最优放置改变，但迁移代价过高，文中建议提前预留备份节点，但未评估具体实现成本。
- **拓扑普遍性有限**：表征基于CLOS拓扑，其他拓扑（如环型、直连）需重新表征和适配亲和参数。
- **商业敏感数据未开放**：模型大小、训练步数、具体MFU等因业务原因隐藏，部分实验不可完全复现。
- **调度假设强**：假设通信组同质同步（所有PP组同时启动等），若存在资源异构或非同步执行则效果可能下降。
- **对比基线局限**：仅与MegaScale对比，未在模拟中与更多DDL调度器（如Gandiva、Phoebe等）比较；MegaScale本身可能已包含非公开优化。
- **资源管理依赖JCT预测**：GBM预测RMSE 1.61（10分钟区间），但预测误差仍可能导致保留资源浪费或作业冲突，文中未分析长尾情况。

（完）
