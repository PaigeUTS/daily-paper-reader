---
title: "HyGen: Efficient LLM Serving via Elastic Online-Offline Request Co-location"
title_zh: HyGen：通过弹性在线-离线请求共置实现高效LLM服务
authors: "Ting Sun, Penghan Wang, Fan Lai"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=cQxLCVa9u7"
tags: ["query:agents-os"]
score: 7.0
evidence: 高效LLM服务系统，通过弹性共置在线/离线请求处理异构SLO
tldr: HyGen提出了一种干扰感知的LLM服务系统，通过在线与离线请求的弹性共置来提升资源利用率，其核心包括延迟预测器和SLO感知分析器以管理性能干扰，实验表明在保持服务质量的同时显著提高吞吐量，为AI操作系统中的资源调度提供了有效方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 517, \"height\": 766, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 692, \"height\": 791, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1427, \"height\": 514, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1430, \"height\": 515, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 649, \"height\": 286, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 630, \"height\": 306, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 366, \"height\": 286, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 780, \"height\": 361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1375, \"height\": 326, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 671, \"height\": 282, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 743, \"height\": 339, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 674, \"height\": 306, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 687, \"height\": 320, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 687, \"height\": 317, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-cqxlcva9u7/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 728, \"height\": 262, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-cqxlcva9u7/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1441, \"height\": 1127, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-cqxlcva9u7/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1432, \"height\": 1324, \"label\": \"Table\"}]"
motivation: 专用机器部署LLM工作负载导致资源利用率低下。
method: 提出干扰感知的共置方案，包含延迟预测与SLO感知分析。
result: 在线离线共置显著提升资源利用率，同时满足SLO。
conclusion: 弹性共置是优化LLM服务器资源利用的有效手段。
---

## Abstract
Large language models (LLMs) have facilitated a wide range of applications with distinct service-level objectives (SLOs), from latency-sensitive online tasks like interactive chatbots to throughput-oriented offline workloads like data synthesis. The existing deployment model, which dedicates machines to each workload, simplifies SLO management but often leads to poor resource utilization. This paper introduces HyGen, an interference-aware LLM serving system that enables efficient co-location of online and offline workloads while preserving SLOs. HyGen incorporates two key innovations: (1) performance control mechanisms, including a latency predictor to estimate batch execution time and an SLO-aware profiler to quantify latency interference, and (2) SLO-aware offline scheduling policies that maximize serving throughput and prevent starvation. Our evaluation on production workloads shows that HyGen achieves up to 3.9-5.8× throughput gains over online and hybrid serving baselines, while ensuring latency SLOs. The code of HyGen is publicly available at https://github.com/UIUC-MLSys/HyGen.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **背景**：大语言模型（LLM）服务面临两类截然不同的负载：延迟敏感的在线任务（如聊天机器人）和吞吐优先的离线任务（如数据合成）。现有部署通常为每种任务专用机器，简化了SLO管理，但导致资源利用率低下，尤其在在线请求呈昼夜波动和分钟级突发变化时，需按峰值配置资源，造成大量闲置。
- **问题**：如何在不违反在线SLO的前提下，将在线与离线请求高效共置于同一推理引擎，从而提升资源利用率和整体吞吐量？核心挑战包括：多样化延迟SLO、请求到达和资源需求的不确定性、以及共置带来的性能干扰（如头部阻塞、长输入拖慢短查询）。
- **核心含义**：通过弹性共置，在低在线负载时“填充”离线请求，可显著提高GPU利用率，同时保证在线服务质量。这一方向对降低LLM服务部署成本、提升系统效率具有重要意义。

## 2. 论文提出的方法论

- **核心思想**：设计一个干扰感知的LLM服务系统HyGen，采用两阶段调度：先保障在线请求，再利用剩余容量弹性调度离线请求。关键组件包括延迟预测器和SLO感知分析器，用于精确控制共置干扰。
- **关键技术细节**：
  - **延迟预测器**：基于线性回归（LR）模型，特征包括预填充token总数 \(S_p\)、解码token总数 \(S_d\)、预填充token平方 \(S_p^2\)、预填充请求数 \(N_p\)、解码请求数 \(N_d\)，公式为 \(T_{batch}=f(S_p, S_d, S_p^2, N_p, N_d)\)。训练数据通过对目标硬件在不同批次组成下进行系统化性能 profiling 收集，模型推理时间为常数级（~18μs/次）。
  - **SLO感知分析器**：通过离线 profiling 确定一个“延迟预算”（latency budget），该预算作为批次执行时间的上限，确保在线请求的TTFT和TBT等指标满足SLO。采用二分搜索找出满足SLO的最大预算值。
  - **两阶段调度算法**（Algorithm 1）：第一阶段从在线请求队列中选出请求，第二阶段利用剩余延迟预算、内存预算和分块大小，从离线请求中尽可能加入请求。支持基于优先级的抢占以保护在线请求。
  - **SLO感知离线调度策略**：引入前缀共享最大化（Prefix Sharing Maximization, PSM）策略，将离线请求组织成前缀树（Trie树），按深度优先顺序调度以最大化KV缓存复用。扩展版本结合请求新鲜度（通过平衡二叉搜索树）以避免饥饿，使用效用比平衡效率与公平。
- **算法流程文字说明**：每个调度步骤中，主进程发送上次批次元数据到消息队列，离线调度器异步计算当前状态并执行调度模拟，生成离线请求决策后返回给主进程。支持流水线并行时维护K步的历史记录。

## 3. 实验设计

