---
title: "SpecEdge: Scalable Edge-Assisted Serving Framework for Interactive LLMs"
title_zh: SpecEdge：面向交互式LLM的可扩展边缘辅助服务框架
authors: "Jinwoo Park, Seunggeun Cho, Dongsu Han"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=4QVLKwgg3S"
tags: ["query:agents-os"]
score: 7.0
evidence: 边缘辅助的服务器推理，利用异构GPU
tldr: 当前服务器为中心的LLM推理系统忽视了边缘GPU资源。本文提出SpecEdge框架，通过投机解码将LLM推理工作负载在边缘和服务器GPU之间拆分，仅交换token输出。实验表明，SpecEdge将服务器吞吐量提升2.22倍，整体成本效率提升1.91倍，为服务器异构计算资源利用提供了新思路。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 585, \"height\": 341, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 880, \"height\": 311, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 478, \"height\": 279, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 687, \"height\": 220, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 675, \"height\": 209, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1394, \"height\": 328, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 465, \"height\": 271, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 467, \"height\": 270, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 457, \"height\": 276, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 456, \"height\": 275, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 465, \"height\": 268, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 455, \"height\": 272, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1405, \"height\": 223, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 845, \"height\": 626, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 753, \"height\": 567, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-4qvlkwgg3s/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 613, \"height\": 521, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-4qvlkwgg3s/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1440, \"height\": 1047, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4qvlkwgg3s/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1439, \"height\": 782, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4qvlkwgg3s/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1160, \"height\": 786, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4qvlkwgg3s/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1442, \"height\": 388, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4qvlkwgg3s/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1136, \"height\": 265, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4qvlkwgg3s/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 998, \"height\": 266, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4qvlkwgg3s/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1178, \"height\": 574, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4qvlkwgg3s/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 489, \"height\": 314, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4qvlkwgg3s/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1441, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4qvlkwgg3s/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 556, \"height\": 313, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-4qvlkwgg3s/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1440, \"height\": 793, \"label\": \"Table\"}]"
motivation: 现有服务器中心系统忽略边缘GPU，导致资源浪费和成本高昂。
method: 提出SpecEdge框架，利用投机解码在边缘和服务器GPU间拆分LLM推理负载。
result: 服务器吞吐量提升2.22倍，成本效率提升1.91倍。
conclusion: 边缘辅助推理能有效降低LLM服务成本并提升吞吐量。
---

## Abstract
Large language models (LLMs) power many modern applications, but serving them at scale remains costly and resource-intensive. Current server-centric systems overlook consumer-grade GPUs at the edge. We introduce SpecEdge, an edge-assisted inference framework that splits LLM workloads between edge and server GPUs using a speculative decoding scheme, exchanging only token outputs over the network. SpecEdge employs proactive edge drafting to overlap edge token creation with server verification and pipeline-aware scheduling that interleaves multiple user requests to increase server-side throughput. Experiments show SpecEdge enhances overall cost efficiency by **1.91×** through achieving **2.22×** server throughput, and reduces inter token latency by **11.24\%** compared to a server-only baseline, introducing a scalable, cost-effective paradigm for LLM serving. The code is available at https://github.com/kaist-ina/specedge

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **背景**：大规模语言模型（LLM）服务成本高昂、资源密集，现有系统完全依赖数据中心内昂贵的高端GPU（如H100、A100），忽视了网络边缘大量存在的消费级GPU（如RTX 4090、RTX 3090）。这些边缘GPU在计算能力和性价比上具有显著优势（RTX 4090的FP16算力超过A100，成本仅为1/14.43）。
- **核心问题**：如何有效利用边缘GPU来降低LLM推理服务的成本，同时保持或提升服务质量（低延迟、高吞吐）？
- **挑战**：传统并行化技术（如张量并行、流水线并行）依赖专用高速互联（NVLink、InfiniBand），在广域网（WAN）环境下不适用；传统的层分割（split computing）方法每生成一个token都需要通信，导致高延迟，且无法缓解LLM推理的内存I/O瓶颈。
- **整体含义**：如果能够协调边缘和服务器GPU进行协同推理，就可以显著降低运营成本，并缓解数据中心算力压力，推动LLM服务的可扩展性和经济性。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

### 2.1 核心思想：基于投机解码（Speculative Decoding）的边缘-服务器协同

- 将LLM推理过程解耦为两个阶段：
  - **边缘起草（Edge Drafting）**：边缘GPU使用轻量级草案模型（draft model）快速生成多个候选token（通常以树结构形式）。
  - **服务器验证（Server Verification）**：服务器GPU（运行完整目标模型）在单个前向传播中并行验证这些候选token，输出最终token。
