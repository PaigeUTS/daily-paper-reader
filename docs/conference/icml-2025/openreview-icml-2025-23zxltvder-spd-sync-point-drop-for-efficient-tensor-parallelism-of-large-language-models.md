---
title: "SPD: Sync-Point Drop for Efficient Tensor Parallelism of Large Language Models"
title_zh: SPD：用于大语言模型高效张量并行的同步点丢弃
authors: "Han-Byul Kim, Duc N.M Hoang, Arnav Kundu, Mohammad Samragh, Minsik Cho"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=23zxLtvder"
tags: ["query:agents-os"]
score: 7.0
evidence: 减少张量并行中的通信开销，支持大模型的异构计算
tldr: 大型语言模型分布式推理中，张量并行的通信开销是主要瓶颈。本文提出同步点丢弃（SPD）技术，通过选择性丢弃注意力输出上的同步点，使执行无需同步即可继续。实验表明，SPD能够有效降低通信延迟，提升推理吞吐量，为异构计算环境下大模型部署提供了高效优化方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-23zxltvder/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1759, \"height\": 467, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-23zxltvder/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1761, \"height\": 241, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-23zxltvder/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1767, \"height\": 531, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-23zxltvder/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 535, \"height\": 617, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-23zxltvder/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 854, \"height\": 851, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-23zxltvder/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 837, \"height\": 509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-23zxltvder/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1773, \"height\": 1198, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-23zxltvder/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1747, \"height\": 772, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-23zxltvder/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1745, \"height\": 349, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-23zxltvder/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 710, \"height\": 204, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-23zxltvder/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 563, \"height\": 203, \"label\": \"Table\"}]"
motivation: 张量并行中同步通信开销大，限制了分布式推理的扩展性和低延迟。
method: 提出SPD，在注意力块上根据敏感性选择性地丢弃同步点，允许无通信执行。
result: 理论分析和实验证明SPD显著降低通信开销，提升推理效率。
conclusion: SPD是一种有效的大模型分布式推理优化技术，可加速异构计算环境下的模型服务。
---

## Abstract
With the rapid expansion in the scale of large language models (LLMs), enabling efficient distributed inference across multiple computing units has become increasingly critical. However, communication overheads from popular distributed inference techniques such as Tensor Parallelism pose a significant challenge to achieve scalability and low latency. Therefore, we introduce a novel optimization technique, Sync-Point Drop (SPD), to reduce communication overheads in tensor parallelism by selectively dropping synchronization on attention outputs. In detail, we first propose a block design that allows execution to proceed without communication through SPD. Second, we apply different SPD strategies to attention blocks based on their sensitivity to the model accuracy. The proposed methods effectively alleviate communication bottlenecks while minimizing accuracy degradation during LLM inference, offering a scalable solution for diverse distributed environments: SPD offered about 20\% overall inference latency reduction with < 1\% accuracy regression for LLaMA2-70B inference over 8 GPUs.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

大语言模型规模快速增长，分布式推理成为降低延迟的常用手段。其中张量并行（Tensor Parallelism, TP）通过将模型参数分割到多个GPU并行计算，但需要在每个decoder block的注意力输出后执行全局同步（all-reduce），引入大量通信开销。随着模型增大和GPU数量增多，同步点数量增加，通信延迟成为主要瓶颈，限制可扩展性。现有工作多从系统层面优化通信操作本身（如ring/tree all-reduce），但本文提出直接丢弃部分同步点（Sync-Point Drop, SPD），从根本上减少通信次数，同时通过设计新型块结构和基于敏感性的策略最小化精度损失。

## 2. 方法论

### 核心思想
在TP中，选择性移除注意力输出后的all-reduce同步操作，让各设备独立继续前向计算，从而节省通信延迟。但丢弃同步会导致各设备上注意力输出不一致，因此需要重新设计块结构并采用多级策略恢复精度。

### 关键技术细节
#### 2.1 新块设计（以无偏置线性层为例）
- **MLP输入**：将残差连接（X）与本地注意力输出（Y_i）相加作为MLP输入（X + Y_i），使输入尽可能接近完整信息情况。
- **MLP输出**：拆解原始残差连接——将块输入X保留到同步后添加，将Y_i作为新残差在同步前添加。最终块输出为 X + sum(Y_i) + sum(Z_i)，其中Z_i为本地MLP输出。有偏置时，偏置项b需在同步后添加以保持正确。

#### 2.2 基于块敏感性的多级策略
首先使用校准数据（WikiText2训练集128样本）测量每个块的同步敏感性：对第i块，对比其之前所有块保持TP状态、其之后全部设为SPD时，若将第i块也设为SPD导致的困惑度变化作为敏感性指标。将所有块按敏感性升序排列，根据阈值τ1、τ2分为三类：

- **不敏感块（ISB）**：零样本丢弃同步点（ZS），直接应用SPD块设计。
- **敏感块（SB）**：采用SPD感知的块到块蒸馏（B2B）。以原TP块为教师，使用校准数据通过单块前向传播的输出计算MSE损失，微调SPD块的参数（保持TP块参数不变）。
- **极敏感块（ESB）**：先使用注意力头分组初始化（HG），再进行B2B蒸馏。HG分两步：
  - **头散射**：根据校准数据计算每个注意力头的注意力分数（σ(Q,K)），通过最大化同一设备内头部注意分数的欧氏距离，使功能不同的头分布在不同设备。
  - **MLP匹配**：将散射后的头子集与设备上MLP分区匹配，以MLP输出范数（残差前）为指标，选择使总范数最大的分配组合。

