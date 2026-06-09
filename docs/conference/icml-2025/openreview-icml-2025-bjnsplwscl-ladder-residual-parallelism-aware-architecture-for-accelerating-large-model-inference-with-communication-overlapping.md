---
title: "Ladder-Residual: Parallelism-Aware Architecture for Accelerating Large Model Inference with Communication Overlapping"
title_zh: 阶梯残差：面向大模型推理加速的并行感知架构与通信重叠
authors: "Muru Zhang, Mayank Mishra, Zhongzhu Zhou, William Brandon, Jue WANG, Yoon Kim, Jonathan Ragan-Kelley, Shuaiwen Leon Song, Ben Athiwaratkun, Tri Dao"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=bJnSplWSCL"
tags: ["query:agents-os"]
score: 7.0
evidence: 针对多GPU大模型推理的通信重叠架构修改
tldr: Ladder-Residual提出了一种简单的残差架构修改，适用于所有基于残差的模型，能够有效隐藏模型并行中的通信延迟。该方法无需额外工程即可加速多GPU推理，显著提升了异构计算环境下大模型的可扩展性。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-bjnsplwscl/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 816, \"height\": 491, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bjnsplwscl/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1723, \"height\": 1309, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bjnsplwscl/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 829, \"height\": 620, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bjnsplwscl/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 829, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bjnsplwscl/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 832, \"height\": 479, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-bjnsplwscl/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 864, \"height\": 422, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-bjnsplwscl/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 624, \"height\": 343, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bjnsplwscl/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 864, \"height\": 835, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bjnsplwscl/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1472, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bjnsplwscl/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1372, \"height\": 276, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bjnsplwscl/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1476, \"height\": 204, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-bjnsplwscl/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1523, \"height\": 200, \"label\": \"Table\"}]"
motivation: 模型并行中的通信成为多GPU推理的主要瓶颈。
method: 提出Ladder Residual架构，通过设计残差连接来重叠通信与计算。
result: 有效隐藏通信延迟，提升多GPU推理速度。
conclusion: 该方法为分布式大模型推理提供了轻量级解决方案。
---

## Abstract
Large language model inference is both memory-intensive and time-consuming, often requiring distributed algorithms to efficiently scale. Various model parallelism strategies are used in multi-gpu training and inference to partition computation across multiple devices, reducing memory load and computation time. However, using model parallelism necessitates communication of information between GPUs, which has been a major bottleneck and limits the gains obtained by scaling up the number of devices. We introduce Ladder Residual, a simple architectural modification applicable to all residual-based models that enables straightforward overlapping that effectively hides the latency of communication. **Our insight is that in addition to systems optimization, one can also redesign the model architecture to decouple communication from computation.** While Ladder Residual can allow communication-computation decoupling in conventional parallelism patterns, we focus on Tensor Parallelism in this paper, which is particularly bottlenecked by its heavy communication. For a Transformer model with 70B parameters, applying Ladder Residual to all its layers can achieve 29% end-to-end wall clock speed up at inference time with TP sharding over 8 devices. We refer the resulting Transformer model as the Ladder Transformer. We train a 1B and 3B Ladder Transformer from scratch and observe comparable performance to a standard dense transformer baseline. We also show that it is possible to convert parts of the Llama-3.1 8B model to our Ladder Residual architecture with minimal accuracy degradation by only retraining for 3B tokens.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：大语言模型（LLM）推理在多个GPU上使用模型并行（尤其是张量并行 Tensor Parallelism, TP）时，GPU间的通信（AllReduce）成为严重瓶颈，占据总延迟的较大比例（例如70B模型在TP world size=8、batch=4时可达38%）。现有系统级优化（如细粒度内核融合、DSL编译器）虽能一定程度重叠通信，但需要低级别硬件适配，且随硬件更新需重写，工程开销大。
- **研究动机**：作者提出从**模型架构本身**出发，通过修改残差连接的依赖关系，使通信与计算天然可重叠，从而在不修改底层核函数的情况下加速推理。这一思路使方法具备硬件无关性，易于部署。
- **整体含义**：Ladder Residual是一种简单通用（适用于所有残差模型）的架构修改，能有效隐藏TP通信延迟，显著提升多GPU推理吞吐量，且保持模型质量，为分布式推理提供轻量级、可迁移的解决方案。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：利用残差流中**更新量较小**（激活变化缓慢）的特点，将当前模块的输入替换为“过时”的残差（前两个模块的输出），从而解除模块计算与上一个模块通信的强制顺序依赖，使通信能与后续计算并行。
- **关键技术细节**：
    - **标准Transformer**：`xi+1 = hi+1(xi) + xi`，其中`hi`是第i个模块（注意力或MLP），每个模块后需AllReduce同步，阻塞下一个模块。
    - **Ladder Residual**：`xi+1 = hi+1(xi-1) + xi`。第i+1个模块直接使用第i-1个模块的输出作为输入，而残差连接仍使用第i个模块的输出（保证信息流）。这样，第i个模块的AllReduce可与第i+1个模块的计算重叠。
