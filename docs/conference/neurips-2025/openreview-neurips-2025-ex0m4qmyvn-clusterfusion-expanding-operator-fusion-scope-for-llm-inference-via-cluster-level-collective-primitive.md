---
title: "ClusterFusion: Expanding Operator Fusion Scope for LLM Inference via Cluster-Level Collective Primitive"
title_zh: ClusterFusion：通过集群级集体原语扩展LLM推理的算子融合范围
authors: "Xinhao Luo, Zihan Liu, Yangjie Zhou, Shihan Fang, Ziyu Huang, Yu Feng, Chen Zhang, Shixuan Sun, Zhenzhe Zheng, Jingwen Leng, Minyi Guo"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=eX0m4qMYVN"
tags: ["query:agents-os"]
score: 7.0
evidence: 面向异构硬件的集群级通信原语用于LLM推理
tldr: LLM推理中算子执行碎片化导致高延迟和内存流量。本文利用现代架构的分布式共享内存和低延迟互连，提出集群级通信原语ClusterReduce和ClusterGather，扩展算子融合范围。该方法减少了内存流量和内核启动开销，为异构计算基础设施上的LLM推理优化提供了新途径。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 808, \"height\": 243, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 558, \"height\": 279, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1455, \"height\": 595, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 388, \"height\": 277, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 978, \"height\": 259, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1442, \"height\": 231, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1452, \"height\": 572, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 692, \"height\": 288, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 517, \"height\": 320, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 691, \"height\": 287, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 407, \"height\": 267, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 813, \"height\": 308, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 559, \"height\": 322, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1441, \"height\": 599, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1457, \"height\": 439, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1452, \"height\": 601, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 705, \"height\": 288, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 810, \"height\": 306, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 704, \"height\": 288, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ex0m4qmyvn/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 548, \"height\": 303, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ex0m4qmyvn/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 845, \"height\": 305, \"label\": \"Table\"}]"
motivation: 现有LLM推理算子执行碎片化，内存流量和延迟高。
method: 提出集群级集体通信原语ClusterReduce和ClusterGather，扩展算子融合。
result: 显著降低了内存流量和推理延迟。
conclusion: 集群级原语是优化异构计算基础设施上LLM推理的关键技术。
---

## Abstract
Large language model (LLM) decoding suffers from high latency due to fragmented execution across operators and heavy reliance on off-chip memory for data exchange and reduction. 
This execution model limits opportunities for fusion and incurs significant memory traffic and kernel launch overhead.
While modern architectures such as NVIDIA Hopper provide distributed shared memory and low-latency intra-cluster interconnects, they expose only low-level data movement instructions, lacking structured abstractions for collective on-chip communication.
To bridge this software-hardware gap, we introduce two cluster-level communication primitives, ClusterReduce and ClusterGather, which abstract common communication patterns and enable structured, high-speed data exchange and reduction between thread blocks within a cluster, allowing intermediate results to be on-chip without involving off-chip memory.
Building on these abstractions, we design ClusterFusion, an execution framework that schedules communication and computation jointly to expand operator fusion scope by composing decoding stages such as QKV Projection, Attention, and Output Projection into a single fused kernels.
Evaluations on H100 GPUs show that ClusterFusion outperforms state-of-the-art inference frameworks by $1.61\times$ on average in end-to-end latency across different models and configurations.

---

## 论文详细总结（自动生成）

# ClusterFusion 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：大语言模型（LLM）推理中的解码阶段因算子执行碎片化而面临高延迟。现有框架中，线程块（thread block）之间相互独立，通过片外全局内存进行数据交换和规约，导致大量内存流量和内核启动开销，严重限制了算子融合的范围。
- **背景**：现代GPU架构（如NVIDIA Hopper）虽然引入了**分布式共享内存（DSMEM）** 和低延迟的簇（cluster）内互连，但只提供底层的数据移动指令，缺乏高级的结构化通信抽象。开发者难以直接利用这些硬件能力来构建高效的融合算子。
- **论文目标**：通过设计**簇级（cluster-level）集体通信原语**，抽象片上规约与聚合模式，从而突破传统块隔离执行模式的限制，实现QKV投影、注意力、输出投影三大算子的完全片上融合，显著降低片外内存访问与内核启动开销。

