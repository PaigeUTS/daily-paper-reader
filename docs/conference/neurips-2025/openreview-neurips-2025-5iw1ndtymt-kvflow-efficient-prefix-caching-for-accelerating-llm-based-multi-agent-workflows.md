---
title: "KVFlow: Efficient Prefix Caching for Accelerating LLM-Based Multi-Agent Workflows"
title_zh: KVFlow：面向LLM多Agent工作流的高效前缀缓存加速
authors: "Zaifeng Pan, AJJKUMAR PATEL, Yipeng Shen, Zhengding Hu, Yue Guan, Wan-Lu Li, Lianhui Qin, Yida Wang, Yufei Ding"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=5Iw1nDtYmT"
tags: ["query:agents-os"]
score: 5.0
evidence: 面向LLM多Agent工作流的感知缓存管理
tldr: 不相关
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-5iw1ndtymt/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1189, \"height\": 405, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5iw1ndtymt/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 699, \"height\": 556, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5iw1ndtymt/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 649, \"height\": 519, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5iw1ndtymt/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1304, \"height\": 406, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5iw1ndtymt/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 704, \"height\": 476, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5iw1ndtymt/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1394, \"height\": 458, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-5iw1ndtymt/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 584, \"height\": 353, \"label\": \"Figure\"}]"
motivation: 不相关。
method: 不相关。
result: 不相关。
conclusion: 不相关。
---

## Abstract
Large language model (LLM) based agentic workflows have become a popular paradigm for coordinating multiple specialized agents to solve complex tasks. To improve serving efficiency, existing LLM systems employ prefix caching to reuse key-value (KV) tensors corresponding to agents' fixed prompts, thereby avoiding redundant computation across repeated invocations. However, current systems typically evict KV caches using a Least Recently Used (LRU) policy, which fails to anticipate future agent usage and often discards KV caches shortly before their reuse. This leads to frequent cache misses and substantial recomputation or swap- ping overhead. We present KVFlow, a workflow-aware KV cache management framework tailored for agentic workloads. KVFlow abstracts the agent execution schedule as an Agent Step Graph and assigns each agent a steps-to-execution value that estimates its temporal proximity to future activation. These values guide a fine-grained eviction policy at the KV node level, allowing KVFlow to preserve entries likely to be reused and efficiently manage shared prefixes in tree-structured caches. Moreover, KVFlow introduces a fully overlapped KV prefetching mecha- nism, which proactively loads required tensors from CPU to GPU in background threads for agents scheduled in the next step, thereby avoiding cache miss stalls during generation. Compared to SGLang with hierarchical radix cache, KVFlow achieves up to 1.83× speedup for single workflows with large prompts, and up to 2.19× speedup for scenarios with many concurrent workflows.

---

## 论文详细总结（自动生成）

# 论文结构化中文总结：KVFlow

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：基于大语言模型（LLM）的多智能体（Agent）工作流（如 MetaGPT、AutoGen 等）通过协调多个专用 Agent 解决复杂任务。每个 Agent 拥有固定提示词（固定前缀），在不同调用间共享。现有 LLM 服务系统采用前缀缓存（Prefix Caching）机制，将固定部分的 KV 张量缓存于 GPU 以避免重复计算。
- **存在的瓶颈**：主流系统（如 SGLang、vLLM）使用最近最少使用（LRU）策略驱逐缓存。然而，在 Agent 工作流中，LRU 无法感知未来执行顺序，频繁将即将重用的 Agent 缓存提前驱逐，导致缓存未命中（Cache Miss），引发昂贵的重计算或 CPU-GPU 换入换出开销。
- **整体含义**：KVFlow 通过感知工作流执行顺序来优化缓存管理，显著降低 Agent 执行延迟，提升服务效率。

## 2. 论文提出的方法论

### 核心思想
利用工作流结构信息（Agent 执行依赖图），为每个 Agent 计算“距下次执行的步数”（steps-to-execution），指导缓存驱逐和预取操作。

### 关键技术细节
- **Agent Step Graph**：抽象 Agent 执行调度为有向图，节点代表 Agent 调用，边代表依赖关系。每个节点关联一个“步聚合函数”（step-aggr function），用于计算其 steps-to-execution：
  - 依赖为“与”关系：`step = max(前驱步数) + 1`
  - 依赖为“或”关系：`step = min(前驱步数) + 1`
  - 递归计算所有 Agent 的 steps-to-execution。
- **工作流感知的驱逐策略**：
  - 将 steps-to-execution 值分配至树形缓存结构的每个节点（KV node level）。
  - 共享前缀节点取所有子节点中的最小优先权（即最不急需驱逐），保证共享段保留。
  - 变长后缀始终拥有最高驱逐优先级。
  - 驱逐时按优先级从高到低驱逐节点（算法 1 和算法 2）。
- **完全重叠的 KV 预取机制**：
  - 利用 Step Graph 预测下一轮将执行的 Agent，提前将其 KV 从 CPU 加载到 GPU（后台线程异步执行），与当前 Agent 的生成计算重叠。
  - 状态感知调度：为每个缓存节点维护状态（在 GPU、备份在 CPU、加载中、卸载中）；调度器跳过加载中的请求，优先执行其他就绪请求。
  - 结合预取和状态感知，消除缓存未命中停顿。