- **算法流程**（伪代码 Algorithm 1）：
    1.  等待上一个MLP的异步AllReduce完成（`mlp_work.wait()`）。
    2.  更新残差：`residual += mlp_out`。
    3.  计算当前注意力（先Norm，再Attention）。
    4.  发起注意力的异步AllReduce（返回句柄`attn_work`）。
    5.  等待上一个注意力的异步AllReduce完成（`attn_work.wait()`）。
    6.  更新残差：`residual += attn_out`。
    7.  计算当前MLP（先Norm，再MLP）。
    8.  发起MLP的异步AllReduce（返回句柄`mlp_work`）。
    9.  将残差、当前注意力输出、MLP输出以及两个句柄传给下一层。
- **实现细节**：使用PyTorch的异步NCCL操作（`AsyncAllReduce`），结合CUDA Graphs和`torch.compile`减少CPU开销。注意：需通过句柄在下一层同步，保证最终结果正确。

### 3. 实验设计：使用的数据集/场景、benchmark、对比方法

- **数据集与场景**：
    - **从零训练**：FineWeb-edu 数据集（100B tokens），StarCoder tokenizer，2048上下文长度。
    - **后训练适应**：对Llama-3.1-8B-Instruct，使用Infinity-Instruct数据集（7M子集+Gen子集，共3B tokens）进行SFT。
    - **推理基准**：固定prompt长度1024，生成长度512；变参batch size (1,4,16,64)、TP world size (1,2,4,8/16)；启用/禁用NVLink P2P通信。模型规模从1B到405B。
- **Benchmark**：
    - **从零训练评估**：ARC-C、ARC-E、HellaSwag、PIQA、SciQ、Winogrande（准确率）；Wikitext perplexity。使用EleutherAI LM eval harness。
    - **后训练适应评估**：MMLU (5-shot)、ARC-C (25-shot)、OpenBookQA、HellaSwag (10-shot)、TruthfulQA (mc1)、GSM8K (8-shot)、HumanEval+ (pass@1)、IFEval、AlpacaEval (length-controlled win rate against GPT-4 Turbo)。
    - **推理加速评估**：端到端延迟（prefill+decode）、吞吐量（tokens/sec/GPU）、Pareto前沿（延迟 vs 吞吐量）。
- **对比方法**：
    - 标准Transformer（Baseline）。
    - Parallel Transformer（PaLM风格：并行Attention和MLP，减少一半AllReduce）。
    - 通信无界上界（移除所有通信）。
    - 30%更大的Ladder Transformer（对比相同吞吐量下的质量）。
    - 自身消融：Ladder Transformer vs 标准；P2P启用/禁用；不同适应层数（16L vs 20L）。

### 4. 资源与算力

- **训练资源**：
    - 1.2B模型：使用DDP（多节点数据并行），未明确GPU数量。
    - 3.5B模型：使用HSDP（每节点8xH100内分片，节点间复制）。具体节点数未提及。
    - 所有模型训练100B tokens。
    - 后训练适应（8B model）：使用Axolotl库，具体GPU数量未说明，但从文中“使用64个H100训练8B模型”仅用于验证训练加速（5-7%），非主要实验。适应实验可能使用较少GPU（如8或16）。
    - 推理基准：使用NVIDIA H100 GPU（可能为单节点8卡或两节点16卡（405B））。

