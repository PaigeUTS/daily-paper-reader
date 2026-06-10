---
title: "FlashMoE: Fast Distributed MoE in a Single Kernel"
title_zh: "FlashMoE: 快速分布式MoE的单内核实现"
authors: "Osayamen Jonathan Aimuyo, Byungsoo Oh, Rachee Singh"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=EZfDHprhZM"
tags: ["query:agents-os"]
score: 8.0
evidence: 用于分布式训练的GPU驻留MoE算子
tldr: 针对现有MoE分布式训练中GPU利用率低、延迟高的问题，提出FlashMoE，将专家计算和GPU间通信融合为单个持久内核，实现细粒度流水线化调度，消除启动开销，显著提升训练效率。实验表明该方法在多种模型上取得加速，为大规模神经网络训练提供高效算子。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ezfdhprhzm/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1157, \"height\": 758, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ezfdhprhzm/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 721, \"height\": 457, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ezfdhprhzm/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1414, \"height\": 456, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ezfdhprhzm/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1232, \"height\": 391, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ezfdhprhzm/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 876, \"height\": 652, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ezfdhprhzm/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1261, \"height\": 752, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ezfdhprhzm/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1417, \"height\": 458, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ezfdhprhzm/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 630, \"height\": 305, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ezfdhprhzm/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 759, \"height\": 415, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ezfdhprhzm/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1411, \"height\": 455, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ezfdhprhzm/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1417, \"height\": 452, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ezfdhprhzm/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1157, \"height\": 904, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ezfdhprhzm/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1160, \"height\": 1072, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ezfdhprhzm/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 953, \"height\": 919, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ezfdhprhzm/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1169, \"height\": 1287, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ezfdhprhzm/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 650, \"height\": 292, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ezfdhprhzm/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 993, \"height\": 180, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ezfdhprhzm/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1444, \"height\": 288, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ezfdhprhzm/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 755, \"height\": 429, \"label\": \"Table\"}]"
motivation: 现有MoE分布式训练因CPU调度和频繁内核启动导致GPU利用率低、延迟高。
method: 设计完全GPU驻留的MoE算子，将专家计算与跨GPU通信融合为单持久内核，实现细粒度流水线。
result: 在多个大规模模型上显著提升训练吞吐量，降低延迟。
conclusion: FlashMoE消除了调度开销，是一种高效的分布式MoE训练方案。
---

## Abstract
The computational sparsity of Mixture-of-Experts (MoE) models enables sub-linear growth in compute cost as model size increases, thus offering a scalable path to training massive neural networks. However, existing implementations suffer from low GPU utilization, significant latency overhead, and a fundamental inability to leverage task locality, primarily due to CPU-managed scheduling, host-initiated communication, and frequent kernel launches. To overcome these limitations, we develop FlashMoE, a fully GPU-resident MoE operator that fuses expert computation and inter-GPU communication into a single persistent GPU kernel. FlashMoE enables fine-grained pipelining of dispatch, compute, and combine phases, eliminating launch overheads and reducing idle gaps. Unlike existing work, FlashMoE obviates bulk-synchronous collectives for one-sided, device-initiated, inter-GPU (R)DMA transfers, thus unlocking payload efficiency, where we eliminate bloated or redundant network payloads in sparsely activated layers. When evaluated on an 8-H100 GPU node with MoE models having up to 128 experts and 16K token sequences, FlashMoE achieves up to 9× higher GPU utilization, 6× lower latency, 5.7× higher throughput, and 4× better overlap efficiency compared to state-of-the-art baselines—despite using FP32 while baselines use FP16. FlashMoE shows that principled GPU kernel-hardware co-design is key to unlocking the performance ceiling of large-scale distributed ML. We provide code at https://github.com/osayamenja/FlashMoE.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **问题**：现有混合专家（Mixture-of-Experts, MoE）模型在分布式训练中面临严重的性能瓶颈。主要原因是**CPU管理的调度**、**主机发起的通信**以及**频繁的内核启动**，导致GPU利用率低、延迟高、无法利用任务局部性。
- **背景**：MoE通过稀疏激活专家实现模型规模增加时计算成本亚线性增长，但现有实现（如DeepSpeed-MoE、Megatron-LM、COMET等）需要大量内核启动（最多550个GPU操作），且依赖同步的AlltoAll集合通信，易受掉队者影响，产生大量空闲等待。
- **整体目标**：设计一个完全**GPU驻留**的MoE算子，将专家计算和跨GPU通信融合为单个持久内核，消除启动开销，实现细粒度流水线，显著提升性能。

## 2. 论文提出的方法论

### 核心思想
- **完全融合单内核**：将MoE层的门控、分发、专家计算、合并全阶段合并为一个持久GPU内核，仅需一次内核启动。
- **Actor模型**：将GPU线程块和Warp特化为三种角色：
  - **处理器（Processor）**：执行GEMM和元素操作。
  - **调度器（Scheduler）**：分配计算任务给空闲处理器，采用工作守恒、多线程调度。
  - **订阅者（Subscriber）**：解码来自其他GPU的远程数据包，生成任务描述符。
- 除一个线程块作为操作系统（OS）块外，其余均为处理器。OS块内3个Warp为订阅者，1个Warp为调度器。