## 2. 方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：将线程块簇视为**协同执行与调度的基本单元**，利用簇内高速片上互连（DSMEM）解决跨块数据依赖，避免片外内存介入。

- **关键原语**：
  - **ClusterReduce**：在簇内线程块之间执行元素级规约（如求和、取最大值），采用**二进制树模式**，经过 \( \log_2 N \) 轮（\( N \) 为簇大小）完成通信与计算重叠。
  - **ClusterGather**：将每个块持有的本地数据广播/收集到所有其他块，同样采用二进制树模式，每轮传输大小翻倍。
  - 两种原语均基于 **DSMEM** 实现，避免全局内存访问。

- **簇中心数据流（Cluster-Centric Dataflow）**：
  - 将每个注意力头映射到一个簇，簇内线程块分别负责切分**隐藏维度**（QKV投影）、**KV缓存序列长度**（注意力计算）、**输出维度**（输出投影）。
  - 数据流融合三个算子为一个内核：
    1. 计算局部Q、K、V；
    2. 使用 `ClusterGather` 得到完整Q、K、V；
    3. 计算局部注意力输出（类似FlashDecoding分区）；
    4. 使用两次 `ClusterReduce` 分别规约softmax统计量和注意力输出；
    5. 计算输出投影，写回全局内存。
  - 算法伪代码见论文 Algorithm 3（QKV+Attn+Out Proj）和 Algorithm 4（DeepSeek MLA 融合版本）。

- **DSMEM流量模型**：
  - \( \text{Traffic}_{\text{Reduce}} = size \times \log_2 N \times N \)
  - \( \text{Traffic}_{\text{Gather}} = size \times (2^{\log_2 N + 1} - 1) \times N \)
  - 论文通过理论分析和实验选择了**SplitToken**数据流（切分序列长度），其DSMEM流量最低，性能优于SplitHead等变体。

## 3. 实验设计

- **数据集/场景**：
  - 使用随机生成的标准输入，序列长度从 **1K 到 16K**，batch size 主要为 **1**（附录C.1也补充了 batch size=16 的实验）。
  - 评估真实数据集（ShareGPT、Splitwise）的序列长度分布，表明大多数实际场景序列长度 <8K。

- **基准方法（Baselines）**：
  - **SGLang** (v0.4.3.post2)、**vLLM** (v0.6.4.post1)、**TensorRT-LLM** (v0.18.0)、**MLC-LLM** (v0.20.dev0)
  - 所有基线启用 CUDA Graph 和 Torch.compile，并采用官方推荐的后端内核（CUTLASS、FlashAttention、FlashInfer 等）。

- **评估指标**：
  - **端到端延迟**：每个输出Token的时间（TPOT, Time Per Output Token）。
  - **核心模块延迟**：QKV投影 + 注意力 + 输出投影的合并延迟。

- **模型**：
  - **Llama2-7B**（标准MHA）
  - **DeepSeek-V2-Lite**（多潜在注意力MLA，包含权重吸收优化）

## 4. 资源与算力

- **GPU**：**单块 NVIDIA H100 SXM5 80GB** GPU（未使用多GPU训练，所有推理实验均在该单卡上完成）。
- **软件**：PyTorch 2.5.1，CUDA 12.4。
- **训练时长**：论文不涉及训练，仅讨论推理优化，未报告任何训练时间。所有实验均为推理延迟测量，属于一次性运行，未说明耗时。

## 5. 实验数量与充分性

