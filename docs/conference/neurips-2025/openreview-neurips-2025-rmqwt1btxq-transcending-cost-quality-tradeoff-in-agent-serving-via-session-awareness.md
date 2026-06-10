---
title: Transcending Cost-Quality Tradeoff in Agent Serving via Session-Awareness
title_zh: 通过会话感知超越智能体服务中的成本-质量权衡
authors: "Yanyu Ren, Li Chen, Dan Li, Xizheng Wang, Zhiyuan Wu, Yukai Miao, Yu Bai"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=RmqWt1btxQ"
tags: ["query:agents-os"]
score: 8.0
evidence: 面向LLM智能体的会话感知服务系统
tldr: 现有LLM服务系统缺乏会话感知，无法优化智能体服务的独特需求。本文提出会话感知机制，通过有效的KV缓存管理和精准模型选择，打破成本-质量权衡。该方法直接优化了智能体服务的基础设施，可视为智能体操作系统的核心组件之一。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1297, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 720, \"height\": 331, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 435, \"height\": 278, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1293, \"height\": 313, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 668, \"height\": 249, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 665, \"height\": 297, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1428, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1423, \"height\": 241, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1418, \"height\": 287, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 692, \"height\": 224, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1429, \"height\": 240, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 697, \"height\": 223, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-rmqwt1btxq/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 761, \"height\": 1025, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-rmqwt1btxq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 730, \"height\": 250, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rmqwt1btxq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 660, \"height\": 172, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rmqwt1btxq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1180, \"height\": 159, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rmqwt1btxq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1175, \"height\": 179, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rmqwt1btxq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 919, \"height\": 148, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rmqwt1btxq/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 810, \"height\": 149, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rmqwt1btxq/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1297, \"height\": 806, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rmqwt1btxq/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1430, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rmqwt1btxq/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 987, \"height\": 115, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rmqwt1btxq/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1180, \"height\": 147, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-rmqwt1btxq/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 959, \"height\": 211, \"label\": \"Table\"}]"
motivation: 当前LLM服务系统未针对智能体服务优化，存在成本-质量权衡。
method: 提出会话感知的服务机制，包括KV缓存管理和模型选择优化。
result: 在保证质量的同时降低服务成本。
conclusion: 会话感知是构建高效智能体服务基础设施的关键技术。
---

## Abstract
Large Language Model (LLM) agents are capable of task execution across various domains by autonomously interacting with environments and refining LLM responses based on feedback.
However, existing model serving systems are not optimized for the unique demands of serving agents. Compared to classic model serving, agent serving has different characteristics:
predictable request pattern, increasing quality requirement, and unique prompt formatting. We identify a key problem for agent serving: LLM serving systems lack session-awareness. They neither perform effective KV cache management nor precisely select the cheapest yet competent model in each round.
This leads to a cost-quality tradeoff, and we identify an opportunity to surpass it in an agent serving system.

To this end, we introduce AgServe for AGile AGent SERVing.
AgServe features a session-aware server that boosts KV cache reuse via Estimated-Time-of-Arrival-based eviction and in-place positional embedding calibration, a quality-aware client that performs session-aware model cascading through real-time quality assessment, and a dynamic resource scheduler that maximizes GPU utilization. 
With AgServe, we allow agents to select and upgrade models during the session lifetime, and to achieve similar quality at much lower costs, effectively transcending the tradeoff. Extensive experiments on real testbeds demonstrate that AgServe (1) achieves comparable response quality to GPT-4o at a 16.5\% cost. (2) delivers 1.8$\times$ improvement in quality relative to the tradeoff curve.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大语言模型（LLM）智能体（agent）通过与环境的自主交互和反馈来执行多轮任务，但现有的 LLM 服务系统（如 vLLM、SGLang）是为常规的、单次、人类导向的查询设计的，没有针对智能体的独特工作流进行优化。
- **智能体服务的三个独特特征**：
  - 请求模式可预测且高频（间隔毫秒级，输出短）。
  - 上下文随轮次不断增长，任务难度逐渐增加。
  - 提示格式特殊（如中间截断而非前缀截断）。
- **核心问题**：现有系统缺乏会话感知（session-awareness），既无法高效复用 KV 缓存，也无法在每轮准确选择最便宜且胜任的模型，导致一个固有的成本-质量权衡：使用更强大的模型提高质量但增加成本，反之亦然。
- **整体含义**：作者识别出打破这一权衡的机会，通过利用会话的可预测性来设计会话感知的缓存管理和模型级联，从而在降低成本和延迟的同时保持高质量。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **总体架构**：AgServe 由三个主要组件构成，共同实现会话感知的智能体服务。