- **数据集/场景**：
  - 在线负载：Azure LLM Inference trace 2023（真实生产一小时的对话请求记录），以及 Mooncake trace（来自Kimi服务）。
  - 离线负载：arXiv摘要数据集（长文档总结）、CNN/DailyMail摘要数据集、MMLU（问答）。
- **Benchmark**：对比方法包括：
  - Sarathi（纯在线服务基准）
  - Sarathi-offline（纯离线服务，优化分块大小以达最高吞吐）
  - Sarathi++（在Sarathi上实现HyGen的在线优先调度策略但无SLO感知）
  - HyGen*（在Sarathi++基础上加入离线QPS控制，模拟SLO感知但无细粒度预测）
- **评估指标**：延迟指标（平均TTFT、P99 TTFT、平均TBT、P99 TBT）和吞吐量（tokens per second, TPS；queries per second, QPS）。

## 4. 资源与算力

- **硬件配置**：三个服务器：
  - 4× NVIDIA A100 GPU（40GB VRAM）
  - 4× NVIDIA A40 GPU（48GB VRAM）
  - 1× NVIDIA A5000 GPU（24GB VRAM）
  - 所有服务器：64 CPU核，256GB DDR4 RAM，1.5TB NVMe SSD。
- **模型**：主要使用Llama2-7B（A100）、Qwen-14B（A40）；消融实验使用Sheared-LLaMA-2.7B、Mistral-7B、Yi-34B（TP=2, PP=2）。
- **训练时长**：LR模型训练约15ms（80,000样本，CPU上）。
- **运行开销**：每次调度迭代约18μs。
- **说明**：论文未明确说明总实验时长，但提供了部署细节和开销数据。

## 5. 实验数量与充分性

- **实验数量**：涵盖7组主要实验（端到端性能、吞吐量对比、消融实验），以及多个消融研究：
  - 延迟预测器精度（图5）
  - 前缀共享吞吐提升（图6）
  - SLO感知分析器效果（图7）
  - 时间动态分析（图8）
  - 模型并行的影响（Yi-34B，图9）
  - 不同在线QPS下的SLO满足（图10）
  - 多SLO同时满足（图11）
  - 不同离线数据集（CNN/DailyMail，图12；Mooncake trace，图14）
  - 不同硬件（A5000，图15）
  - 预测器鲁棒性（图16）
  - 在线速率对离线吞吐的影响（图17）
- **充分性与公平性**：
  - 消融实验全面，覆盖模型、数据集、硬件、并行策略、SLO类型、在线负载强度等维度。
  - 对比基线经过优化（如Sarathi-offline使用最佳分块大小提升~12%吞吐）。
  - 实验设置合理，结果报告了SLO满足和吞吐提升，且分析了鲁棒性。
  - 不足：所有实验基于特定模型和跟踪，通用性需进一步验证；未涉及多模型或混合LoRA场景。

## 6. 论文的主要结论与发现

1. **HyGen能严格满足在线SLO**：在平均TBT、P99 TBT、平均TTFT、P99 TTFT等指标下，HyGen均能控制在容忍度范围内（图3），而SLO无感知的Sarathi++则无法控制。
2. **HyGen显著提升服务吞吐**：相比Sarathi，HyGen实现3.87-5.84×的吞吐提升（图4）；相比HyGen*（简化版本），HyGen也持续更高，接近纯离线系统Sarathi-offline的84.3%吞吐。
3. **延迟预测器高精度**：在Llama2-7B和Qwen-14B上，平均绝对百分比误差分别为1.78%和1.07%（图5）。
4. **前缀共享最大化策略有效**：可达4×离线吞吐增益（图6）。
5. **SLO感知分析器至关重要**：若不使用，HyGen的延迟控制会偏离SLO（图7）。
6. **HyGen动态适应在线负载**：在线流量低谷时更积极调度离线请求，高峰时减少（图8）。
7. **方法对模型并行、不同数据集、硬件、预测器精度均具鲁棒性**：消融实验证实其泛化能力。

## 7. 优点

- **方法创新**：
  - 首次系统性地将在线与离线LLM服务共置于同一引擎，并设计干扰感知的调度框架。
  - 轻量级线性回归延迟预测器，训练快（~15ms）、推理快（~18μs），易于部署。
  - SLO感知分析器将宏观预算与微观预测结合，实现精确控制。
  - 前缀共享最大化策略（PSM）及公平性扩展，兼顾效率与公平。
- **实验设计**：
  - 使用真实生产跟踪（Azure、Mooncake），保证负载真实性。
  - 对比基线包含SLO无知和简化版本，清晰展示各部件的贡献。
  - 消融实验全面，覆盖模型、硬件、并行策略、数据集、SLO类型等多种维度，验证鲁棒性。
  - 开源代码，促进可复现性。

## 8. 不足与局限

- **实验覆盖**：仅针对特定模型（Llama2-7B、Qwen-14B等）和特定生产痕迹（Azure、Mooncake），对更广泛架构（如MoE）和更长上下文场景未充分验证。
- **潜在偏差**：假设预测器在动态环境下保持稳定，但高动态或对抗性输入可能使预测退化；延迟预算基于离线 profiling，未考虑在线负载的极端突发。
- **应用限制**：
  - 当前仅支持单模型共置，未考虑多模型或LoRA适配器场景（如Punica、dLoRA）。
  - 与集群级路由（如Preble）的集成细节未深入探讨。
  - 对流水线并行的支持依赖消息队列和K步历史，调度延迟可能随并行度增加而增加。
- **其他**：论文未讨论节能或功耗约束，也未涉及大规模集群部署的端到端性能。虽提到扩展版PSM可防饥饿，但未在实验中展示其效果。

（完）