- 网络只传输token输出（而非中间激活值），极大降低带宽需求和通信轮次。
- 该架构保证输出分布与纯服务器推理完全相同（无损）。

### 2.2 关键技术细节

#### (a) 主动边缘起草（Proactive Edge Drafting）

- 传统投机解码中，起草和验证顺序执行。SpecEdge中，边缘GPU在发送候选token后，**立即继续起草下一批token**，而不等待验证结果。
- 若服务器验证结果与主动起草的路径完全匹配（complete draft alignment），则可以直接复用之前生成的token，消除等待延迟。
- 关键策略：初始草拟后，仅保留**具有最高累积对数概率的单个路径**作为扩展头（expansion head），继续深度展开。这使得当对齐发生时，保留的token数最多，从而最大化期望收益。
- 期望收益公式（式1）：
  \[
  E(Gain) = P_{\text{align}} \cdot P_{\text{match}|\text{align}} \cdot \left( \frac{T_{\text{draft}}}{H_{\text{expan}}} - 1 \right)
  \]
  其中 \(P_{\text{align}}\) 为对齐概率，\(P_{\text{match}|\text{align}}\) 为给定对齐下服务器额外token匹配扩展头的概率，\(T_{\text{draft}}\) 为主动起草token数，\(H_{\text{expan}}\) 为扩展头数量（此处为1）。

#### (b) 服务器端流水线感知调度（Pipeline-aware Scheduling）

- 边缘起草与服务器验证是异步的：当边缘正在起草时，服务器可能空闲。SpecEdge通过**交织多个用户请求**来消除服务器空闲气泡。
- 服务器持续验证来自不同边缘设备的已完成草案批次，同时其他请求在边缘上起草。
- 动态调整起草深度（draft tree depth），使得服务器验证时间 ≈ 边缘起草时间 + 网络RTT，以最大化系统吞吐。

#### (c) 异构请求处理

- 通过自定义注意力掩码和KV cache填充技术，将不同长度的序列统一批处理，实现高效并行验证。

### 2.3 算法流程（文字说明）

1. 初始化：边缘运行草案模型，生成初始候选token树。
2. 提交：边缘将候选token树发送给服务器。
3. 主动扩展：边缘在等待服务器验证的同时，沿最大概率路径继续生成额外token树。
4. 服务器验证：服务器使用目标模型批量验证接收到的候选token，输出接受/拒绝结果及一个额外生成的token。
5. 更新：边缘根据验证结果更新KV cache，若完全对齐则保留主动扩展的token；否则丢弃并从头起草。
6. 循环：重复步骤2-5直至生成结束符。

## 3. 实验设计

### 3.1 使用数据集

- **主要任务**：SpecBench（六种任务：多轮对话、翻译、摘要、QA、数学、RAG）。
- **补充数据集**：C4 (en)、OpenAssistant Conversations (OAsst)、WikiText-2、MTBench。

### 3.2 基准方法（Baselines）

- **Server-only（服务器-only）**：所有推理在服务器A100上完成，同样使用树形投机解码。
- **Autoregressive decoding**：纯自回归解码，不使用投机解码。
- **Layer-split（层分割）**：将部分模型层运行在边缘RTX 4090，其余在服务器A100上。
- **SpecEdge**：边缘RTX 4090起草 + 服务器A100验证。

### 3.3 对比的主要指标

- **服务器吞吐量**（tok/s）
- **成本效率**（每美元产生的千token数，1k toks/$）
- **令牌间延迟**（Inter Token Latency，ITL）

### 3.4 模型组合

- 目标模型：Qwen3-14B, Qwen3-32B, Vicuna-33B, Llama2-13B
- 草案模型：Qwen3-1.7B, Qwen3-0.6B, Sheared Llama-1.3B, Tiny Llama-1.1B, JackFram-160M
- 总共测试了多种目标-草案配对。

## 4. 资源与算力

- **服务器GPU**：NVIDIA A100 40GB（部分32B模型使用A100 80GB），部署在Google Cloud Platform。
- **边缘GPU**：NVIDIA RTX 4090（主要），另测试了RTX 4070 Ti Super、RTX 3090、RTX 2080 Ti、RTX 3060 Ti。
- **网络延迟**：平均RTT为14.07 ms（本地边缘到GCP实例）。
- **模型规模**：目标模型最大为32B参数，草案模型最小160M参数。
- **未明确说明**：训练时长、预训练/微调计算量（本文不涉及训练，仅推理）。推理时间在实验中已报告。