### 2.1 会话感知服务器（Session-Aware Server, SAS）
- **核心目标**：最大化 KV 缓存命中率，减少预填充计算。
- **关键技术**：
  - **会话 ID-序列表（SIST）**：维护每个会话的块 ID，允许按会话管理缓存。
  - **原位位置嵌入校准（In-place Positional Embedding Calibration）**：针对中间截断导致的 RoPE 位置错位，通过矩阵乘法直接更新已缓存的 KV 值（乘以旋转因子 \(e^{i\delta p\theta}\)），无需重新计算，从而重用缓存。
  - **基于预计到达时间的缓存驱逐（ETA-based Cache Eviction, ECE）**：替代传统的 LRU 策略。预测每个会话下一个请求的到达时间（ETA），优先驱逐最晚被需要的会话缓存。对于大小不同的会话缓存，使用动态规划（类背包算法）找到最优驱逐集合以最小化总等待时间（TTFT）。算法复杂度低，单次决策在 0.1ms 内。

### 2.2 会话守护客户端（Session Guard Client, SGC）
- **核心目标**：在会话生命周期内动态选择最合适的模型，避免过度杀伤（overkill）或不足（underkill）。
- **两个关键子模块**：
  - **Q-Judge**：在会话开始时评估任务难度，选择初始模型。使用基于 Chatbot-Arena 数据训练的 BERT 分类器，预测难度标签（0/1/2）。优化损失函数时对过度预测（overkill）给予更高惩罚（\(\alpha > 1\)），鼓励偏向较小模型的初始选择。
  - **R-Judge**：在运行中定期（用户可设频率）评估响应质量。基于 DistilBERT 分类器，输入包括模型大小、响应、任务、最近观察，输出是否满足质量阈值 \(\theta\)。用户可调整严格程度。当质量不达标时，采取重试（retry）或升级迁移（upgrade migration）到更强模型，也支持回滚（restoration）到上一个检查点。

### 2.3 资源调度器（Resource Scheduler, RS）
- **核心目标**：根据实时需求-供应比动态调整 GPU 分配，最大化硬件利用率。
- **实现**：
  - 将模型分为可调整（单个节点内可调，如 Llama-8B/70B）和预设（需跨节点，如 GPT-4o API）。
  - 跟踪每个模型的请求频率和缓存容量需求，计算需求-供应比。
  - 优先扩容高比率模型，缩容低比率模型，并在节点间重新分布实例，尽量将同一模型实例合并以利用并行度。

## 3. 实验设计：数据集、基准、对比方法

### 3.1 数据集与场景
- **基准**：使用 AgentBench 中的四个典型智能体任务：
  - AlfWorld (AW): 家居环境导航与操作。
  - Card Game (CG): 双人卡牌游戏（多智能体协作）。
  - Knowledge Graph (KG): 知识图谱查询。
  - Mind2Web (M2W): 真实网站导航与操作。
- **多智能体负载**：使用人工合成的请求轨迹（均匀、Gamma、泊松、突发分布），定义启动时间，不影响后续轮次。

### 3.2 对比方法
- **vLLM+**：单模型服务（Llama-8B/70B 或 GPT-4o）+ 前缀缓存 + 重试。
- **Cascade**：三级级联但禁用 R-Judge 和 Q-Judge，始终从小模型开始，仅处理显式质量问题。
- **RouteLLM**：基于训练的路由器（BERT 路由器，偏好小模型），无会话意识。
- **Llumnix++**：基于 vLLM 的 SoTA 多实例系统，扩展支持 Llama-3 并集成 AgServe 的 QMM。

### 3.3 评估指标
- **质量**：根据 AgentBench 评分机制，综合正常行为（25%）、任务处理能力（50%）、效率（25%）给出 0-100 分数。
- **成本**：包括硬件租赁（根据云服务定价）和 OpenAI API 费用。
- **延迟**：端到端 (e2e) 延迟，TTFT，以及缓存命中率。

## 4. 资源与算力

- **测试平台**：
  - 两个节点，各 4 块 A6000 GPU（48GB 显存），PCIe 互联。
  - 两个节点，各 8 块 A800 GPU（80GB 显存），PCIe 互联。
- **模型**：Llama-3 8B 和 70B（开源），GPT-4o（API）。
- **训练**：
  - Q-Judge 基于 BERT，在 Chatbot-Arena 33k 数据上训练 10 epochs，用时 2.9 小时，使用 1 块 A6000。
  - R-Judge 基于 DistilBERT，同样数据上训练 10 epochs，用时 17 分钟。
