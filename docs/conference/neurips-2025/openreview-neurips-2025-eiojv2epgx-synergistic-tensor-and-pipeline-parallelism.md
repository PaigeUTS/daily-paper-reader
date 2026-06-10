---
title: Synergistic Tensor and Pipeline Parallelism
title_zh: 协同张量并行与流水线并行
authors: "Mengshi Qi, Jiaxuan Peng, Jie Zhang, Juan Zhu, Yong Li, Huadong Ma"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=eIojV2epgX"
tags: ["query:agents-os"]
score: 7.0
evidence: 大模型训练的并行调度
tldr: 针对混合并行方案中张量并行通信开销大和流水线并行气泡问题，本文提出一种协同调度策略，通过解耦前向后向传播同时减少两类空闲时间。在LLM训练实验中，该方法显著提升了吞吐量，且无需修改硬件。该工作为高效大规模模型分布式训练提供了实用方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-eiojv2epgx/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1132, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eiojv2epgx/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1304, \"height\": 292, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eiojv2epgx/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1441, \"height\": 528, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eiojv2epgx/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1427, \"height\": 350, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eiojv2epgx/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1438, \"height\": 291, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eiojv2epgx/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1338, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eiojv2epgx/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1416, \"height\": 805, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eiojv2epgx/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1447, \"height\": 482, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eiojv2epgx/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1019, \"height\": 363, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eiojv2epgx/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1309, \"height\": 414, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eiojv2epgx/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1136, \"height\": 983, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eiojv2epgx/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1421, \"height\": 955, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-eiojv2epgx/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1102, \"height\": 496, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-eiojv2epgx/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1426, \"height\": 223, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eiojv2epgx/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1349, \"height\": 775, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eiojv2epgx/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1292, \"height\": 944, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eiojv2epgx/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 980, \"height\": 515, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eiojv2epgx/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1084, \"height\": 1213, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eiojv2epgx/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1097, \"height\": 1221, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eiojv2epgx/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1145, \"height\": 498, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eiojv2epgx/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1427, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eiojv2epgx/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 891, \"height\": 433, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-eiojv2epgx/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1066, \"height\": 264, \"label\": \"Table\"}]"
motivation: 现有混合并行方案孤立优化张量并行或流水线并行，未能协同减少通信和气泡开销。
method: 提出一种协同调度，解耦前向和后向传播，同时减少通信等待和流水线气泡。
result: 在大规模LLM训练中验证了吞吐量提升，优于单独优化方案。
conclusion: 该协同并行策略为高效训练提供了可行的调度方法。
---

## Abstract
In the machine learning system, the hybrid model parallelism combining tensor parallelism (TP) and pipeline parallelism (PP) has become the dominant solution for distributed training of Large Language Models~(LLMs) and Multimodal LLMs (MLLMs). However, TP introduces significant collective communication overheads, while PP suffers from synchronization inefficiencies such as pipeline bubbles. Existing works primarily address these challenges from isolated perspectives, focusing either on overlapping TP communication or on flexible PP scheduling to mitigate pipeline bubbles. In this paper, we propose a new synergistic tensor and pipeline parallelism schedule that simultaneously reduces both types of bubbles. Our proposed schedule decouples the forward and backward passes in PP into fine-grained computation units, which are then braided to form a composite computation sequence. This compositional structure enables near-complete elimination of TP-related bubbles. Building upon this structure, we further design the PP schedule to minimize PP bubbles. Experimental results demonstrate that our approach improves training throughput by up to 12\% for LLMs and 16\% for MLLMs compared to existing scheduling methods. Our source code is avaiable at https://github.com/MICLAB-BUPT/STP.

---

## 论文详细总结（自动生成）