算法流程如Algorithm 1所示：按敏感性排序后，对前Nspd个块依次应用ZS（ISB）、ZS+B2B（SB）、ZS+B2B+HG（ESB）。

## 3. 实验设计

### 数据集/场景
- **零样本评估**：ARC、HellaSwag、LAMBADA、PIQA、SciQ、WinoGrande六个任务的平均准确率。
- **MMLU评估**：部分模型（LLaMA2-13B/70B）在MMLU上的准确率。
- **校准数据**：WikiText2训练集中随机128个样本，序列长度2048，用于敏感性测量和蒸馏。

### Benchmark
- 对比基线：0% SPD（即完全TP）作为No SPD，以及不同SPD比例（25%~100%）下三种策略：纯ZS、ZS+B2B、ZS+B2B+HG。
- 设备互连带宽：高带宽（HBW，300GB/s）和低带宽（LBW，10GB/s）两种设置；2节点情况节点间50GB/s。

### 对比方法
主要对比不同SPD策略对精度和延迟的影响，未与其他优化技术（如量化、剪枝）直接比较。

## 4. 资源与算力

- **GPU型号**：Nvidia A100-80G。
- **GPU数量**：每个实验使用4或8个GPU（单节点或双节点）。
- **带宽设置**：高带宽300GB/s，低带宽通过关闭CUDA-direct link设为10GB/s；双节点时节点间50GB/s。
- **训练/微调资源**：块到块蒸馏使用10 epochs，每个epoch使用128个样本（批处理大小文中未明确），属于轻量级微调，文中未给出具体训练时长或GPU小时数。

## 5. 实验数量与充分性

- 覆盖模型：LLaMA2（7B/13B/70B）、OPT（6.7B/13B/30B/66B），共7种规模。
- 分布式配置：8 GPU和4 GPU（部分模型），共12种（模型×GPU数）组合。
- SPD比例：从25%到100%不等，逐步增加。
- 策略对比：ZS vs ZS+B2B vs ZS+B2B+HG vs No SPD，在每个比例下比较精度。
- 延迟测试：在不同带宽（HBW/LBW）和节点数（1-node/2-node）下测量加速比。
- 消融实验：附录B对块设计选择进行了困惑度对比，验证残差添加点的最优选择。
- 总体实验量充足，且在不同条件下均验证了方法的有效性，公平性良好（所有结果均在同一硬件下测量）。

## 6. 主要结论与发现

- SPD可有效降低TP通信延迟：减少一半同步点后，数据传输延迟降低超46%，端到端推理加速显著。
- 基于敏感性的多级策略能最小化精度损失：例如LLaMA2-70B 8GPU下，70%块使用SPD（均为ISB，零样本）可获~19.7%加速比，精度下降仅0.94%。
- 不敏感块比例随模型增大而增加（LLaMA2-70B达75%，OPT-66B达84%），表明大规模模型冗余性更强，适合SPD。
- 较小模型（如LLaMA2-7B、OPT-6.7B）存在极敏感块，需HG+B2B恢复精度。
- OPT模型比LLaMA2对SPD更鲁棒，可能因为更高冗余。
- 加速比在低带宽环境下更显著，对计算瓶颈的预填充阶段（prefill stage）特别有效。

## 7. 优点

- **创新性**：首次提出直接丢弃同步点而非优化通信本身，概念简单但有效。
- **块设计严谨**：从数学上保证SPD块的输出形式与TP相同（完整求和），减少信息丢失。
- **敏感性分析实用**：仅需少量校准数据即可识别每块敏感度，成本低。
- **多级策略灵活**：对不同敏感度块采用不同恢复手段，平衡精度与效率。
- **全面实验**：覆盖多种模型、多种GPU数、多种带宽和多种SPD比例，结果具有说服力。
- **兼容性讨论**：在附录中讨论了与数据并行、流水线并行和混合并行的集成，拓展了应用范围。

## 8. 不足与局限

- **实验覆盖有限**：仅测试了LLaMA2和OPT系列，未在更大模型（如GPT-3/4、Gemma等）或其他架构（如Mistral、Falcon）上验证。
- **校准数据依赖性**：敏感性测量和蒸馏均依赖于从WikiText2随机采样的128个样本，可能无法完全反映真实部署数据的分布，有偏差风险。
- **最大加速比受限**：SPD只减少注意力输出后的同步（占TP总同步点的一半），无法消除MLP前的同步，故理论加速上限为50%（实际低于此）。
- **极敏感块的适用性**：仅在小模型中发现ESB，且头分组初始化仅在小模型有效，大模型（70B）未出现ESB，方法在大模型上的额外收益有限。
- **未与其他优化技术定量比较**：未与量化、剪枝或系统级通信优化（如NCCL优化）进行端到端对比，无法体现相对优劣。
- **应用限制**：SPD改变模型数值行为，在需要严格数学等价性的场景（如科学计算）可能不可接受；且对注意力头分组和MLP匹配依赖前向采样，可能引入额外预处理开销。

（完）
