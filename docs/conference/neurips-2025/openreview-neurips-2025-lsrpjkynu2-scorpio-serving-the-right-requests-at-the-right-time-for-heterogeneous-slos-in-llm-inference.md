---
title: "Scorpio: Serving the Right Requests at the Right Time for Heterogeneous SLOs in LLM Inference"
title_zh: Scorpio：面向LLM推理中异构服务等级目标的请求适时服务系统
authors: "Yinghao Tang, Tingfeng Lan, Xiuqi Huang, Hui Lu, Wei Chen"
date: 2025-05-09
pdf: "https://openreview.net/pdf?id=LSrpJkynU2"
tags: ["query:agents-os"]
score: 7.0
evidence: 面向SLO的LLM服务系统，利用异构SLO进行自适应调度
tldr: SCORPIO面向异构SLO的LLM推理服务系统，通过TTFT守卫和TPOT守卫分别优化首token延迟和输出token速率，利用SLO异质性在准入控制、队列管理和批次选择中进行自适应调度，显著提升系统有效吞吐量与SLO达标率。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-lsrpjkynu2/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1432, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lsrpjkynu2/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1425, \"height\": 419, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lsrpjkynu2/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1153, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lsrpjkynu2/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1427, \"height\": 482, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lsrpjkynu2/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1437, \"height\": 795, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lsrpjkynu2/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1500, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lsrpjkynu2/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 712, \"height\": 952, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lsrpjkynu2/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 997, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lsrpjkynu2/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 694, \"height\": 940, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-lsrpjkynu2/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1400, \"height\": 840, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-lsrpjkynu2/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 962, \"height\": 280, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lsrpjkynu2/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1455, \"height\": 289, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lsrpjkynu2/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 587, \"height\": 331, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lsrpjkynu2/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1446, \"height\": 381, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-lsrpjkynu2/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1448, \"height\": 1019, \"label\": \"Table\"}]"
motivation: 现有LLM服务系统忽略异构SLO，导致SLO达标率低。
method: 提出TTFT守卫与TPOT守卫，基于SLO异质性调度请求。
result: SCORPIO在异构SLO下显著提高有效吞吐量和达标率。
conclusion: 利用SLO异质性可大幅提升LLM推理服务质量。
---

## Abstract
Existing Large Language Model (LLM) serving systems prioritize maximum throughput. They often neglect Service Level Objectives (SLOs) such as Time to First Token (TTFT) and Time Per Output Token (TPOT), which leads to suboptimal SLO attainment. This paper introduces SCORPIO, an SLO-oriented LLM serving system designed to maximize system goodput and SLO attainment for workloads with heterogeneous SLOs. Our core insight is to exploit SLO heterogeneity for adaptive scheduling across admission control, queue management, and batch selection. SCORPIO features a TTFT Guard, which employs least-deadline-first reordering and rejects unattainable requests, and a TPOT Guard, which utilizes a VBS-based admission control and a novel credit-based batching mechanism. Both guards are supported by a predictive module. Evaluations demonstrate that SCORPIO improves system goodput by up to 14.4X and SLO adherence by up to 46.5% compared to state-of-the-art baselines.

---

## 论文详细总结（自动生成）

# SCORPIO：面向LLM推理中异构服务等级目标的请求适时服务系统

## 1. 核心问题与整体含义（研究动机和背景）

现有的大语言模型（LLM）推理服务系统（如 vLLM、SGLang）主要关注最大化吞吐量，忽略了服务质量目标（SLO），包括首令牌时间（TTFT）和每个输出令牌时间（TPOT）。这导致在异构SLO的工作负载下，SLO达标率低下。不同应用（如编程助手、聊天机器人、摘要生成）对TTFT和TPOT的要求差异很大，但现有系统对所有请求一视同仁，无法满足差异化的SLO需求。该论文提出一个面向SLO的LLM服务系统SCORPIO，旨在通过利用SLO的异构性进行自适应调度，最大化系统有效吞吐量（goodput）和SLO达标率。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
利用请求SLO的异质性，在准入控制、队列管理和批次选择三个阶段进行差异化调度：TTFT上，宽松SLO的请求可以稍后服务；TPOT上，宽松TPOT的请求可以跳过部分生成迭代，为紧TPOT的请求腾出资源。

