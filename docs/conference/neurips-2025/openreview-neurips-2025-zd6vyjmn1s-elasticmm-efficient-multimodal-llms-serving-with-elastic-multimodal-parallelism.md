---
title: "ElasticMM: Efficient Multimodal LLMs Serving with Elastic Multimodal Parallelism"
title_zh: ElasticMM：基于弹性多模态并行的高效多模态大模型服务
authors: "Zedong Liu, Shenggan Cheng, Guangming Tan, Yang You, Dingwen Tao"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=Zd6VyjmN1S"
tags: ["query:agents-os"]
score: 7.0
evidence: 弹性并行适应资源异构性以支持AI工作负载
tldr: 针对多模态大模型服务中异构工作负载和资源利用率低的问题，提出了弹性多模态并行（EMP）范式。该方法通过动态调整并行策略适配不同推理阶段的资源异构性，显著降低了首个令牌生成时间并提升了资源利用率。实验验证了EMP在异构环境下的高效性，为AI工作负载的异构计算基础设施提供了实用方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-zd6vyjmn1s/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1448, \"height\": 463, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zd6vyjmn1s/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1224, \"height\": 676, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zd6vyjmn1s/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1238, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zd6vyjmn1s/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1161, \"height\": 415, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zd6vyjmn1s/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1437, \"height\": 640, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zd6vyjmn1s/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1450, \"height\": 335, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zd6vyjmn1s/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1445, \"height\": 317, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-zd6vyjmn1s/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1453, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zd6vyjmn1s/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1228, \"height\": 182, \"label\": \"Table\"}]"
motivation: 现有紧密耦合的服务架构无法适应混合请求类型和推理阶段的资源异构性，导致延迟高、资源利用率低。
method: 提出弹性多模态并行（EMP）范式，根据推理阶段和资源异构性动态调整并行策略。
result: 相比基线方法，TTFT显著降低，资源利用率提升。
conclusion: EMP为异构环境下的大模型高效服务提供了可行范式。
---

## Abstract
Multimodal large language models (MLLMs) extend LLMs to handle images, videos, and audio by incorporating feature extractors and projection modules. However, these additional components—combined with complex inference pipelines and heterogeneous workloads—introduce significant inference overhead. Therefore, efficiently serving MLLMs remains a major challenge. Current tightly coupled serving architectures struggle to distinguish between mixed request types or adapt parallelism strategies to different inference stages, leading to increased time-to-first-token (TTFT) and poor resource utilization. To address this, we introduce Elastic Multimodal Parallelism (EMP), a new serving paradigm that elastically adapts to resource heterogeneity across request types and inference stages. Building upon EMP, we develop ElasticMM, an MLLM serving system that (1) separates requests into independent modality groups with dynamic resource allocation via a modality-aware load balancer; (2) decouples inference stages and enables parallelism adjustment and adaptive scaling via elastic partition scheduling; and (3) improves inference efficiency through unified multimodal prefix caching and non-blocking encoding. Experiments on diverse real-world datasets show that ElasticMM outperforms state-of-the-art (SOTA) serving systems, reducing TTFT by up to 4.2$\times$ and achieving 3.2–4.5$\times$ higher throughput while meeting service-level objectives (SLOs).

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：多模态大语言模型（MLLMs）在文本基础上整合图像、视频、音频等输入，引入了特征提取器、投影模块等额外组件，导致推理管线复杂、计算开销大。现有服务系统采用紧密耦合架构（如 vLLM、SGLang），将所有推理阶段（编码、预填充、解码）固定在同一硬件实例上执行，无法区分纯文本请求与多模态请求的异构需求，也无法根据不同推理阶段的计算特性调整并行策略，造成**首令牌生成时间（TTFT）增加**、**资源利用率低下**。
- **整体含义**：为满足服务等级目标（SLO），需要一种既能**解耦**又能**弹性适应**资源异构性的新服务范式，动态地为不同请求类型和推理阶段分配资源，从而提高吞吐、降低延迟。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
提出**弹性多模态并行（Elastic Multimodal Parallelism, EMP）** 范式，构建两层次调度框架（模态级和阶段级），实现：
- 模态级：将纯文本请求与多模态请求分离至独立模态组，通过**模态感知负载均衡**动态分配和缩放资源。
- 阶段级：解耦推理阶段（编码、预填充、解码），通过**弹性分区调度**允许各阶段独立调整并行度（如编码和预填充采用更大并行度，解码收缩并行度）。

### 关键技术细节

1. **模态感知负载均衡**：
   - 结合主动机制（根据长期负载趋势预分配实例，最大化最低突变容差 `bt(i) = N_peak_i / N_avg_i`，采用贪心策略）与反应式扩展（当短时流量突发时，评估调整组内并行与跨组抢占的收益-成本，选择影响最小的实例进行抢占）。
   
2. **弹性分区调度**（公式已用文字说明）：
   - **请求调度**：采用 FCFS 策略选取预填充请求子集 `Rp`，受 GPU 内存和计算吞吐约束，通过分析预填充时间上限确定批处理临界点。
   - **阶段分配**：优先分配空闲实例为 `Rp` 做预填充；若空闲 KV 缓存不足，允许抢占解码阶段实例 `emax`（拥有最多空闲槽位），并通过收益-成本模型（公式 (2)）决定是否抢占：增益 = 加速比，成本 = 迁移开销 + 被抢占任务性能影响 × 惩罚因子 w。
   - **弹性自动缩放**：监控解码阶段，当其资源不足时触发缩放。通过离线预配置确定阈值，优先从组内空闲实例扩展，否则通过收益-成本模型（公式 (3)）选择抢占预填充实例或跨组实例。数据并行优先于张量并行，以简化 KV 缓存迁移和碎片资源利用。