# 中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：在大型语言模型（LLM）和多模态大模型（MLLM）的分布式训练中，混合并行策略（张量并行 TP + 流水线并行 PP）已成为主流方案。然而，两者各自存在严重效率问题：TP 引入大量集体通信（All-Reduce）开销，形成“TP 气泡”（TP bubble），且随 TP 规模增大而显著增长；PP 则面临同步低效导致的“PP 气泡”（pipeline bubble）。现有工作大多孤立地优化其中一个方面，未充分利用二者协同潜力。
- **整体含义**：本文旨在提出一种新的协同调度策略，同时减少 TP 气泡和 PP 气泡，从而提升混合并行训练的整体吞吐量。该工作为大规模模型训练提供了更高效、更实用的调度方案。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：将 PP 中每个阶段的 Transformer 层的前向和反向传播解耦为细粒度计算单元，并将这些单元交错编织成“编织执行块”（braided execution block），使得 TP 通信可以与该块内的后续计算重叠，从而几乎完全消除 TP 气泡。在此基础上，设计一种低气泡率的 PP 调度，采用“V”形数据流以实现跨阶段均衡的内存占用和更低的 PP 气泡。
- **关键技术细节**：
  - **细粒度单元分解**：将 Transformer 层内的前向计算分解为 Pre-Attn、Attn、Pre-MLP、MLP 四个单元；反向计算进一步拆分为激活梯度计算和权重梯度计算（借鉴 Zero Bubble）。
  - **编织执行块（图3）**：将前向单元与反向单元交错排列，使得前向中的 TP 通信（All-Reduce）能与反向的权重梯度计算并行执行，实现重叠。两种块类型：
    - 类型 (a)：前向 + 完整反向（无权重分离），自然重叠反向 TP 通信。
    - 类型 (b)：前向 + 激活反向（分离权重），后续前向单元填充额外气泡。
  - **PP 调度（图5）**：
    - 采用“V”形数据流均衡各阶段峰值内存。
    - 虚拟阶段（virtual stage）策略：每个设备分配两个虚拟阶段，使得前向和后向单元可以跨不同微批次交织。
    - 三阶段执行：预热阶段（最大化在途微批次数量，启动编织块）、稳态阶段（保持 F&B 重叠）、冷却阶段（完成剩余反向）。
    - 权重分离的激活：在稳态阶段将激活及时卸载到 CPU，避免内存堆积；冷却阶段再加载。
  - **公式修改**：将残差连接融合到 Attn 和 MLP 的前向计算中，避免额外的数据依赖，保持计算等价。
- **理论分析（表1）**：对比 1F1B-I、ZB-V 和本方法的 PP 气泡、TP 气泡和峰值激活内存的理论大小。本方法在相近的 PP 气泡下，TP 气泡显著小于 ZB-V（(2p+1)*T_AR vs 4*m*T_AR），峰值内存略高但可通过卸载降低。

## 3. 实验设计：数据集/场景、benchmark、对比方法

- **数据集/场景**：不是使用特定公开数据集，而是以 Qwen2（LLM）和 Qwen2-VL（MLLM）为模型进行分布式训练性能评估。场景包括不同的模型规模（12.1B、26.3B LLM；14.9B、28.8B+ MLLM）、序列长度（2048～8192）、TP 规模（2/4/8）、PP 规模（2/4/8）以及微批次数量（64～256）。
- **Benchmark**：吞吐量（samples/s）、峰值激活内存（GB）、Model FLOPs Utilization (MFU)。
- **对比方法**：
  - 1F1B-I（Megatron-LM 中的交错 1F1B）
  - ZB-V（Zero Bubble V，具有“V”形数据流）
  - 本文所提方法（Ours），以及增强变体（带激活卸载）

## 4. 资源与算力

- **实验使用的 GPU**：
  - 主要实验：高达 32 块 NVIDIA A800 SXM4 80GB GPU，分布在 4 个节点。
  - 部分实验（增强变体、最大化资源利用）：16 块 NVIDIA H20 96GB GPU（配备 PCIe Gen 5）。
- **训练时长**：未明确报告具体训练小时数，仅说明经过数次 warm-up 迭代后记录稳定结果。
- **其他细节**：使用 Flash Attention 2，基于开源 Megatron-Core 项目实现。

