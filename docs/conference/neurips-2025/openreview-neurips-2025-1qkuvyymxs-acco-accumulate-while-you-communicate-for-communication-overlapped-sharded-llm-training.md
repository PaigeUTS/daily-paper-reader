---
title: "ACCO: Accumulate While You Communicate for Communication-Overlapped Sharded LLM Training"
title_zh: ACCO：面向分片LLM训练的通信重叠累积方法
authors: "Adel Nabli, Louis Fournier, Pierre ERBACHER, Louis Serrano, Eugene Belilovsky, Edouard Oyallon"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=1qKUVyymXs"
tags: ["query:agents-os"]
score: 7.0
evidence: 通信重叠的分片LLM训练，支持异构硬件
tldr: ACCO提出了一种内存高效的分布式LLM训练优化算法，通过将梯度同步与计算重叠来减少GPU空闲时间，同时支持异构硬件，显著提升了训练效率与可扩展性，为异构计算环境下的大模型训练提供了关键技术。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qkuvyymxs/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1439, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qkuvyymxs/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1381, \"height\": 229, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qkuvyymxs/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 739, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qkuvyymxs/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 667, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qkuvyymxs/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1342, \"height\": 486, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qkuvyymxs/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 669, \"height\": 430, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qkuvyymxs/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1340, \"height\": 432, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qkuvyymxs/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1330, \"height\": 428, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qkuvyymxs/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1317, \"height\": 430, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qkuvyymxs/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 813, \"height\": 526, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qkuvyymxs/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 809, \"height\": 521, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qkuvyymxs/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 819, \"height\": 522, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qkuvyymxs/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1408, \"height\": 467, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-1qkuvyymxs/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1408, \"height\": 760, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-1qkuvyymxs/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1457, \"height\": 564, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1qkuvyymxs/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 716, \"height\": 218, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1qkuvyymxs/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 855, \"height\": 257, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1qkuvyymxs/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 942, \"height\": 541, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-1qkuvyymxs/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 876, \"height\": 500, \"label\": \"Table\"}]"
motivation: 分布式LLM训练中梯度同步开销大，且局部优化防止状态分片。
method: 提出累积与通信重叠算法，允许延迟梯度同步。
result: ACCO减少空闲时间并支持异构硬件，提升训练效率。
conclusion: 通信重叠是优化分布式训练的关键，尤其适用于异构系统。
---

## Abstract
Training LLMs relies on distributed implementations using multiple GPUs to compute gradients in parallel with sharded optimizers. However, synchronizing gradients in data parallel setups introduces communication overhead that grows with the number of workers, limiting parallelization efficiency. Local optimization algorithms reduce communications but incur high memory costs as they prevent optimizer state sharding, hindering scalability. To address this, we propose $\textbf{AC}$cumulate while $\textbf{CO}$mmunicate ($\texttt{ACCO}$), a memory-efficient optimization algorithm for distributed LLM training. By synchronizing delayed gradients while computing new ones, $\texttt{ACCO}$ reduces GPU idle time and supports heterogeneous hardware. To mitigate the convergence issues caused by delayed updates, we introduce a novel technique ensuring training dynamics align with standard distributed optimization. Compared to ZeRO-1, our approach is significantly faster and scales effectively across heterogeneous hardware.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：大规模语言模型（LLM）训练依赖分布式数据并行，但梯度同步的通信开销随GPU数量增长而急剧上升，成为主要瓶颈。局部更新方法（如Local SGD）虽能减少通信频率，但需要完整保存优化器状态（如Adam动量），无法使用ZeRO等内存分片技术，导致内存开销剧增，限制了模型的规模扩展。
- **核心问题**：如何在保持**内存高效**（即支持优化器状态分片）的前提下，实现**通信与计算的重叠**，从而减少GPU空闲时间，并**兼容异构硬件**，同时保证收敛质量与标准训练一致。
- **整体意义**：提出ACCO（Accumulate While COmmunicate）算法，统一了通信-计算重叠与内存高效训练，填补了现有方法（如DPU、WP）在收敛退化、额外超参数和内存开销方面的空白，为大规模LLM分布式训练提供了可扩展的解决方案。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：利用梯度累积的自然过程，将一次mini-batch的计算分为两个阶段，实现通信和计算的并行执行，并引入两阶段补偿机制消除延迟更新对收敛的负面影响。
- **关键技术细节**：
  - **两阶段执行**：
    - **阶段1**：计算流使用mini-batch的后一半计算梯度 \(g^{(t)}_i\)（相对于当前参数 \(\theta^{(t)}\)）；同时通信流利用前一轮估计的梯度 \(\tilde{g}^{(t)}_i\) 更新参数得到 \(\tilde{\theta}^{(t+1)}\)（预测下一步参数）。
    - **阶段2**：计算流使用mini-batch的前一半计算梯度 \(\tilde{g}^{(t+1)}_i\)（相对于预测参数 \(\tilde{\theta}^{(t+1)}\)）；同时通信流利用完整的梯度（\(g^{(t)}_i + \tilde{g}^{(t)}_i\)）执行实际优化器步骤更新 \(\theta^{(t+1)}\)。
  - **补偿机制**：与DPU（直接使用延迟梯度更新）或WP（重复应用两次优化器步骤）不同，ACCO通过将mini-batch分裂，使得实际更新使用的梯度与当前参数对齐，避免了延迟。这确保了训练动态与标准DDP一致。
  - **内存效率**：ACCO仍然使用ZeRO-1风格的分片优化器状态（仅需一个通信缓冲区，内存开销与ZeRO-1相同，远低于局部更新方法）。
  - **理论保证**：对SGD给出收敛率证明（使用Lyapunov函数），表明ACCO达到与标准SGD相同的收敛速度（\(O(1/T)\)，且方差项与标准SGD一致），而DPU和WP无法提供类似的保证。

