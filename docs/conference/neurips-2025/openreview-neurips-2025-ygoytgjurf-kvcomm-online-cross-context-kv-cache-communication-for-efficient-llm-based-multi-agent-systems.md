---
title: "KVCOMM: Online Cross-context KV-cache Communication for Efficient LLM-based Multi-agent Systems"
title_zh: KVCOMM：面向高效LLM多智能体系统的在线跨上下文KV缓存通信
authors: "Hancheng Ye, Zhengqi Gao, Mingyuan Ma, Qinsi Wang, Yuzhe Fu, Ming-Yu Chung, Yueqian Lin, Zhijian Liu, Jianyi Zhang, Danyang Zhuo, Yiran Chen"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=yGOytgjurF"
tags: ["query:agents-os"]
score: 4.0
evidence: 多智能体LLM系统中的在线KV缓存通信，提升智能体协作效率
tldr: 多智能体LLM系统中，每个代理独立重处理大量重叠上下文造成低效。KVCOMM通过在线跨上下文KV缓存通信，使代理间复用前驱的计算结果。实验证明了大幅加速，为构建高效智能体操作系统提供了通信优化技术。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-ygoytgjurf/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1448, \"height\": 400, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ygoytgjurf/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1233, \"height\": 757, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ygoytgjurf/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1408, \"height\": 700, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ygoytgjurf/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1449, \"height\": 626, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ygoytgjurf/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1394, \"height\": 1805, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ygoytgjurf/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1432, \"height\": 321, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ygoytgjurf/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1430, \"height\": 867, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ygoytgjurf/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1430, \"height\": 332, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ygoytgjurf/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1445, \"height\": 1803, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ygoytgjurf/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1443, \"height\": 1799, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ygoytgjurf/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1442, \"height\": 1820, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ygoytgjurf/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1440, \"height\": 1825, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ygoytgjurf/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1442, \"height\": 1820, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ygoytgjurf/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1441, \"height\": 1823, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ygoytgjurf/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1443, \"height\": 1830, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ygoytgjurf/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1442, \"height\": 1827, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-ygoytgjurf/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1416, \"height\": 945, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-ygoytgjurf/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1451, \"height\": 952, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ygoytgjurf/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 721, \"height\": 223, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ygoytgjurf/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 659, \"height\": 260, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ygoytgjurf/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 806, \"height\": 122, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ygoytgjurf/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 802, \"height\": 387, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ygoytgjurf/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 805, \"height\": 404, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ygoytgjurf/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1455, \"height\": 749, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ygoytgjurf/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1448, \"height\": 695, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ygoytgjurf/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 803, \"height\": 218, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ygoytgjurf/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1258, \"height\": 301, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ygoytgjurf/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 804, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ygoytgjurf/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1050, \"height\": 302, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-ygoytgjurf/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1450, \"height\": 431, \"label\": \"Table\"}]"
motivation: 多智能体系统中重复处理相同上下文导致计算浪费。
method: 提出在线KV缓存共享机制，允许代理间传递缓存的键值对。
result: 显著减少重复计算，加速多轮对话和协作任务。
conclusion: KV缓存通信是优化多智能体系统效率的关键技术。
---

