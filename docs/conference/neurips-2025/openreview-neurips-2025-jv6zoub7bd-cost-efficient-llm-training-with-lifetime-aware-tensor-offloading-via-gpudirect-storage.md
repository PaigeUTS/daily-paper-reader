---
title: Cost-Efficient LLM Training with Lifetime-Aware Tensor Offloading via GPUDirect Storage
title_zh: TERAIO：基于生命周期感知和张量卸载的高性价比大模型训练
authors: "Ziqi Yuan, Haoyang Zhang, Yirui Eric Zhou, Apoorve Mohan, I-Hsin Chung, Seetharami Seelam, Jian Huang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=JV6ZOUb7BD"
tags: ["query:agents-os"]
score: 7.0
evidence: 利用SSD进行张量生命周期感知卸载，实现异构存储下的大模型低成本训练
tldr: 大模型训练中GPU内存紧张，大量张量长期闲置。TERAIO利用GPUDirect Storage将非活跃张量卸载到SSD，精确估计生命周期以避免训练停滞。实验表明该方法以较低成本扩展了可用显存，为异构计算环境下的大模型训练提供了高效的内存管理方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-jv6zoub7bd/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1398, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jv6zoub7bd/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1444, \"height\": 313, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jv6zoub7bd/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 480, \"height\": 351, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jv6zoub7bd/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1296, \"height\": 403, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jv6zoub7bd/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1166, \"height\": 311, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jv6zoub7bd/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 724, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jv6zoub7bd/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 526, \"height\": 335, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jv6zoub7bd/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1453, \"height\": 620, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jv6zoub7bd/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1443, \"height\": 268, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jv6zoub7bd/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 793, \"height\": 294, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jv6zoub7bd/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1448, \"height\": 681, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-jv6zoub7bd/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1433, \"height\": 278, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-jv6zoub7bd/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 338, \"height\": 130, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jv6zoub7bd/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 561, \"height\": 200, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jv6zoub7bd/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1110, \"height\": 219, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-jv6zoub7bd/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1458, \"height\": 389, \"label\": \"Table\"}]"
motivation: GPU显存有限，SSD成本低但延迟高，需智能卸载以降低训练成本。
method: 提出生命周期感知的张量卸载框架，利用GPUDirect Storage在SSD与GPU间高效迁移数据。
result: 显著降低显存占用，训练大模型时成本减少且吞吐量损失小。
conclusion: 利用异构存储可有效支撑大模型训练，降低成本。
---

## Abstract
We present the design and implementation of a new lifetime-aware tensor offloading
framework for GPU memory expansion using low-cost PCIe-based solid-state
drives (SSDs). Our framework, TERAIO, is developed explicitly for large language
model (LLM) training with multiple GPUs and multiple SSDs. Its design is driven
by our observation that the active tensors take only a small fraction (1.7% on
average) of allocated GPU memory in each LLM training iteration, the inactive
tensors are usually large and will not be used for a long period of time, creating
ample opportunities for offloading/prefetching tensors to/from slow SSDs without
stalling the GPU training process. TERAIO accurately estimates the lifetime (active
period of time in GPU memory) of each tensor with the profiling of the first few
iterations in the training process. With the tensor lifetime analysis, TERAIO will
generate an optimized tensor offloading/prefetching plan and integrate it into the
compiled LLM program via PyTorch. TERAIO has a runtime tensor migration
engine to execute the offloading/prefetching plan via GPUDirect storage, which
allows direct tensor migration between GPUs and SSDs for alleviating the CPU
bottleneck and maximizing the SSD bandwidth utilization. In comparison with
state-of-the-art studies such as ZeRO-Offload and ZeRO-Infinity, we show that
TERAIO improves the training performance of various LLMs by 1.47× on average,
and achieves 80.7% of the ideal performance assuming unlimited GPU memory.

---

## 论文详细总结（自动生成）

# 中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **问题**：大语言模型（LLM）训练对GPU显存的需求增长远快于GPU显存扩展速度，导致显存成为瓶颈。扩展GPU显存技术困难且成本高昂（DRAM每GB约4美元），而通过集群扩展增加成本。
- **现有方案不足**：现有张量卸载方案（如ZeRO-Offload、ZeRO-Infinity）使用CPU内存或SSD扩展显存，但存在粗粒度卸载、I/O带宽利用率低、依赖CPU瓶颈等问题，导致训练性能远低于理想情况。
- **核心观察**：LLM训练中，活跃张量仅占平均1.7%的显存，非活跃张量大且长时间（>10^4微秒）不被使用，提供了充分的卸载/预取机会。利用低成本PCIe SSD（约0.2美元/GB）扩展显存具有可行性，且32-48 GB/s的聚合SSD带宽即可接近理想性能。

## 2. 方法论
- **核心思想**：基于张量生命周期（活跃/非活跃周期）的精确感知，实现细粒度、I/O带宽感知的卸载/预取调度，最大化计算与数据迁移的重叠，避免GPU停滞。
- **三大组件**：
  - **张量生命周期剖析器**：在训练前几个迭代中，通过插桩PyTorch自动算子生成器，收集张量大小、活跃/非活跃时间（根据GPU内核执行时间计算）。无需修改模型代码。
  - **生命周期感知的迁移算法**：迭代选择最佳卸载候选，直到GPU显存需求低于容量。优先卸载大且非活跃期长的张量。算法跟踪I/O带宽使用，计算实际可卸载/预取的时间窗口。定义“关键内存压力”区域（超过容量的部分），收益为该区域积分，成本为卸载+预取时间，按收益/成本比排序。卸载目标首选SSD，SSD带宽饱和时使用CPU内存（用户可设上限）。若仍不足，则阻塞GPU内核等待紧急迁移。
  - **运行时迁移引擎（GPUDirect Storage）**：利用GPUDirect Storage实现GPU与SSD之间的直接数据传输，绕过CPU，避免主机内存瓶颈和CPU资源竞争。维护哈希表跟踪张量位置。紧急迁移优先级最高。