### 关键技术细节
- **预测模块（Predictor）**：
  - 序列长度预测器：采用OPT-125M微调的分类器，将输出长度分为100个等宽桶，预测输出长度所在的桶。
  - TPOT估计器：基于运行批次大小、平均序列长度等构建解析模型（公式4），估计迭代间延迟（ITL），并进一步估算新请求加入后的批次TPOT（公式5）。
  - TTFT估计器：基于请求在等待队列中的排序索引，通过预填时间模型（公式6）累加估算最小TTFT（公式7）。

- **TTFT守卫（TTFT Guard）**：
  - 最晚截止时间优先（LDF）重排序：根据TTFT截止时间对等待队列排序，紧急请求靠前。
  - 不可达SLO拒绝：当系统负载过高时，拒绝那些无法在其TTFT截止时间内完成的请求。

- **TPOT守卫（TPOT Guard）**：
  - **TPOT相对比例（TRP）**：定义请求的TRP = min(S_TP) / S_TP(r)，量化其紧急性。
  - **基于虚拟批次大小的准入控制（VBS-based Admission Control）**：新请求加入时，将运行集合中所有请求的TRP之和作为虚拟批次大小（VBS），用VBS估算TPOT，仅当不违反最小SLO时准入。
  - **基于信用的批处理（Credit-based Batching）**：每个请求每步按TRP速率积累信用，信用≥1.0时被选中进入批次，然后信用减1.0。宽松TPOT的请求积累慢，被选中的频率低，从而跳过部分迭代。

### 算法流程（文字说明）
1. 请求到达→预测模块预测输出长度，并估算TTFT和TPOT。
2. TTFT守卫：按LDF重排序队列，拒绝不可达请求。
3. TPOT守卫：对排队请求，依次尝试加入运行集R，用VBS估算TPOT，若不超过min S_TP则准入。
4. 每步迭代：运行集中的请求根据TRP积累信用；信用≥1.0的请求组成实际执行批次，并扣除1.0信用。
5. 执行引擎处理选中的批次。

## 3. 实验设计

### 数据集/场景
- **数据集**：ShareGPT、LMSYS-Chat-1M（真实对话数据）。
- **SLO类别**：6个类别，涵盖紧TTFT+紧TPOT（如代码生成）、紧TPOT+松TTFT、松TPOT+紧TTFT、双松（如摘要）等。
- **基准方法**：
  - vLLM（吞吐量优先的调度，贪婪准入）
  - S3（基于输出长度排序的调度，作者在vLLM上复现其核心策略）
  - Mooncake（基于早期拒绝的准入控制，集成到vLLM中）

### 实验场景
- **QPS缩放实验**：在不同请求到达率（QPS）下比较goodput和SLO达标率。
- **真实轨迹服务**：使用Azure推理轨迹的前20分钟（含突发和轻负载交替）评估累计SLO达标请求数。
- **消融实验**：逐步加入TTFT Guard、TPOT Guard，分析对TTFT违规、TPOT违规和goodput的影响。
- **开销分析**：测量SCORPIO调度开销占总时间比例。
- **预测器桶策略分析**：比较不同桶数（10~1000）和等宽/等频两种分桶策略的预测性能。

### 对比指标
- 系统有效吞吐量（goodput）：单位时间内SLO达标的请求数。
- SLO达标率（adherence）：SLO达标请求数占总请求数比例。
- 累计SLO达标请求数。

## 4. 资源与算力