## Abstract
Multi-agent large language model (LLM) systems are increasingly adopted for complex language processing tasks that require communication and coordination among agents. However, these systems often suffer substantial overhead from repeated reprocessing of overlapping contexts across agents. In typical pipelines, once an agent receives a message from its predecessor, the full context-including prior turns-must be reprocessed from scratch, leading to inefficient processing. While key-value (KV) caching is an effective solution for avoiding redundant computation in single-agent settings where prefixes remain unchanged, it cannot be directly reused in multi-agent scenarios due to diverging prefixes introduced by agent-specific context extensions. We identify that the core challenge lies in the offset variance of KV-caches across agents. To address this, we propose **KVCOMM**, a training-free framework that enables efficient prefilling in multi-agent inference by reusing KV-caches and aligning cache offsets of overlapping contexts under diverse prefix contexts. KVCOMM estimates and adjusts KV-caches for shared content by referencing a pool of cached examples—termed *anchors*—that store observed cache deviations under varying prefixes. The anchor pool is maintained and updated online, allowing dynamic adaptation to distinct user requests and context structures. KVCOMM achieves over 70% reuse rate across diverse multi- agent workloads, including retrieval-augmented generation, math reasoning, and collaborative coding tasks, all without quality degradation. Particularly, when each fully-connected agent receives 1K input tokens with 512 prefix tokens and 512 output tokens under a five-agent setting, KVCOMM achieves up to 7.8× speedup compared to the standard prefill pipeline, reducing TTFT from ∼430ms to ∼55ms. Code is available at https://github.com/FastMAS/KVCOMM.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：基于LLM的多智能体系统（MAS）中，智能体之间反复传递消息，每个智能体在处理包含大量重叠上下文（如系统提示、上游智能体的输出）的输入时，都会从头重新计算KV缓存（Key-Value Cache），导致大量冗余的预填充计算（prefilling）。例如，一个8B的Llama模型在H100 GPU上预填充3K token需要约430ms，若M个智能体全连接，总预填充复杂度为O(M²)，严重拖慢实时协作。
- **挑战**：传统KV缓存复用方法（如CacheBlend）假设共享前缀不变，但在多智能体场景中，不同智能体的前缀上下文不同，导致相同文本的KV缓存出现“偏移方差”（offset variance）——即使相同token在不同前缀下，其KV缓存的差异很大且不可预测。静态复用策略无法处理这种偏移，要么导致精度下降，要么退化为完全重计算。
- **核心洞察**：两个相似token在不同前缀下的KV缓存偏移具有相似分布（图1b），且偏移大小与token嵌入距离高度相关（图4c/d）。因此可以通过参考相似样本（锚点）的偏移来估计当前上下文的偏移，从而实现跨上下文KV缓存复用。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：提出一种无需训练、在线自适应的KV缓存通信框架**KVCOMM**。它将每个复用尝试视为一个近似“翻译”问题——通过旋转和解旋RoPE实现位置对齐，再利用锚点池（anchor pool）中存储的偏移量，通过嵌入相似度加权插值估计当前上下文中共享文本的KV缓存偏移，从而直接复用基础KV缓存，跳过预填充阶段。
- **关键技术细节**：
    - **锚点池设计**：每个占位符（placeholder，如用户输入、上游回复）维护一个锚点池。一个锚点包含：基础KV缓存（无外部上下文时的值）、在该智能体上下文中占位符和相邻前缀段（prefix）的KV偏移。锚点由“嵌入距离”和“长度兼容性”两个条件决定是否匹配。
    - **锚点预测**：基于新样本的嵌入熵和长度判断是否可共享。公式(5)定义了可共享条件：若样本比所有锚点都长，或与锚点之间的嵌入加权熵小于阈值γ，则视为可共享。
    - **锚点匹配与偏移近似**：匹配后，使用**softmax归一化的ℓ₂范数距离**作为权重，对锚点的偏移进行加权平均，得到占位符和前缀段的近似KV缓存：
        - 占位符：`(k̂/v̂)_ϕ = (k/v)_ϕ + Σ w·Δ(k/v)_ϕ` (公式6)
        - 前缀段：`(k̂/v̂)_p = (k/v)_p + Σ w·Δ(k/v)_p` (公式7)
    - **位置对齐**：由于RoPE，必须先对Key进行解旋/重旋（de-rotate/re-rotate），消除位置偏移后再加偏移。
    - **在线更新**：若样本不可共享，则进行密集预填充，并将产生的偏移作为新锚点加入池中；当池满（容量V=20）时，淘汰最不常用的早期锚点。
- **算法流程**（见附录Algorithm 1）：
    1. 初始化：所有智能体预计算模板中所有前缀段的KV缓存。
    2. 运行时：检查所有占位符的基础KV缓存是否就绪；若就绪，尝试匹配锚点。
    3. 若所有占位符可共享，则通过锚点匹配和偏移近似并行更新所有占位符和前缀段的KV缓存，然后直接解码。
    4. 若不可共享，则执行密集预填充，并将新的偏移存入锚点池。
    5. 解码后，将生成的回复KV缓存根据可共享性存入共享内存或锚点池。

## 3. 实验设计

- **多智能体系统**：遵循GPTSwarm和AgentPrune，构建全连接图，每个智能体使用相同基座模型但不同角色模板（如知识专家、批评家、最终决定者等）。模型：Llama-3.1-8B-Instruct（用于RAG和数学推理）和Qwen-Coder-2.5-7B-Instruct（用于编程）。
- **基准数据集**：
    - RAG：MMLU（知识问答，4选1）
    - 数学推理：GSM8K（小学数学应用题）
    - 编程：HumanEval（代码生成，Pass@1）
- **对比方法**：Original（无缓存复用）、CacheBlend（选择性重计算top-20%高偏差token）。由于CacheBlend与vLLM紧耦合，论文复现其策略。
- **评估指标**：Accuracy、Pass@1、Reuse Rate（复用比例）、TTFT（首令牌延迟）及平均加速比。
- **实验配置**：2-5个智能体，最大生成长度512 tokens，超参数γ=0.3，锚点池大小V=20。