### 关键技术细节
- **对称张量布局（Symmetric Tensor Layout）**：定义 \( L \in \mathbb{R}^{P \times R \times B \times E \times C \times H} \)，通过时间缓冲（over-provision 4倍）实现完全无阻塞的一侧（R）DMA通信，并证明无写-写冲突。
- **Payload高效通信**：通过就地填充（in-place padding）避免零填充导致的带宽浪费，只传输实际有令牌的专家数据。
- **任务抽象**：统一FFN和专家合并操作，定义任务描述符 \( t = (M, \star, \phi) \)，其中 \( \star \) 为矩阵乘或Hadamard积，\( \phi \) 为激活函数。处理器内融合执行。
- **Tile级并行**：将令牌矩阵划分为 \( 128 \times 64 \) 的tile，平衡寄存器压力与SM占用率。

### 算法流程
- 算法1展示单内核入口：执行融合门控 → 分发令牌 → 启动处理器/OS块。
- 处理器循环：等待调度器任务 → 执行GEMM0/GEMM1/Combine → 通知调度器。
- 调度器循环：扫描调度器及订阅者门铃 → 分发任务。
- 订阅者循环：轮询远程/本地标志 → 解码任务写入队列 → 通知调度器。

## 3. 实验设计

### 数据集/场景
- 使用自定义MoE Transformer模型：16注意力头、嵌入维度2048、FFN中间维度2048。
- 前向单层MoE，评估指标：前向延迟、GPU SM利用率、吞吐量（MTokens/s）、弱扩展重叠效率、专家扩展性。

### Benchmark
- 对比方法：
  - **COMET**（基于cudaMemcpyPeerAsync）
  - **FasterMoE**（基于NCCL）
  - **Megatron-CUTLASS**（Megatron-LM + CUTLASS）
  - **Megatron-TE**（Megatron-LM + Transformer Engine）
  - **DeepEP**（在GPU利用率和内核启动对比中出现）
- 注意：COMET在≥4 GPU时表现异常，因此只在2/4 GPU中比较。

### 实验设置
- 路由方式：top-2，容量因子1.0。
- 序列长度：4K、8K、16K。
- 专家总数：8、16、32、64、128。
- GPU数量：2、4、8。
- 精度：FlashMoE使用FP32（不利条件），基线使用FP16。

## 4. 资源与算力
- **硬件**：单节点8块NVIDIA H100 80G GPU，通过NVLink互连；125GB RAM；20 vCPUs。
- **软件**：PyTorch 2.6.0，CUDA 12.8，Ubuntu 22.04。
- **未明确说明训练时长**，论文仅评估前向推理延迟（平均32次运行）。

## 5. 实验数量与充分性
- **实验组数**：涵盖5个主要维度（前向延迟在4/8 GPU上对3种序列长度；GPU利用率；吞吐量随GPU数变化；弱扩展重叠效率；专家可扩展性），并额外提供内核启动数量对比、内存开销分析等补充实验。
- **充分性**：对比了多个SOTA基线，覆盖不同通信实现（CUDA Peer-to-Peer / NCCL）；在处理精度不公平的情况下（FP32 vs FP16）仍显著领先，增强了说服力；报告了32次运行平均，统计可靠。
- **客观公平**：作者承认FP16路径调优不完善，因此选择FP32作公平竞争，表明性能优势来源于架构而非精度红利。

## 6. 论文的主要结论与发现
- FlashMoE在8×H100上相比SOTA基线，实现：
  - **6×更低延迟**（最高6.4×）
  - **9×更高GPU SM利用率**（93.17% vs 9.67%~59.11%）
  - **5.7×更高吞吐量**（17.7 MTokens/s vs ~3.1 MTokens/s）
  - **4×更好弱扩展重叠效率**（8 GPU时90% vs 22%~48%）
- 即使使用FP32（双倍通信量和计算量），仍大幅超越使用FP16的基线。
- 证明原则性GPU内核-硬件协同设计是解锁大规模分布式ML性能天花板的关键。

## 7. 优点
- **完全消除了CPU调度和内核启动开销**：仅1次内核启动，而基线最多550次。
- **细粒度流水线**：通过Actor模型和Tile级任务调度，实现计算与通信无缝重叠，无需同步屏障。
- **异步设备发起通信**：利用NVSHMEM实现一侧RDMA，避免AlltoAll的同步等待和掉队者问题。
- **Payload高效**：动态路由下只传输有效令牌，避免零填充浪费带宽和计算。
- **原型公开**：代码开源，便于复现和二次开发。

## 8. 不足与局限
- **工程复杂度高**：需要深厚的GPU+分布式系统专家知识，编译器/DSL抽象可降低门槛（作者自述）。
- **FP16路径效率低**：因调优不完善，共享内存布局导致指令数翻倍，未充分利用半精度优势，遗憾未能在等精度下直接比较。
- **仅支持推理**：当前仅实现前向传播，不支持训练（反向和梯度通信尚未融合）。
- **内存开销**：对称张量布局约增加4倍令牌缓冲区，虽然占模型总内存≤2%，但对极大规模模型仍可能构成限制。
- **跨节点验证缺失**：实验仅在单节点8 GPU（NVLink）上进行，未涉及多节点Infiniband场景，虽然作者推测收益更大，但尚无实验证据。
- **超参数敏感**：Tile维度（128×64）需精细调参，不具普适性，可能需针对不同模型重新搜索。

（完）
