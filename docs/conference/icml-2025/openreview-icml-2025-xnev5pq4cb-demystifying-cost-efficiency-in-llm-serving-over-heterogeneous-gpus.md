---
title: Demystifying Cost-Efficiency in LLM Serving over Heterogeneous GPUs
title_zh: 揭秘异构GPU上LLM服务的成本效率
authors: "YOUHE JIANG, Fangcheng Fu, Xiaozhe Yao, Guoliang HE, Xupeng Miao, Ana Klimovic, Bin CUI, Binhang Yuan, Eiko Yoneki"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=xnEv5pq4cB"
tags: ["query:agents-os"]
score: 9.0
evidence: 研究在异构GPU上服务LLM的成本效率
tldr: 针对当前LLM服务多采用同构GPU导致成本效率低的问题，系统研究异构GPU资源池上的服务优化。通过综合基准测试发现，根据不同请求的资源需求匹配不同GPU类型可显著降低成本效率，并设计调度策略实现最优分配，实验表明相比同构方案可节省大量成本且不降低服务质量。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 816, \"height\": 331, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 825, \"height\": 316, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1764, \"height\": 581, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1750, \"height\": 608, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 844, \"height\": 676, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 846, \"height\": 295, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 841, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 847, \"height\": 302, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 830, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 824, \"height\": 325, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1764, \"height\": 585, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1750, \"height\": 1200, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1745, \"height\": 1200, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 875, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 865, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-xnev5pq4cb/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 840, \"height\": 378, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-xnev5pq4cb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 853, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xnev5pq4cb/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 832, \"height\": 671, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xnev5pq4cb/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 769, \"height\": 159, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xnev5pq4cb/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 960, \"height\": 249, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xnev5pq4cb/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 916, \"height\": 204, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xnev5pq4cb/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 953, \"height\": 384, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-xnev5pq4cb/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 883, \"height\": 204, \"label\": \"Table\"}]"
motivation: LLM请求多样性导致固定同构GPU集群成本效率低下，异构GPU可更好匹配不同请求的资源需求。
method: 对多种GPU类型和请求特征进行系统基准测试，分析成本效率，并设计基于需求感知的请求调度策略。
result: "在真实云平台数据集上，建议的异构调度策略相比同构基线可降低30%以上成本，同时满足延迟约束。"
conclusion: 异构GPU资源池是提升LLM服务成本效率的关键方向，为AI操作系统资源调度提供实用指导。
---

## Abstract
Recent advancements in Large Language Models (LLMs) have led to increasingly diverse requests, accompanied with varying resource (compute and memory) demands to serve them. However, this in turn degrades the cost-efficiency of LLM serving as common practices primarily rely on homogeneous GPU resources. In response to this problem, this work conducts a thorough study about serving LLMs over heterogeneous GPU resources on cloud platforms. The rationale is that different GPU types exhibit distinct compute and memory characteristics, aligning well with the divergent resource demands of diverse requests. Particularly, through comprehensive benchmarking, we discover that the cost-efficiency of LLM serving can be substantially optimized by meticulously determining GPU composition, deployment configurations, and workload assignments. Subsequently, we design a scheduling algorithm via mixed-integer linear programming, aiming at deducing the most cost-efficient serving plan under the constraints of price budget and real-time GPU availability. Remarkably, our approach effectively outperforms homogeneous and heterogeneous baselines under a wide array of scenarios, covering diverse workload traces, varying GPU availablilities, and multi-model serving. This casts new light on more accessible and efficient LLM serving over heterogeneous cloud resources.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：当前大语言模型（LLM）服务普遍使用同构GPU资源，但LLM请求的输入/输出长度日益多样化（工作负载异构性），产生截然不同的计算和内存需求（预填阶段计算密集，解码阶段内存密集）。同构GPU难以同时高效满足多样化的资源需求，导致成本效率低下。
- **研究动机**：探索是否可以利用云平台上异构GPU资源（不同GPU具有不同的计算能力、内存带宽和容量）来提升LLM服务的成本效率，并回答“如何最大化成本效率”这一关键问题。
- **整体含义**：通过系统研究揭示，精心选择GPU组成、部署配置和工作负载分配可以显著优化成本效率，为在云环境中经济高效地部署LLM服务提供了新范式。