### 5. 实验数量与充分性

- **实验数量**：论文包含约6个主要表格（表1-5）和4个图表（图2-5），涵盖：
    - 推理加速（表1、表2、图2、图3、图4）跨越7种模型大小、多种TP配置、两种互联场景。
    - 从零训练（表3）含1.2B和3.5B两个规模，各3种架构，评估6项指标+perplexity。
    - 后训练适应（表4）含零样本和微调后的8个基准，以及两种适应层数。
    - 质量-效率权衡（表5）对比30%更大Ladder vs 标准。
- **充分性**：整体较为充分，覆盖了不同规模、训练范式和推理场景。对比了强基线（标准Transformer和并行Transformer）。消融实验包括P2P启用/禁用、适应层数。但不足在于：
    - 未验证更大规模（如70B）从零训练的效果（仅推理加速）。
    - 后训练适应仅在8B模型上实验，且最优仅16层，20层性能下降。
    - 未报告多次运行以消除随机性，部分结果差异较小（如1.2B平均准确率59.98 vs 58.92）可能不显著。
    - 训练加速的5-7%未详细展开，缺少实验细节。

### 6. 论文的主要结论与发现

- **推理加速显著**：Ladder Residual在TP场景下实现29%（70B, P2P启用）至59%（P2P禁用）的吞吐量提升。在不同batch size和TP size下均优于标准及并行Transformer，接近无通信上界。
- **模型质量无损**：
    - 从零训练的1.2B和3.5B Ladder Transformer在多数基准上匹配标准Transformer（表3），仅3.5B略低（平均准确率63.03 vs 64.11，但PPL 14.90 vs 14.48），作者认为可能因超参数未最优。
    - 后训练适应中，混合Ladder Llama（最后16层）经3B tokens微调后，在8个基准上平均准确率56.24 vs 原模型56.11，基本持平。
- **效率-质量权衡**：如果牺牲部分质量换取更高吞吐，可将模型增大30%（如1.5B Ladder vs 1.2B标准），在相同推理速度下质量更好（表5）。
- **方法通用性**：可与管道并行、数据并行兼容，且无需底层内核修改，易于集成到PyTorch/JAX。

### 7. 优点

- **架构创新**：首次从残差结构设计角度解决通信重叠问题，而非依赖系统级优化，具备硬件不可知性。
- **简单实用**：改动极小（仅调整残差输入），可即插即用，兼容现有框架（PyTorch异步NCCL）。
- **实验覆盖面广**：从1B到405B、训练和适应、多种通信场景，验证了方法的稳健性。
- **后训练适应高效**：仅需3B tokens微调即可恢复性能，远少于其他架构转换（如Mamba需50B tokens），说明表示偏移小。
- **兼容性强**：可与并行Attention/MLP等现有加速技巧结合（如论文中Parallel-Ladder未实验但理论上可行）。

### 8. 不足与局限

- **从零训练性能差距**：在3.5B规模，Ladder Transformer准确率比标准低约1.2%，PPL高0.42，虽不大但仍需更多调优或更大训练量以消除差距。
- **后训练适应不完整**：仅适应后半部分（16层）达到原表现；尝试更多层（20层）性能下降，说明全模型适应仍需更充分训练或更智能方法（如蒸馏）。未探索逐层渐进适应策略。
- **推理加速与通信依赖度强**：当通信非瓶颈时（如小模型、P2P快、TP size小），加速比有限（例如1B模型仅1.39x P2P禁用）。实际部署中需评估通信开销比例。
- **训练加速证据不足**：仅一句提及5-7%加速，未提供详细设置、效率曲线，无法严谨复现。
- **实验统计缺失**：未报告多次重复实验的标准差，部分指标差异小，结论可能在统计上不显著。
- **泛化性验证不足**：仅测试Transformer语言模型，虽宣称适用于所有残差架构，但未在Vision Transformer、Mamba等上验证。
- **增加复杂度**：每个层需要管理多个异步句柄，增加代码复杂性和潜在风险（如同步错误）。内存占用可能略微增加（需保留更多中间输出？）。

（完）