## 5. 实验数量与充分性

- **实验组数**：
  - **LLM 实验（图7、8，表5、6、7）**：覆盖 2 种模型规模（12.1B、26.3B），2 种序列长度（2048/3072、4096/6144），4 种并行配置（TP×PP 组合），3 种微批次数量（64/128/192 或 96/176/256）。每个配置测试三种调度方法，共约 48 组主要对比实验。
  - **MLLM 实验（表3）**：2 种模型规模（14.9B、28.8B），不同 ViT 和 LM 长度组合，3 种 PP 配置，多组微批次。共约 18 组实验。
  - **增强变体实验（图10、表4）**：在 H20 上测试卸载方案的吞吐与内存，以及与最大化资源利用的对比。
  - **消融与兼容性实验（附录 E、F）**：激活检查点兼容性、数据并行/上下文并行兼容性、重叠对 GEMM 效率影响的微基准测试。
- **充分性与公平性**：
  - 实验覆盖多种模型规模、序列长度、并行配置，以及 LLM 和 MLLM 两种类型，具有较好代表性。
  - 所有对比方法使用相同的虚拟阶段数（2 个/设备），基于相同开源代码基实现，保证了公平。
  - 提供了理论分析（表1）与实验结果的相互验证。
  - 不足：未在更大规模（如 100B+ 模型）或更多 GPU（如 64+）上验证；未报告多次运行的误差棒（稳定性声明但未显示统计量）。

## 6. 论文的主要结论与发现

- 本文提出的协同调度策略在 LLM 训练中相比 1F1B-I 最高提升 12.2% 吞吐量（TP=8, PP=2, seq=6144 场景），在 MLLM 训练中最高提升 16.7%（PP=2 不平衡负载场景）。
- TP 规模越大、序列越长，本方法优势越明显；PP 规模较大时优势相对降低（但仍优于基线）。
- ZB-V 由于暴露了原本在 1F1B-I 中可重叠的 TP 通信，实际性能常不及甚至持平 1F1B-I。
- 增强变体（激活卸载）可在吞吐损失极小的情况下降低峰值内存 10%~19.2%，适用于内存受限场景。
- 在最大化资源利用（H20，大微批次）时，本方法在 MFU 和吞吐上均优于基线，且内存更均衡。

## 7. 优点：方法或实验设计上的亮点

- **协同优化视角**：同时针对 TP 和 PP 气泡进行调度级重叠，而非孤立优化。
- **细粒度编织块设计**：通过软件层解耦计算单元实现通信重叠，无需修改底层 CUDA kernel 或硬件，用户友好。
- **“V”形数据流**：均衡各阶段峰值内存，避免 1F1B-I 中首设备内存瓶颈。
- **理论分析完善**：给出各类气泡和峰值内存的理论公式，与实验结果一致。
- **实验全面**：覆盖 LLM 和 MLLM 两大模型类型，多种并行规模，且含增强变体与兼容性验证。

## 8. 不足与局限

- **峰值内存偏高**：本方法在标准调度下峰值内存高于 1F1B-I 和 ZB-V（表1），需借助卸载或检查点缓解，但卸载依赖高带宽互联（如 PCIe Gen 5）。
- **PP 规模较大时收益下降**：由于显式管道通信无法被重叠，PP=8 场景下提升幅度减小。
- **实验规模有限**：最大仅用 32 GPU，未在更大集群（如 64+ GPU）或更大模型（>100B）上验证。
- **工程实现开销**：细粒度单元解耦和权重分离带来额外的实现复杂性和潜在内存管理开销。
- **未报告统计误差**：虽然声称结果稳定，但未提供多次运行的标准差或置信区间。
- **MLLM 的不平衡负载**：当 ViT 与 LM 计算量差异大时，需人工调整虚拟阶段分配，可能增加部署复杂度。

（完）