## 2. 方法论：核心思想、关键技术细节

### 2.1 核心思想

- 将LLM服务优化分解为三个联合优化的因素：
  1. **GPU组成（GPU Composition）**：从云平台可用的GPU池中选择类型和数量，满足预算和资源约束。
  2. **部署配置（Deployment Configuration）**：将租用的GPU组织成服务组，确定每个模型副本的并行策略（数据并行DP、张量并行TP、流水线并行PP）。
  3. **工作负载分配（Workload Assignment）**：将不同类型的请求分配到最匹配的模型副本上，同时平衡负载。

### 2.2 关键技术细节

- **基准测试发现（Observations）**：
  - 异构GPU适合管理模型和负载多样性（例如数据中心GPU擅长计算密集型，工作站GPU擅长内存密集型，消费级GPU适合小模型）。
  - 最优部署配置因模型、负载和GPU类型而异，不应用统一配置。
  - 工作负载分配需与GPU组成和部署配置协同优化。

- **MILP调度算法**：
  - 变量：\(d_n\)（类型n的GPU数量）、\(y_c\)（配置c的副本数）、\(x_{c,w}\)（配置c处理负载w的比例）。
  - 决策变量：\(y_c \in \{0,1,2,\dots\}\)（整数），\(x_{c,w} \in [0,1]\)（连续）。
  - 目标：最小化整体makespan \(T\)。
  - 约束：
    - 每个负载完整处理：\(\sum_{c} x_{c,w} = 1\)
    - 每个配置的完成时间不超过\(T\)：\(\sum_w \frac{x_{c,w} f_w}{y_c h_{c,w}} \le T\)
    - 激活耦合：\(x_{c,w} \le y_c\)
    - 预算：\(\sum_c o_c y_c \le B\)
    - GPU可用性：\(\sum_c d_n(c) y_c \le a_n\)
  - 复杂度：理论上指数级，实际通过**二进制搜索**、启发式规则（内存约束、连接约束、限制TP在单机内等）加速。

- **二进制搜索**：将最小化\(T\)转化为对候选\(\hat{T}\)的可行性检查，利用背包近似加速，搜索时间减少约4倍，性能偏差<1%。

- **多模型扩展**：引入模型类型维度，约束跨模型共享GPU和预算。

## 3. 实验设计

### 3.1 数据集/场景

- **模型**：Llama3-8B、Llama3-70B。
- **工作负载痕迹**：
  - **Trace 1**：瑞士AI中心真实一个月痕迹（500k+请求）。
  - **Trace 2**：Azure-Trace（生产轨迹）。
  - **Trace 3**：WildGPT数据集。
  - 每个痕迹包含9种工作负载类型（按输入/输出长度组合：长/短输入 × 长/短输出）。
- **GPU类型**：6种云GPU：A6000、A40、L40、A100、H100、4090（涵盖数据中心、工作站、消费级）。
- **预算设置**：15、30、60 $/h。
- **GPU可用性**：从Vast.ai获取4种实时可用性设置（Table 4）。

### 3.2 基准（Benchmark）与对比方法

- **同构基线**：分别使用H100（数据中心）、A6000（工作站）、4090（消费级）作为同构集群，并利用算法优化其部署和分配。
- **异构基线**：
  - **HexGen**：固定GPU组成下的异构服务框架。
  - **Helix**：基于最大流和MILP的异构部署优化。
- **消融实验**：分别关闭GPU组成优化、部署配置优化、工作负载分配优化，评估各自贡献。