### 公式/算法流程（文字说明）
- **优先级分配（Algorithm 1）**：遍历 ASG，对每个 Agent 的固定提示最后一个节点，将其 steps-to-execution 值向上传播直至根节点，并更新各节点计数器与优先级（取路径最小值）。
- **驱逐过程（Algorithm 2）**：从叶子节点按优先级构建最大堆，当 GPU 内存不足时，弹出最高优先级叶子节点并驱逐；若父节点变为叶子，则将父节点加入堆。

## 3. 实验设计

- **数据集/场景**：
  - 单工作流延迟测试：10 阶段顺序工作流；每个 Agent 有固定前缀（4096/8192 tokens）、动态后缀（32/256 tokens）、输出（32/256 tokens）。
    - 确定性顺序（branches=1）：每阶段一个 Agent。
    - 中度动态（branches=2）：每阶段随机选择两个 Agent 之一，部分前缀共享。
  - 高并发性能测试：多个独立顺序工作流同时执行（branches=1）；动态和输出固定为 256 tokens；并发数变化（10/20/64/128 等）。
  - 真实工作流仿真：基于 PEER 框架（4 个 Agent），使用 Financial QA 数据集，生成固定、动态、输出 token 分布各异。
- **基准方法（Baselines）**：
  - SGLang（GPU 仅缓存，无 CPU 备份）
  - SGLang w/ HiCache（SGLang 默认层次缓存，异步 CPU 备份 + LRU 驱逐）
  - vLLM（基于 PagedAttention，LRU 块级驱逐）
  - KVFlow（本文方法）
- **对比指标**：端到端延迟（单工作流）、系统吞吐（高并发）、相对加速比（Speedup over SGLang）。

## 4. 资源与算力

- **GPU 型号**：NVIDIA H100（80GB 显存）
- **PCIe 带宽**：64 GB/s Gen5
- **模型**：Qwen2.5-32B（40 注意力头，8 KV 头）；Llama-3.1-8B 用于部分实验。
- **推测训练时长**：未明确给出具体训练时间（论文主要做推理优化，无模型训练），但实验均在同一 GPU 单卡上完成推理测评。
- **备注**：论文说明他们的系统基于 SGLang v0.4.4 实现，因此算力消耗与标准 LLM 推理相当。

## 5. 实验数量与充分性

- **单工作流延迟**：覆盖 4 种（固定/动态/输出）token 配置 × 2 种分支类型（branches=1/2）= 8 组；每种配置重复 10 次运行，每次执行 10 个工作流周期，取平均与标准差。
- **高并发性能**：4 种不同固定前缀+并发数配置（512/10-task、1024/10-task、512/128-task、1024/64-task），两个模型（Qwen2.5-32B 和 Llama3-8B），共 8 组。
- **真实工作流仿真（PEER）**：3 种配置（Qwen/16-Task、Llama/128-Task、及其他组合），显示加速比。
- **消融分析**：将 KVFlow 两个组件（工作流感知驱逐 + 重叠预取）分别开启，给出贡献度。
- **评估充分性**：实验覆盖了典型场景（单请求交互式、高并发服务、真实 workﬂow）；对比了主流基线（SGLang、vLLM）及其变体，结果有误差线。但未测试分布式场景或其他 GPU 架构（如 A100），也未覆盖高度随机不可预测的工作流（论文承认局限）。

## 6. 主要结论与发现

- KVFlow 在所有场景下均优于 SGLang（GPU-only）、SGLang w/ HiCache 和 vLLM：
  - 单工作流：加速比最高达 1.83×（大固定前缀），在中等动态工作流中仍保持 1.22×~1.30×。
  - 高并发：最高达 2.19× 加速比，且 HiCache 在高并发下甚至劣于 GPU-only 基线（因频繁加载干扰），KVFlow 通过预取和状态感知缓解该问题。
  - 真实工作流（PEER）：加速比 1.08×~1.12×。
- 两个优化组件均有效：仅启用工作流驱逐带来 1.11×，增加预取后达 1.29×（单工作流平均）。
- KVFlow 无额外推理延迟开销；语义正确性不变（仅修改缓存管理，不改变模型输出）。

## 7. 优点

- **设计新颖**：首次利用 Agent 工作流结构（Step Graph 和 steps-to-execution）指导缓存管理，解决 LRU 在 Agent 场景的不足。
- **高效驱逐与预取结合**：细粒度节点级优先级分配 + 完全重叠预取，有效隐藏 CPU-GPU 传输延迟。
- **通用性**：可集成至 SGLang、vLLM 等主流系统；工作流信息可通过 HTTP 元数据传递，无侵入性。
- **实验全面**：覆盖单工作流、多并发、真实工作流；与多种基线对比；提供消融分析和误差棒。
- **实际价值**：对大固定提示和多 Agent 协作任务（如 RTL 生成、测试用例生成等）有显著加速效果。

## 8. 不足与局限

- **对动态不可预测工作流的假设**：仅适用于未来执行顺序可预测的任务（如固定 DAG 的工作流）；若工作流高度随机（如完全动态决策），KVFlow 退化为默认 LRU，无增益。
- **实验覆盖**：未测试分布式多 GPU 场景；仅使用 H100 一种 GPU 型号；未评估 CPU/GPU 带宽更低或更高时的影响。
- **潜在的实现开销**：需在请求中传递工作流元数据，并维护客户端 ID 避免命名冲突，增加了前端代码复杂度（但作者称开销可忽略）。
- **仅聚焦系统层加速**：未考虑模型精度或 Agent 协作质量；语义正确性通过不变性保证。
- **未公开开源代码**（论文注“将来开源”），影响复现性。

（完）