3. **多模态推理优化**：
   - **统一多模态前缀缓存**：将文本前缀缓存与多模态输入缓存统一管理（LRU 淘汰），对重复图像或系统提示跳过编码和预填充阶段，减少冗余计算和数据传输。
   - **非阻塞编码**：将图像预处理和编码解耦为独立异步进程，避免编码阻塞后续阶段，降低 TTFT。

## 3. 实验设计

- **数据集**：两个真实世界多模态数据集，混合图像和纯文本请求：
  - VisualWebInstruct：来自 70 万+ Web URL 的大规模数据集，文本输入较长。
  - ShareGPT-4o：5 万张高分辨率图像及对应文本提示。
- **benchmark 场景**：使用 Poisson 分布生成变请求到达率（QPS），并引入真实生产服务轨迹模拟实际负载。
- **对比方法**：
  - vLLM (v0.6.6)：紧密耦合基线，所有阶段在同一硬件。
  - DistServe：解耦预填充和解码阶段但静态分配资源，为其扩展支持多模态推理。
- **模型**：LLaMA3.2-Vision-11B（编码器-解码器架构）和 Qwen2.5-VL-7B（解码器仅架构），分别代表两类 MLLM 架构。
- **消融实验**：构建 ElasticMM 变体（w/o EMP、w/o UniCache、ElasticMM-EMP 等）逐一评估各技术贡献。

## 4. 资源与算力

- **实验平台**：一台高端工作站，配备 **8 张 NVIDIA A800 80GB GPU**、2 颗 64 核 Intel Xeon 8358P CPU、2 TB DDR4 内存。GPU 间 NVLink 带宽 400 GB/s。
- **训练/推理时长**：论文未明确报告单次实验或全部实验的总时长，仅说明是在上述平台上完成的评估。

## 5. 实验数量与充分性

- **主要实验**：
  - 端到端性能对比（图 5）：两个数据集 × 两个模型 × 三种方法（vLLM、DistServe、ElasticMM）→ 共 12 组子图，涵盖输入延迟（TTFT）和输出延迟随 QPS 变化。
  - 吞吐量对比（图 6）：不同 SLO 缩放系数（1×-5×）下的最大吞吐，类似 2 模型 × 2 数据集 × 5 个 SLO 水平 → 20 组数据点。
  - 消融实验（图 7、图 8）：
    - 图 7：EMP 效果（静态分配 vs. 弹性分配），2 模型 × 5 SLO 水平 × 4 种分配策略 → 40 组数据点。
    - 图 8：推理优化效果（UniCache、非阻塞编码），在混合数据集下，2 模型 × 多个 QPS → 约 16 组曲线。
- **充分性评价**：
  - 覆盖了两种主流 MLLM 架构、两种类型数据集（文本密集型 vs. 视觉密集型）、多种负载水平、多个 SLO 要求，以及充分的消融实验分离各技术贡献。
  - 采用实际生产轨迹，增强了真实性。
  - **客观公平**：基线方法为公开 SOTA 系统（vLLM、DistServe），且明确说明对 DistServe 扩展了多模态支持；实验指标标准化（归一化延迟），便于公平比较。

## 6. 主要结论与发现

- ElasticMM 相比 vLLM 将 TTFT 降低最多 **4.2 倍**（ShareGPT-4o 上 Qwen2.5-VL），在 LLaMA3.2-Vision 上降低 3.5 倍；在 VisualWebInstruct 上降低 3.7 倍与 2.9 倍。
- 吞吐提升：相比 vLLM 达到 **3.2–4.5 倍**（ShareGPT-4o），相比 DistServe 提升最多 2.3 倍。
- 输出延迟保持稳定，不受编码和预填充干扰。
- 弹性多模态并行（EMP）比任何静态资源分配策略（如偏向文本、均分、偏向多模态）均显著提升吞吐（1.8×–2.3×）。
- 统一前缀缓存和非阻塞编码各自贡献一致的延迟降低，两者叠加效果更佳。

## 7. 优点

- **方法创新**：首次系统性提出面向 MLLM 服务的弹性和解耦两层次框架，解决了紧密耦合和静态分配的根本瓶颈。
- **技术实用性**：优先使用数据并行，简化弹性扩展时的 KV 缓存迁移；收益-成本模型提供可调惩罚因子，灵活控制抢占激进程度。
- **实验体系全面**：涵盖多种架构、多种数据集、多种负载、多种 SLO、充分的消融实验，验证了每项技术的独立贡献。
- **结果显著**：延迟和吞吐的改进幅度大，且始终满足 SLO。
- **兼容性广**：不依赖特定模型架构，无需牺牲精度，可与 FlashAttention、Flash-Decoding 等算子优化正交整合。

## 8. 不足与局限

- **实验环境**：仅在单机 8 GPU 上测试，未扩展到多节点集群。论文将多节点场景（存在跨节点通信延迟、更大并行搜索空间）列为未来工作。
- **资源与时间细节缺失**：未报告单个实验运行时间、总 GPU 小时数，不利于判断成本。
- **基线覆盖**：仅对比 vLLM 和 DistServe，未包括其他解耦方案（如 Splitwise、Mooncake）或专门的多模态服务系统（如 ModServe），可能削弱对比的全面性。
- **负载模型**：使用 Poisson 分布生成请求，虽加入真实轨迹，但随机性可能掩盖某些极端突发模式。
- **收益-成本模型**：模型中的惩罚因子 w 需要人工调节，论文未讨论自适应性或对不同工作负载的鲁棒性。缩放阈值的离线预配置也可能在动态环境中过时。
- **非阻塞编码的实现细节**：未详细说明如何确保异步编码结果正确同步，仅依赖同步屏障，但未评估极端情况下的延迟波动。

（完）