## 5. 实验数量与充分性

- **核心实验（表1）**：在6个SpecBench任务上，使用3种目标-草案配对（14B/1.7B、14B/0.6B、32B/1.7B），报告了吞吐、成本效率、生成token数等均值和标准差。
- **延迟分析（图6）**：针对不同batch size（1,4,6）和模型配对，展示了延迟-成本散点图。
- **消融实验（图7-10）**：
  - 服务器运行时间对比（server-only vs edge-assisted）
  - 组件获益：基础解耦 vs 加主动起草 vs 完整版（含流水线调度）
  - 生成token数/验证轮次
  - 起草深度调优
- **敏感性分析（图11-12）**：
  - 网络RTT从15ms到65ms对延迟的影响
  - 不同边缘GPU性能
- **补充实验（附录）**：
  - 其他模型和数据集（Vicuna-33B, Llama2-13B, C4, OAsst, WikiText-2, MTBench）
  - 非树形投机解码方法
  - 批量起草（单边缘GPU服务多请求）
  - 推理模式（reasoning mode）
  - 多GPU提供商成本对比
- **公平性**：所有配置生成相同输出分布，确保比较公平。实验覆盖了多种模型规模、草案模型大小、网络条件、硬件配置，且报告了标准差。

## 6. 论文的主要结论与发现

- **成本效率提升**：平均 **1.91×**（最高2.13×），主要来源于服务器吞吐量提升 **2.22×**。
- **延迟降低**：在14.07ms RTT下，令牌间延迟比纯服务器基线降低 **11.24%**（即使服务器基线无网络延迟）。
- **主动起草有效性**：显著提高每轮验证生成的token数（平均+13.21%），并有效隐藏网络延迟。
- **流水线调度必要性**：基础解耦仅获得32.76 tok/s，加主动起草后达67.89 tok/s（2.07×提升）。
- **网络鲁棒性**：在RTT低于50ms时优于服务器基线；即使65ms RTT仍具竞争力；远优于层分割方法（2.73~3.35倍延迟劣势）。
- **硬件泛化性**：多种消费级GPU均能获得加速，更强大的边缘GPU带来更大收益。
- **跨平台成本一致性**：在不同GPU提供商和云服务商下均能保持成本效率优势。

## 7. 优点

1. **创新性**：首次将投机解码解耦应用于边缘-服务器异构环境，克服了传统并行化和层分割在广域网下的局限。
2. **实用性**：仅需网络传输token，对带宽要求极低，适用于真实WAN场景。
3. **无损输出**：保证最终输出分布与服务器单独推理一致，不牺牲质量。
4. **系统设计完整**：主动起草和流水线调度有效解决了异步协同中的延迟和利用率问题，形成了完整的工程方案。
5. **实验充分**：覆盖多种模型、数据集、硬件配置、网络条件，并进行了详尽的消融和敏感性分析，结果可信度高。
6. **成本效率突出**：在延迟几乎没有牺牲甚至略有改善的情况下，显著提升了成本效率，具有很强的商业应用价值。

## 8. 不足与局限

1. **网络条件假设**：实验网络RTT为14.07ms，虽然分析了更高RTT下仍具竞争力，但极端高延迟或不可靠网络（如移动网络）下表现未知。
2. **未考虑安全性**：论文承认当前未处理不可信边缘设备参与时的安全和容错问题，仅支持分布式多用户环境，但缺乏恶意攻击、模型窃取等防护。
3. **边缘设备算力依赖**：轻量级边缘GPU（如RTX 3060 Ti）虽仍有效，但性能下降明显；极低端设备（如手机、嵌入设备）未测试。
4. **模型规模限制**：目标模型最大为32B，未测试更大规模（如70B、405B）模型。虽然设计原理可扩展，但实际部署时服务器验证延迟增加，可能影响调度均衡。
5. **批量起草评估不充分**：附录B.4对单边缘GPU服务多请求的替代方案仅测试了小batch，缺乏大规模并发下的详细分析。
6. **推理模式分析较浅**：仅报告了有无reasoning模式下的指标，未深入分析推理token的模式对性能的影响机制。
7. **成本模型简化**：仅考虑了GPU租赁成本，未计算网络带宽费用、边缘设备管理开销、软件维护成本等。
8. **公平比较问题**：服务器基线使用树形投机解码，但SpecEdge使用了主动起草和流水线调度，两者在算法上不完全对等；不过论文通过消融实验分离了贡献。

（完）