### 3.3 评估指标

- 吞吐量（req/s）
- 百分位延迟（P10-P100）

## 4. 资源与算力

- **GPU型号及数量**：实验中使用了A6000、A40、L40、A100、H100、4090等6种GPU，具体数量取决于实时可用性和预算。例如预算60 $/h时可租用多达20台H100。
- **训练时长**：本文聚焦推理服务，未涉及模型训练，因此没有训练时长信息。
- **推理集群**：数据中心GPU（H100/A100）通过NVLink（300 GB/s）互联，工作站/消费级GPU通过PCIe（60 GB/s），服务器间通过以太网（5 Gb/s）。所有实验基于vLLM框架。

## 5. 实验数量与充分性

- **实验组数**：包含端到端实验（3个痕迹 × 2个模型 × 3个预算 × 4种可用性 = 72组主要对比）、消融实验（3个因素 × 2个痕迹 × 2个预算 = 12组）、与HexGen对比（2个预算 × 3个痕迹 = 6组）、与Helix对比（2个模型）、算法效率实验、多模型扩展实验、预算敏感性实验等，共计约100余组实验。
- **充分性与公平性**：
  - **充分**：覆盖了多种真实工作负载、不同预算和GPU可用性场景，进行了消融和与最先进异构系统的对比。
  - **客观公平**：同构基线也使用了本文算法优化配置，HexGen对比使用了其最优和统一组成两种设置，Helix对比使用了其最优单集群情况，方法完备。

## 6. 主要结论与发现

- **性能提升**：在相同预算下，本文方法相比最优同构基线：
  - 吞吐量提升最高**41%**，平均**20%**。
  - 延迟降低最高**54%**，平均**20%**。
- 优于现有异构框架HexGen（平均高14%–29%）和Helix（25%–35%）。
- **三个因素贡献**：消融实验表明，GPU组成优化贡献约20%性能提升，部署配置优化约33%，工作负载分配约29%，三者联合优化不可或缺。
- **算法效率**：二进制搜索相比原生MILP搜索时间减少约4倍，解质量偏差<1%。
- **多模型服务**：在同时服务Llama3-8B和70B时仍能获得最高35%的性能提升。
- **预算敏感性**：预算越高，性能差距缩小（因云资源有限，同构基线可线性扩展）。

## 7. 优点

- **系统级视角**：首次联合优化GPU组成、部署配置和工作负载分配，而非仅优化单一方面。
- **实用性**：考虑云平台真实的GPU可用性变化和用户预算约束，贴近实际部署。
- **可扩展性**：二进制搜索和启发式规则使算法适用于大规模集群，并支持多模型场景。
- **全面基准测试**：对6种GPU、多种模型和负载进行了详细基准测试，揭示关键见解，具有高参考价值。
- **公平比较**：同构基线也使用相同调度算法优化，消除方法差异。

## 8. 不足与局限

- **离线调度假定**：当前MILP基于静态工作负载（已知所有请求），未考虑动态到达和排队。论文仅简要讨论了在线重规划思路，缺乏完整在线调度方案。
- **求解时间**：尽管二进制搜索加速，但求解时间仍随GPU数量和配置组合增加而增长（文中显示48个GPU时搜索时间约115秒），实时性可能受限。
- **模型版本限制**：仅评估了Llama3-8B和70B，未覆盖MoE模型（如Mixtral）或更大模型（如DeepSeek-V3）。
- **网络异构性简化**：假设TP仅限单机内，PP跨机器，但未细致建模不同机器间网络带宽差异对性能的影响。
- **估计误差**：Profiling估计与实际延迟误差在4%–7%，可能影响最优配置选择。
- **忽略能量效率**：仅考虑经济成本（$），未评估不同GPU的功耗和碳足迹。
- **单一时间槽**：所有请求假设同时到达，未模拟时间变化的工作负载模式（如突发）。

（完）
