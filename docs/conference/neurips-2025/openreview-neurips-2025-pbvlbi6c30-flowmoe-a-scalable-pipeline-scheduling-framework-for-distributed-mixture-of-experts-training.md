---
title: "FlowMoE: A Scalable Pipeline Scheduling Framework for Distributed Mixture-of-Experts Training"
title_zh: "FlowMoE: 分布式混合专家训练的可扩展流水线调度框架"
authors: "Yunqi Gao, Bing Hu, Mahdi Boloursaz Mashhadi, A-Long Jin, Yanfeng Zhang, Pei Xiao, Rahim Tafazolli, Merouane Abdelkader DEBBAH"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=PBvlBI6c30"
tags: ["query:agents-os"]
score: 8.0
evidence: 分布式MoE的多类型任务流水线调度
tldr: 现有分布式MoE训练调度仅关注专家计算和A2A通信，忽略注意力和门控等操作。本文提出FlowMoE，统一调度多类型任务流水线，显著提升吞吐量和可扩展性，支持更大规模模型训练，对异构计算基础设施设计有启示。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-pbvlbi6c30/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1179, \"height\": 217, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-pbvlbi6c30/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1449, \"height\": 506, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-pbvlbi6c30/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1029, \"height\": 207, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-pbvlbi6c30/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 489, \"height\": 210, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-pbvlbi6c30/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1454, \"height\": 537, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-pbvlbi6c30/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1141, \"height\": 352, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-pbvlbi6c30/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1042, \"height\": 583, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-pbvlbi6c30/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1170, \"height\": 335, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-pbvlbi6c30/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1426, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pbvlbi6c30/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 688, \"height\": 461, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pbvlbi6c30/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 835, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pbvlbi6c30/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1461, \"height\": 632, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pbvlbi6c30/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1432, \"height\": 304, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pbvlbi6c30/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1451, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pbvlbi6c30/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1346, \"height\": 1056, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pbvlbi6c30/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1443, \"height\": 502, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pbvlbi6c30/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1283, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pbvlbi6c30/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1435, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pbvlbi6c30/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1371, \"height\": 383, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pbvlbi6c30/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1404, \"height\": 105, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pbvlbi6c30/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1213, \"height\": 377, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pbvlbi6c30/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1076, \"height\": 590, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pbvlbi6c30/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1032, \"height\": 417, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pbvlbi6c30/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1435, \"height\": 243, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pbvlbi6c30/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1432, \"height\": 157, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-pbvlbi6c30/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1434, \"height\": 263, \"label\": \"Table\"}]"
motivation: 现有分布式MoE训练调度忽略多类型操作，导致效率瓶颈。
method: 提出可扩展流水线调度框架，统一调度专家计算、注意力、门控等操作。
result: 显著提升训练吞吐量，降低通信开销，支持更大规模MoE模型。
conclusion: FlowMoE为分布式MoE训练提供了更全面的调度优化。
---

## Abstract
The parameter size of modern large language models (LLMs) can be scaled up to the trillion-level via the sparsely-activated Mixture-of-Experts (MoE) technique to avoid excessive increase of the computational costs. To further improve training efficiency, pipelining computation and communication has become a promising solution for distributed MoE training. However, existing work primarily focuses on scheduling tasks within the MoE layer, such as expert computing and all-to-all (A2A) communication, while neglecting other key operations including multi-head attention (MHA) computing, gating, and all-reduce communication. In this paper, we propose FlowMoE, a scalable framework for scheduling multi-type task pipelines. First, FlowMoE constructs a unified pipeline to consistently scheduling MHA computing, gating, expert computing, and A2A communication. Second, FlowMoE introduces a tensor chunk-based priority scheduling mechanism to overlap the all-reduce communication with all computing tasks. We implement FlowMoE as an adaptive and generic framework atop PyTorch. Extensive experiments with 675 typical MoE layers and four real-world MoE models across two GPU clusters demonstrate that our proposed FlowMoE framework outperforms state-of-the-art MoE training frameworks, reducing training time by14%-57%, energy consumption by 10%-39%, and memory usage by 7%-32%. FlowMoE’s code is anonymously available at https://anonymous.4open.science/r/FlowMoE.

---

## 论文详细总结（自动生成）

### 1. 核心问题与整体含义
- **背景**：现代大型语言模型（LLM）通过稀疏激活的混合专家（MoE）技术实现参数规模扩展，同时控制计算成本。分布式MoE训练中，流水线化计算与通信是提升效率的关键。
- **问题**：现有调度工作（如ScheMoE、Tutel、FasterMoE）仅专注MoE层内部的任务（专家计算、All-to-All通信），忽略了Transformer块中的**多头注意力（MHA）计算、门控（gating）操作以及全规约（All-Reduce）通信**，这些被忽略的任务占单次迭代时间的**30%~40%**（见表1），成为性能瓶颈。
- **整体含义**：本文提出FlowMoE，通过统一调度多类型任务（MHA计算、门控、专家计算、A2A通信、All-Reduce通信）最大化计算与通信重叠，显著提升分布式MoE训练的可扩展性和效率。

### 2. 方法论
- **核心思想**：构建一个统一的流水线调度框架，覆盖整个Transformer块的所有主要计算和通信任务，并利用**优先级调度机制**进一步重叠All-Reduce通信。
- **关键技术细节**：
  - **统一流水线**：将输入张量划分为R个微批次，将MHA计算、门控、专家计算、A2A通信（dispatch/combine）均按R部分切分，并按照依赖关系重新排序（见式2-5），实现前向和反向传播中计算与通信的重叠（图2e-2f）。
  - **All-Reduce优先级调度**：在反向传播中，将All-Reduce通信张量切分为**小块**，放入通信任务池，并设置其优先级低于A2A通信任务。这样，All-Reduce块可以无缝填充A2A通信之间的空闲间隙，最大化重叠（算法2）。
  - **贝叶斯优化（BO）自动调参**：使用BO自动搜索最优的All-Reduce块大小 \( S_p \)，以平衡重叠增益和启动开销（定理2说明 \( S_p \to 0 \) 理论上最优，但实际需考虑开销）。BO通过少量采样（通常8次）即可找到近优值（图4）。