- **实验组数**：
  - 端到端 TPOT 实验（图8，两个模型，5种序列长度，4个基线 + 本方法，共约 50 个数据点）。
  - 核心模块延迟实验（图9，类似规模）。
  - 簇大小与注意力头数影响实验（图11，两个序列长度，不同簇大小2/4/8/16，不同头数32/64/128）。
  - 消融实验：DSMEM开启/关闭对比（图13），片外 vs 片上原语延迟对比（表1）。
  - 多batch实验（附录C.1，batch size=16）。
  - 数据流变体对比（SplitHead vs SplitToken，附录C.2）。
  - 全局内存传输量与内核启动开销分析（图12/19）。
- **充分性评价**：
  - ✅ 实验覆盖了**不同模型架构**（MHA、MLA）、**不同序列长度**、**不同batch大小**、**不同簇配置**，并进行了**消融分析**和**性能归因**。
  - ✅ 基线对比选择最先进的框架，且全部采用官方优化配置，**公平性较好**。
  - ✅ 消融实验验证了DSMEM和原语的有效性，性能归因（全局内存传输量、内核启动开销）提供了直观解释。
  - ⚠️ 未进行**跨GPU架构**（如AMD MI300）或**其他硬件平台**的实验，也未与**其他融合方法**（如手动融合）进行直接对比。

## 6. 主要结论与发现

1. **性能提升**：ClusterFusion 在端到端延迟（TPOT）上，单batch场景下平均比 SGLang、vLLM、TensorRT-LLM、MLC-LLM 分别快 **1.41×、1.39×、1.43×、2.03×**（Llama2-7B）；对 DeepSeek-V2-Lite 也有 **1.34×~2.39×** 的提升。多batch（batch=16）下加速比略有下降（约1.1×~1.2×），但仍保持优势。
2. **核心模块加速**：QKV投影+注意力+输出投影的融合内核延迟降低更为显著，单batch下最高达 **3.19×** 快于MLC-LLM。
3. **性能来源**：主要得益于**减少全局内存传输**（降幅达一个数量级）和**大幅降低内核启动开销**（几乎降为0）。
4. **簇大小与头数关系**：最优簇大小取决于注意力头数和序列长度，通常**簇大小=4** 在多数配置下表现最佳，过大（8/16）会因互连带宽下降和活跃SM减少而性能回退。
5. **DSMEM的必要性**：关闭DSMEM后，TPOT上升最高达33%，证明片上通信是性能关键。

## 7. 优点

- **创新的原语设计**：ClusterReduce 和 ClusterGather 抽象了常见的片上集体通信模式，使开发者无需处理底层PTX指令，降低了编程门槛，且可复用。
- **融合范围扩展**：首次将QKV投影、注意力、输出投影完全融合到一个内核中，中间结果完全驻留在片上，突破了传统块隔离的限制。
- **理论与实践结合**：提出了DSMEM流量分析模型，用于指导最优数据流选择（如SplitToken优于SplitHead），并通过实验验证。
- **实验全面且客观**：涵盖多种模型、多种配置、消融、性能归因，代码已开源，便于复现。
- **对软硬件协同设计的启示**：指出了当前簇大小限制，并讨论未来硬件支持更全局片上通信的必要性。

## 8. 不足与局限

- **融合范围受硬件限制**：簇大小最大为16个线程块，若未来模型隐藏维度更大或出现更复杂算子，将超出簇内融合能力，需回退到片外通信。
- **多batch场景加速比有限**：当批大小增大时，KV缓存和权重占据主要内存带宽，中间结果占比变小，因此加速比下降至约1.1×。
- **模型覆盖有限**：仅测试了Llama2-7B和DeepSeek-V2-Lite，未验证更大模型（如70B、MoE）或更小模型。也未测试CPU/其他GPU平台（如AMD、Intel GPU）。
- **未考虑正交优化组合**：未与量化（AWQ）、稀疏注意力等技术结合，无法评估联合收益。
- **未评估训练/预填充阶段**：工作专注于解码阶段，对于预填充阶段的适用性未讨论。
- **潜在偏差**：基线可能未针对特定序列长度和模型进行超参数调优，尽管使用了官方推荐配置，但仍存在细微偏差。

（完）