文中明确说明：
- **GPU集群**：1台服务器，配备4块 NVIDIA A100 GPU（每块80GB显存）。GPU间通过NVLink（GPU0-GPU1、GPU2-GPU3）和PCIe+NUMA互联。
- **推理模型**：Meta Llama-3.1 8B（单GPU运行）、Google Gemma-2 27B（4 GPU tensor parallelism）。
- **预测器**：OPT-125M，在同一个GPU上与LLM服务共存（资源争用导致5%~20%性能下降，通过分离可缓解）。
- **训练信息**：预测器使用20K样本，按6:2:2划分训练/验证/测试，batch size=64，8个epoch，优化器Adam，学习率2e-5。

未明确总训练/推理时长，但调度开销小于总运行时间的0.2%。

## 5. 实验数量与充分性

- **QPS缩放实验**：两个数据集×两个模型×多个QPS点（从5到20不等），共约4个子图×6~7个QPS点≈24~28组数据点。
- **真实轨迹服务**：两个数据集×两个模型，共4个子图。
- **消融实验**：一个QPS点（14），两个数据集×两个模型，共4组柱状图。
- **开销分析**：两个数据集×两个模型，共4组数据。
- **桶策略分析**：两个模型×两个数据集×两种分桶策略×7种桶数，共56组指标（含Tau、RMSE等）。
- **解析模型精度分析**：两个模型×两个数据集×两种解析模型（预填、ITL），报告R²、RMSE、MAPE。

实验覆盖了不同模型大小、不同数据集、不同负载水平，并进行了详细的消融和组件分析。实验公平性：所有基线在同一vLLM平台实现，S3和Mooncake的策略被复现后集成。但需注意：基线vLLM本身是吞吐量最优系统，没有针对SLO设计，对比合理。

## 6. 主要结论与发现

- SCORPIO在几乎所有高QPS场景下显著优于所有基线：goodput最高提升14.4倍，SLO达标率最高提升46.5%。
- 真实轨迹下，SCORPIO累计SLO达标请求数比Mooncake高1.25倍，比vLLM高2.01倍，比S3高2.11倍。
- 消融实验表明：TTFT Guard和TPOT Guard相互补充，单独使用任一都会导致另一类SLO严重违规；两者结合达到最佳性能。
- 预测器的桶策略：等宽分桶+100个桶在多个指标（Tau、RMSE、off-by-n准确率）上达到最佳平衡；按600个桶时分类准确率低但误差小。
- SCORPIO调度开销极低（<0.2%），在实际部署中可行。

## 7. 优点

- **问题定位准确**：指出现有系统忽略异构SLO的缺陷，具有实用价值。
- **方法论创新**：提出TRP、VBS、信用批处理等概念，将SLO异质性化为调度中的量化指标，理论清晰，算法优雅。
- **架构模块化**：TTFT Guard和TPOT Guard可独立使用，且与预测模块协同，易于扩展。
- **实验全面**：覆盖多种模型、数据集、负载模式，包含真实轨迹、消融、开销分析。
- **公平对比**：所有基线在同一框架下复现，控制变量。
- **开源**：承诺开源代码，可复现。

## 8. 不足与局限

- **低负载场景性能略差**：在QPS较低时（如5），vLLM在某些配置下goodput和SLO达标率略高于SCORPIO，原因是预测器与LLM在同一GPU上资源争用。文中建议通过分离GPU或动态切换简化策略缓解，但未实现。
- **仅支持标准LLM服务技术**：未与最新优化（如预填-解码分离、推测解码等）集成，论文指出留作未来工作。
- **假设保守**：TPOT估计中假设所有运行请求将继续处理至少P步，可能导致过度拒绝；TTFT估计中只考虑排队序列预填时间，未考虑动态变化。
- **拒绝策略简单**：对不可达请求简单拒绝，未探索降级服务（如分配更低优先级、迁移到其他节点）。
- **预测器依赖**：序列长度预测器使用OPT-125M，可能因权限限制或模型差异影响泛化；预测误差会传导导致调度决策偏差。
- **实验规模有限**：仅使用8B和27B模型，未测试更大规模（如70B/175B）或多节点分布式场景。
- **未考虑公平性**：仅关注SLO达标，可能对某些用户群体造成服务降级，缺乏公平性分析。

（完）