- **推理配置**：Llama-8B 每实例 1/4 节点（约 2 GPU），Llama-70B 每实例 1 节点（8 GPU）。动态分配实验中使用了单 A800 节点。

## 5. 实验数量与充分性

- **端到端级联服务**：在四个智能体上分别进行成本-质量曲线绘制，每种方法重复多次取平均值（文中未给出具体重复次数，但提到“运行昂贵”，推测至少 3 次）。
- **多智能体服务**：四种不同分布（Uniform, Gamma, Poisson, Burst），每种 100 个智能体启动。
- **消融实验**：
  - SAS 缓存：对比 vLLM 与 AgServe 的延迟、质量、缓存命中率（不同批量大小 5-8），以及 TTFT 分布。
  - SGC QMM：R-Judge 与人类标签的一致率（95.2% 召回），Q-Judge 准确率，以及各组件开销。
  - RS 动态分配：对比两种静态配置（FS1, FS2）的延迟。
- **额外实验**：人类判决对比、大规模模拟（60 节点，分布式调度）。
- **充分性评价**：实验覆盖了主要组件（缓存、模型选择、资源调度），对比了有竞争力的基线（vLLM+, RouteLLM, Llumnix++），并在多个智能体类型和负载分布上验证。消融实验逐个分析了关键设计的贡献。总体实验设计较为充分和公平。但多智能体实验的请求轨迹为合成数据，缺乏真实智能体用户行为数据；成本计算基于云服务零售价，可能并非实际部署价格。

## 6. 论文的主要结论与发现

1. **打破成本-质量权衡**：AgServe 在相似质量（与 GPT-4o 相当）下成本仅为 GPT-4o 的 16.5%；在相同成本下质量比权衡曲线提升 1.8 倍。
2. **多智能体环境有效性**：相比 Llumnix++，成本降低 64%，质量提高 1.6 倍；相比 RouteLLM，成本更低且质量相当。
3. **会话感知缓存显著提升效率**：ECE 策略相比 LRU 缓存命中率提高 2.86 倍；结合中间截断原位校准，轮次延迟降低最多 50%。
4. **动态资源分配加速**：相比静态分配，动态分配使端到端延迟降低约 14%（P90），相比单一模型服务降低 49% 平均延迟。
5. **QMM 质量维护**：R-Judge 对不满意响应召回率达 95.2%，且开销极小（每次判断 0.03s）。

## 7. 优点：方法或实验设计上的亮点

- **创新性**：首次提出会话感知的智能体服务系统，突破了传统 LLM 服务的会话无意识限制。
- **技术贡献**：
  - 原位位置嵌入校准：巧妙解决了中间截断带来的 RoPE 不一致问题，无需额外解耦缓存。
  - ETA 驱动的缓存驱逐：利用智能体请求的可预测性，比 LRU 更高效。
  - 质量评估双模块（Q-Judge 和 R-Judge）：结合离线训练和在线监控，动态选择模型层级。
- **实验设计**：
  - 使用标准基准 AgentBench，涵盖多种智能体类型（导航、游戏、知识查询、网页操作）。
  - 对比方法覆盖现有主流：单模型、路由、级联、多实例系统，且对最强基线进行扩展（Llumnix++）。
  - 消融实验系统逐一验证各组件效果。
  - 考虑了成本和服务质量的多面指标，并绘制成本-质量曲线。

## 8. 不足与局限

- **R-Judge 敏感性**：阈值 \(\theta\) 影响性能；极端设置下（\(\theta=0\) 或 \(\theta=1\)）退化为极端策略。虽然性能与人类相当，但若数据不足可能欠佳。
- **节点路由简化**：受限于测试床规模，AgServe 将每个会话绑定到特定实例（首次调度时选最空闲的），未实现飞行中会话迁移。作者指出未来可结合长度预测进行负载均衡。
- **大规模验证不足**：实际实验限于 2 节点（多数）或 1 节点，多节点分布式仅做了模拟（附录 F），未在真实大规模集群上验证。
- **数据集的局限性**：训练数据来自 Chatbot-Arena，非专门针对智能体任务；多智能体轨迹为合成生成，缺乏真实用户行为模式。
- **成本模型假设**：使用云服务零售价计算开源模型成本，但实际自建或预留实例可能更低，导致绝对数值有偏差，但相对优势仍成立。
- **模型层级固定**：当前使用三层（8B/70B/API），是否适用更多层级或不同架构模型未充分探讨。

（完）