### 3. 实验设计：数据集、场景、Benchmark与对比方法

- **数据集与场景**：
  1. **TinyStories**：36M参数GPT-Neo，训练约40K步，用于验证延迟更新影响及ACCO与DDP的匹配性。
  2. **OpenWebText**：125M参数GPT-Neo，训练50B tokens（约50K步），评估大规模预训练性能。
  3. **Alpaca指令微调**：2.7B参数GPT-Neo，52K指令对，评估微调场景下的通信瓶颈。
- **硬件场景**：
  - 同构：8×A100-80GB（单节点）、32×A100-80GB（4节点）、8×H100-PCIe 80GB（单节点）。
  - 异构：4个A100中模拟1个GPU慢4倍，测试异构适应性。
- **Benchmark与对比方法**：
  - **DDP + ZeRO-1**：标准基线（优化器状态分片，无重叠）。
  - **DPU**（Delayed Parameter Update）：ZeRO-Offload风格的延迟更新（有/无warmup）。
  - **WP**（Weight Prediction）：通过重复优化器步骤预测参数。
  - **ACCO**（本文方法）。
- **评估指标**：Loss曲线、Perplexity（LAMBADA、OpenWebTest）、时间加速比、内存占用。

### 4. 资源与算力

- **明确说明的算力**：
  - **A100-80GB集群**：8 GPU/节点，NVLink 300GB/s（节点内），Omni-PAth 100Gb/s（节点间）。
  - **H100-PCIe 80GB**：8 GPU/节点（单节点实验）。
  - **实验规模**：
    - TinyStories：8 GPUs单节点。
    - 125M预训练：8 H100（6B tokens，~4.5h）和32 A100（50B tokens，~11-14h）。
    - 2.7B微调：8 A100（80M tokens，~30min-3.8h）。
    - 异构实验：4 A100（1个模拟4x慢）。
- **未明确说明**：总GPU时数（可估算但未列出），每个实验的完整超参数设置见附录表4、5。

### 5. 实验数量与充分性

- **实验组数**：
  - 同构场景：TinyStories上对比ACCO vs DDP vs DPU（多warmup设置） vs WP；125M预训练在两个硬件配置上（8 H100和32 A100）；2.7B微调在单节点和双节点分别测试。
  - 异构场景：1组（4 workers，1个慢GPU）。
  - 理论分析：包含GD和SGD收敛性证明。
- **充分性与客观性**：
  - 对比了所有相关的基线方法（DDP/ZeRO、DPU、WP），且控制了有效batch size一致。
  - 在多个规模（36M、125M、2.7B）和任务（预训练、微调）上验证，覆盖同构和异构环境。
  - 提供了TinyStories上3次重复的误差（mention in Section 4.3），但大型实验未报告误差条（可能由于计算成本）。
  - 消融实验：对DPU的warmup步数影响做了分析；对WP的补偿效果做了对比，实验设计较为全面。
- **潜在不足**：缺少与现代局部更新方法（如DiLoCo、CO2）的直接比较（作者在内存分析中解释他们因内存过高无法运行，但理论上缺少实际对比）；未在更大模型（>10B）上实验。

### 6. 论文的主要结论与发现

1. **ACCO收敛性匹配DDP**：在TinyStories上训练曲线几乎完全重合，DPU即使使用500步warmup仍存在明显损失差距，WP初期退化更严重。
2. **显著加速**：在125M预训练中实现~25% wall-clock加速（4节点32GPU）；在2.7B微调中因通信瓶颈更突出，加速比达87%（双节点）。
3. **异构硬件优势**：在慢worker场景下，ACCO通过让快worker累积更多梯度，有效利用空闲时间，显著降低wall-clock时间（图9）。
4. **无额外超参数**：无需外循环或warmup，训练动态与标准AdamW完全一致。
5. **理论保证**：对SGD情形，ACCO的收敛率与标准SGD相同，证明其延迟补偿的有效性。

### 7. 优点：方法或实验设计上的亮点

- **方法创新**：
  - 首次将通信-计算重叠与优化器状态分片结合，同时解决内存和通信瓶颈。
  - 两阶段累积机制巧妙消除了延迟更新的负面影响，理论分析干净（Lyapunov函数）。
  - 天然支持异构硬件：快worker自动累积更多梯度，无需特殊适配。
- **实验设计亮点**：
  - 详细分析了DPU的warmup敏感性，揭示了延迟更新的严重性问题。
  - 在多节点、异构环境下验证，展示了实际部署价值。
  - 内存对比表（Table 1）清晰展示ACCO相对于局部更新方法的内存优势。

### 8. 不足与局限

- **实验覆盖**：仅验证到2.7B模型，没有在更大模型（如7B、13B）上实验，尽管动机测量了7B的通信时间。对于更大模型的扩展性缺乏直接证据。
- **对比不完整**：缺少与Non-sharded重叠方法（如CO2、Overlap Local-SGD）的直接性能/时间对比（作者以内存开销为由未运行，但可以在减少内存受限场景下对比）。
- **硬件异构模拟**：异构实验使用`time.sleep()`模拟，而非真正异构GPU集群（如不同代或不同带宽），可能低估了实际异构带来的梯度偏差问题。
- **收敛证明仅针对SGD**：对AdamW等自适应优化器只有实验验证，缺乏理论保证。
- **代码与可复现性**：论文声称代码开放，但检查清单中未提供匿名链接；附录给出了slurm脚本和超参数，但未提供精确的随机种子或完整配置清单。
- **偏差风险**：主要对比基于PyTorch DDP + ZeRO-1，未与DeepSpeed ZeRO-3等更高效的分片框架对比，可能放大自己的优势。

（完）