- **算法流程文字描述**：
  - **前向**：依次调度 \( AT^{(l)}_1 \to ... \to AT^{(l)}_R \to E^{(l)}_1 \to ... \to E^{(l)}_R \)，A2A通信任务穿插进行。
  - **反向**：顺序相反，并插入All-Reduce块通信。
  - 通信池管理线程始终优先执行A2A通信，空闲时执行All-Reduce块通信。

### 3. 实验设计
- **数据集**：
  - OpenWebText（语言建模）
  - Wikitext-103（文本生成）
- **MoE基准模型**：
  - 自定义MoE层（675种配置，覆盖不同B, N, M, H, f等）
  - 四个真实世界MoE模型：GPT2-Tiny-MoE, BERT-Large-MoE, LLaMA2-MoE, DeepSeek-V2-S（配置见表2）
  - 两个扩展模型（压力测试）：LLaMA2-MoE-L, DeepSeek-V2-M
- **对比方法**：vanillaEP（原始专家并行）、FasterMoE、Tutel、ScheMoE、FSMoE。所有方法使用官方实现，流水线度R=2（除非特别说明）。
- **评估指标**：平均每迭代时间、加速比、能耗（NVIDIA SMI）、内存使用。

### 4. 资源与算力
- **集群1**：2节点，每节点8×NVIDIA RTX3090（24GB显存），100Gb/s网络，CPU Intel Xeon Gold 6248R。
- **集群2**：4节点，每节点2×NVIDIA RTX2080Ti（12GB显存），10Gb/s网络。
- **训练时长**：论文未报告总训练时间，但给出了不同模型在16 GPU（集群1）上的平均迭代时间（如DeepSeek-V2-S：3205.3ms），并基于1000次迭代取平均。

### 5. 实验数量与充分性
- **数量丰富**：
  - 端到端时间对比：4个模型 × 4种GPU规模（4/8/16）共12组主要实验（表3）。
  - 自定义MoE层：490个有效用例（集群1，16 GPU）+ 393个（集群2，8 GPU），全部优于ScheMoE（图6）。
  - 消融实验：逐步加入Pipe-AT、Pipe-AR、BO，清晰展示各组件贡献（表5）。
  - 流水线度影响：3种R值对比（表4）。
  - 能耗与内存对比（表6）。
  - 收敛性验证（图A.2）。
  - 压力测试（表A.7）、异构鲁棒性（表A.12）、多专家/容量因子对SM利用率影响（表A.11）等。
- **充分性与公平性**：所有实验统一基线，使用相同的模型配置和随机种子；对比框架均使用官方实现；多次迭代取平均降低噪声；已考虑GPU SM利用率、计算开销等细节。实验设计客观全面。

### 6. 主要结论与发现
- **性能提升**：FlowMoE相比SOTA框架（ScheMoE等）**降低训练时间13%~57%**，节省能耗10%~39%，内存7%~32%。
- **具体加速比**：相对于vanillaEP达1.43×~1.82×；相对于ScheMoE在自定义层上平均**26%**；在真实模型上1.13×~1.31×。
- **统一调度有效**：消融实验证明，同时纳入MHA/门控和All-Reduce管道化，可额外获得高达40%的改进（表5）。
- **BO自动调优关键**：相比固定分块或随机生成，BO显著提升性能（表A.3, A.4）。

### 7. 优点
- **创新性**：首次提出对Transformer块中所有主要任务（MHA、门控、专家、两种通信）进行统一流水线调度，而非仅局限在MoE层内部。
- **理论支撑**：给出定理证明（定理1、2），说明插入All-Reduce任务可降低反向传播时间，且极致细粒度切分可最小化迭代时间。
- **自适应性**：通过贝叶斯优化自动搜索最优All-Reduce块大小，无需人工调参，适应不同硬件和模型。
- **系统实现**：基于PyTorch和Tutel，易于集成；代码开源；提供通信任务优先级管理机制，实现灵活调度。
- **实验充分**：覆盖大量配置、多个模型、两个异构集群，并包含消融、收敛、鲁棒性等全面分析。
- **综合指标优化**：同时降低时间、能耗和内存，实用性高。

### 8. 不足与局限
- **实验覆盖**：未测试**万亿参数级**模型（如Switch Transformer 1.5T）或**超大规模集群**（数百GPU以上）；论文中最大GPU数为16，可能无法完全反映极端可扩展性。
- **动态环境适应**：虽然提出了重调机制，但未深入讨论频繁变化场景（如链路抖动）下的开销。
- **资源竞争假设**：假设同一GPU上计算与通信可并行，但多个通信或计算不能重叠，实际中某些硬件可能支持更细粒度的并发。
- **启动开销简化**：定理2假设无启动开销，实际中BO调参仅能逼近最优，且BO自身有少量计算开销（占总训练时间0.16%~3.22%）。
- **鲁棒性有限**：异构集群实验仅通过模拟计算能力降低（延迟注入）来验证，未涉及真实异构混合GPU（如A100+RTX）环境。
- **内存优化来源**：FlowMoE因及时执行All-Reduce而减少梯度缓存，但未探讨其他内存优化技术（如重计算、卸载），在极端内存受限场景下可能仍需额外手段。

（完）