## 4. 资源与算力

- 文中明确说明：“Experiments are executed on a single NVIDIA H100 GPU。” 未提供具体型号（如H100-80G）或训练时长，因为方法无需训练（training-free），仅推理阶段运行。
- 锚点匹配的软最大操作和KV缓存管理带来额外计算和内存开销，但论文在附录中分析了软最大延迟（表A.5）和内存成本（图A.1），指出主要瓶颈在于长上下文的KV缓存传输。

## 5. 实验数量与充分性

- **主要实验**：表1给出了三个数据集（MMLU、GSM8K、HumanEval）在2-5个智能体下的Accuracy和Reuse Rate，与Original和CacheBlend对比。
- **消融实验**：表5（三个对齐组件的贡献：位置旋转、占位符偏移、前缀偏移）、表6（超参数γ和V的敏感性）。
- **鲁棒性实验**：表4（请求顺序变化对精度的影响）。
- **TTFT分析**：表2（5智能体逐智能体TTFT分解）、表3（不同输入/输出长度的平均加速比）。
- **附录补充实验**：表A.2（MATH500和AIME上的性能）、表A.3（匹配准则消融）、表A.4（近似方法对比）、A.5（软最大延迟模拟）、A.6（长上下文锚点匹配开销）等。
- **充分性评价**：实验覆盖三类代表性任务、多个智能体数量、不同上下文长度，消融和超参数分析较全面。但缺少在更大模型（如70B）或更多智能体（>5）上的测试，也缺少与其他最新KV复用方法（如KVPredict、SGLang前缀缓存）的直接对比。

## 6. 主要结论与发现

- KVCOMM在MMLU、GSM8K、HumanEval上均能达到与原版密集推理相当的精度（精度下降<2.5%），同时实现70%-87.6%的缓存复用率。
- 在5智能体、1K输入+512前缀+512输出的设置下，TTFT从~430ms降至~55ms，加速比达7.8×；平均加速比约为6.7×（3智能体）。
- 加速比随上下文长度增长而扩大（表3），验证了方法在长上下文下的优势。
- 请求顺序对性能影响较小（表4），锚点池在线更新机制能适应不同分布。
- 三个对齐组件（位置对齐、占位符偏移、前缀偏移）缺一不可（表5），尤其是前缀偏移对保持因果连贯性至关重要（图A.2案例）。

## 7. 优点

1. **问题新颖**：首次系统性地识别并解决了多智能体场景下的“偏移方差”问题，提出了“跨上下文KV缓存复用”范式。
2. **无需训练**：所有操作均为推理时的锚点匹配和偏移近似，无需微调或修改模型，易于部署。
3. **理论支撑**：给出了KV距离和偏移距离的上界证明（Proposition 1 & 2），并实验验证了嵌入距离与KV偏移的相关性（Spearman系数>0.8），为锚点类比提供理论依据。
4. **在线自适应**：锚点池动态扩展和淘汰，适应变化的请求分布，无需离线预配置。
5. **显著加速**：在保持精度的前提下实现高达7.8×的预填充加速，且加速比随智能体数量和上下文长度增加而增大，具有良好的可扩展性。
6. **实验设计严谨**：消融实验、超参数敏感性、鲁棒性测试齐全，附录提供了大量可视化（偏移分布、锚点分布、近似误差等），便于理解。

## 8. 不足与局限

1. **模态限制**：仅支持文本输入，未扩展到图像、视频、音频等多模态智能体系统。
2. **解码未加速**：仅加速预填充阶段，解码阶段（自回归生成）仍然是瓶颈，作者提出将解码优化作为未来工作。
3. **模型异构性未覆盖**：要求所有智能体使用相同架构和权重（同质模型），未能处理不同微调版本或不同模型间的KV共享。
4. **动态场景局限**：当前主要针对模板化、消息传递结构相对固定的MAS，未处理完全无结构的对话式或辩论式场景。
5. **内存开销**：锚点池存储大量KV偏移张量，长上下文下内存消耗显著（附录图A.1），且锚点匹配的软最大操作（尤其是KV从CPU卸载时）可能引入额外延迟（表A.6）。
6. **轻微精度损失**：在AIME等较难推理任务上精度下降明显（表A.2中从19.2%降至11.7%），可能因解码长度限制（共享缓存占用额外内存）而非方法本身。
7. **对比基线不足**：仅与CacheBlend对比，未与PromptCache、CacheGen、KVLink等更近期的KV复用方法进行横向比较。

（完）