- **算法流程**：剖析→生成迁移计划→编译执行（指令集成到PyTorch执行图）→运行时按计划执行迁移。

## 3. 实验设计
- **数据集**：C4训练数据集。
- **模型**：Llama3-8B、Llama3-70B、Granite-code-base-8B（以及表征分析中的GPT2-40B、T5-11B）。
- **基准方法**：
  - Ideal（假设无限GPU显存，理论最优）
  - ZeRO-Offload（仅卸载到CPU内存）
  - ZeRO-Infinity（卸载到CPU和SSD）
  - TERAIO-SSD（仅使用SSD）
  - TERAIO-Mixed（同时使用SSD和CPU内存，CPU内存容量与ZeRO-Infinity一致）
- **评估场景**：不同batch size（16-128）和sequence length（1024-8192）组合；不同SSD数量（2-4）、CPU内存容量（16GB-1TB）。

## 4. 资源与算力
- **硬件配置**：
  - GPU：2×NVIDIA H100 NVL，每GPU 94GB HBM
  - CPU：2×AMD EPYC 9334，1.5TB DDR5
  - 互连：PCIe Gen5
  - SSD：8×Samsung 990 PRO 2TB，每SSD读/写6.7/6.5 GB/s，实验中以RAID-0每GPU连接4个SSD（约16 GB/s）
- **软件**：PyTorch 2.5.0、TorchTitan、全精度训练（非混合精度以避免不公平比较）。
- **编译时间**：Llama3-8B约31s，Granite-8B约38s，Llama3-70B约397s。未报告总训练时长（仅报告吞吐量token/s）。

## 5. 实验数量与充分性
- **实验数量**：涵盖3个主要模型（8B、8B、70B）、多种batch size/sequence length组合，每个组合运行并报告平均吞吐量。另包括：延迟分解（计算/重叠/停滞）、存储器带宽利用率、成本分析、SSD/CPU容量消融实验。
- **充分性与公平性**：
  - 对比ZeRO系列时，调整了关键参数（如pipeline_read/write、buffer大小）以达到最佳性能；使用tensor parallelism保证公平。
  - 禁用activation checkpointing以避免ZeRO吞吐受损。
  - 使用全精度训练，避免混合精度导致的显存需求差异。
  - 实验覆盖了不同显存压力（M从187%到1242%），验证了方法在不同规模下的有效性。
  - 未报告多次运行误差棒（因训练成本高），但通过多模型、多配置的一致性结果支持结论。
- **消融实验**：
  - TERAIO-SSD vs TERAIO-Mixed（验证CPU内存的补充作用）
  - 不同SSD数量（2、3、4）和CPU内存容量（16GB-1TB）对吞吐量的影响

## 6. 主要结论与发现
- **性能提升**：TERAIO平均比ZeRO-Offload和ZeRO-Infinity提升1.47倍吞吐量，达到理想性能的80.7%。
- **成本效率**：相比纯GPU方案（8×H100服务器），TERAIO成本降低5.41-5.88倍；相比ZeRO系列，成本效率提升1.45倍。
- **细粒度卸载优势**：基于张量生命周期的细粒度卸载比ZeRO-Infinity的粗粒度层级卸载更高效，I/O带宽利用率更高，GPU停滞时间更少。
- **GPUDirect Storage作用**：显著降低CPU使用率（平均降低12.3% CPU使用率，97.4%内存带宽），避免主机成为瓶颈。
- **硬件需求**：仅需2个SSD（约12-16 GB/s带宽）即可为Llama3-8B达到近理想性能；对于Llama3-70B，4 SSD+适量CPU内存表现优于ZeRO-Infinity。

## 7. 优点
- **轻量且透明**：仅需前几个迭代的剖析，无需修改模型代码；与PyTorch无缝集成。
- **I/O带宽感知的全局优化**：量化卸载收益（关键压力积分）与成本，按收益/成本比贪心选择，优于启发式方法。
- **GPUDirect Storage利用**：消除CPU bounce buffer，提升扩展性，降低主机资源消耗。
- **灵活的多层存储**：优先SSD，可回退到CPU内存，用户可控制CPU内存使用上限。
- **强验证**：在多种模型规模（8B-70B）、序列长度、硬件配置下均优于SOTA，且成本优势显著。

## 8. 不足与局限
- **实验覆盖**：仅使用2个GPU（H100），未在多GPU集群（如8 GPU）上进行扩展性测试。尽管提到GDS的可扩展优势，但缺乏实际多节点验证。
- **偏差风险**：仅评估了Llama、Granite系列，未覆盖其他架构（如T5、GPT2在表征分析中出现，但未作为主要性能基准）。可能不适用于非Transformer模型。
- **应用限制**：当前实现依赖NVIDIA cuFile和主机文件系统（仍需要CPU参与元数据操作），未完全实现GPU发起存储访问（如BAM、GoFS）。未来工作可优化。
- **编译开销**：对于超大规模模型（如70B），编译时间接近7分钟，虽然是一次性开销，但在快速迭代场景中可能带来负担。
- **未考虑混合精度**：为公平对比禁用混合精度，但在实际训练中混合精度普遍使用，可能影响显存容量和卸载策略的适用性。
- **未报告方差**：未提供多次运行的吞吐量误差棒或置信区间，统计显著性不明。
- **硬件限制**：实验PCIe插槽有限（最多8 SSD），实际大规模部署可能需要更多SSD或NVLink-C2C等高速互联，但论文未讨论这些场景下的适配。

（完）
