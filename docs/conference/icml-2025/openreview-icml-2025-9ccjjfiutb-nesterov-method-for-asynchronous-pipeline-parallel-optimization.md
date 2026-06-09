---
title: Nesterov Method for Asynchronous Pipeline Parallel Optimization
title_zh: 异步流水线并行优化的Nesterov方法
authors: "Thalaiyasingam Ajanthan, Sameera Ramasinghe, Yan Zuo, Gil Avraham, Alexander Long"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=9CCJJFiutB"
tags: ["query:agents-os"]
score: 8.0
evidence: 针对异步流水线并行的Nesterov方法解决异构分布式训练中的梯度陈旧问题
tldr: 异步流水线并行存在梯度陈旧问题，影响训练收敛。本文引入Nesterov加速梯度变体，修改look-ahead步以有效应对延迟梯度，理论上证明在固定延迟下以次线性速率收敛。实验表明该方法在大型模型训练中表现良好，为异构计算环境下的分布式优化提供了有效方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-9ccjjfiutb/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 863, \"height\": 277, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9ccjjfiutb/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1755, \"height\": 387, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9ccjjfiutb/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 856, \"height\": 246, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9ccjjfiutb/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1753, \"height\": 391, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9ccjjfiutb/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 857, \"height\": 312, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9ccjjfiutb/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1758, \"height\": 388, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9ccjjfiutb/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 861, \"height\": 245, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9ccjjfiutb/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 844, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9ccjjfiutb/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1755, \"height\": 385, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9ccjjfiutb/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 881, \"height\": 480, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9ccjjfiutb/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1751, \"height\": 388, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9ccjjfiutb/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 882, \"height\": 486, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-9ccjjfiutb/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 881, \"height\": 438, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-9ccjjfiutb/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 764, \"height\": 311, \"label\": \"Table\"}]"
motivation: 异步流水线并行中梯度陈旧严重影响训练效率和收敛性。
method: 提出Nesterov加速梯度变体，修改look-ahead步以补偿梯度延迟。
result: 理论上证明了次线性收敛性，实验验证了在大模型训练中的有效性。
conclusion: 该方法是异步流水线训练的有效优化器，提升了异构计算资源利用率。
---

## Abstract
Pipeline Parallelism (PP) enables large neural network training on small, interconnected devices by splitting the model into multiple stages. To maximize pipeline utilization, asynchronous optimization is appealing as it offers 100% pipeline utilization by construction. However, it is inherently challenging as the weights and gradients are no longer synchronized, leading to *stale (or delayed) gradients*. To alleviate this, we introduce a variant of Nesterov Accelerated Gradient (NAG) for asynchronous optimization in PP. Specifically, we modify the look-ahead step in NAG to effectively address the staleness in gradients. We theoretically prove that our approach converges at a sublinear rate in the presence of fixed delay in gradients. Our experiments on large-scale language modelling tasks using decoder-only architectures with up to **1B parameters**, demonstrate that our approach significantly outperforms existing asynchronous methods, even surpassing the synchronous baseline.

---

## 论文详细总结（自动生成）

# 异步流水线并行优化的Nesterov方法（ICML 2025）— 详细中文总结

## 1. 论文的核心问题与整体含义

- **研究动机**：流水线并行（Pipeline Parallelism, PP）可在大模型训练中分割模型到多个设备，但因同步瓶颈难以达到100%利用率。异步优化虽能完全利用流水线，却引入梯度陈旧（stale/delayed gradients）问题，严重影响收敛速度和稳定性。
- **整体含义**：本文提出一种适用于异步PP的Nesterov加速梯度变体，通过修改look-ahead步来有效应对梯度延迟，首次在**1B参数**的语言模型上实现异步方法超越同步基线，证明了异步PP在大规模训练中的可行性。

## 2. 论文提出的方法论

### 核心思想
- **延迟校正的思路**：利用动量优化器中更新方向缓慢变化的特点，在权重空间进行外推补偿延迟，而非预测梯度值。
- **关键洞察**：Nesterov加速梯度（NAG）本身具有look-ahead步（外推前一次更新），可被重用于延迟校正；但需修改梯度项，加入折扣因子 `(1-γ_t)` 以增强外推作用。

### 关键技术与公式
原始NAG：  
`d_t = γ_t(w_t - w_{t-1})`  
`w_{t+1} = w_t + d_t - η ∇f(w_t + d_t)`  

本文变体（延迟梯度场景）：  
`d_t = γ_t(w_t - w_{t-1})`  
`w_{t+1} = w_t + d_t - η (1-γ_t) ∇f(¯w_t + ¯d_t)`  
其中 `¯w_t = w_{t-τ}`, `¯d_t = d_{t-τ}`，`τ` 为固定延迟。

- **梯度折扣因子** `(1-γ_t)` 使梯度贡献随 `γ_t→1` 而衰减，从而使look-ahead方向 `d_t` 与延迟方向 `∆_t` 对齐，起到延迟校正作用（Proposition 1）。
- **动量系数序列**：`γ_t = (t-2)/t`（收敛分析中采用），实际中使用常数 `β1=0.99` 或线性递增。
- **实现**：直接使用PyTorch的NAdam优化器（已有 `(1-γ_t)` 折扣），仅需设置 `β1=0.99`，无需额外超参数。

### 内存高效版本（Ours-No-WS）
- 不存储旧权重（无weight stashing），但需使用阶段依赖的学习率和动量系数（式13）来补偿错误反向传播。
- 学习率校正：早期阶段降低学习率，动量从0.9线性增至0.99。

### 理论分析
- Theorem 1：对凸、β-光滑、有界梯度函数，以学习率 `η=1/β` 时，收敛率为 `O(1/t)`（次线性）。虽然未达到标准NAG的 `O(1/t^2)`，但证明首次在延迟梯度下展示了NAG变体的收敛性。

## 3. 实验设计

### 数据集与场景
- **主要数据集**：WikiText (WT)、BookCorpus (BC)、OpenWebText (OWT) — 三个大规模语言建模数据集。
- **基准方法**：
  - 同步方法：GPipe（4个微批次，减少气泡）
  - 现有异步方法：PipeDream（weight stashing）、PipeMare（学习率折扣+权重估计）
- **对比的延迟校正方法**：PipeDream-LR（学习率折扣）、LR-SecondOrder（二阶梯度预测）、Polynomial+FFT（时间序列预测）
- **去中心化训练**：SWARM框架（Hivemind），对比同步SWARM和异步SWARM-Async。

### 模型架构
- **基础模型**：类似NanoGPT，8层，嵌入维度768，12注意力头，约134M参数。每层作为一个流水线阶段。
- **1B模型**：嵌入维度2688，24注意力头，8阶段，约1B参数。
- 使用AdamW优化器（基线），微批次大小8，权重衰减0.01，序列长度512（基础）/ 1024（1B模型）。

### 超参数设置
- 学习率：基础模型3e-4，1B模型1e-4（各方法一致）。
- 线性预热3k步，余弦衰减至3e-5。
- 训练迭代50k步。

## 4. 资源与算力

- **基础实验（134M参数）**：8块NVIDIA A10G GPU。
- **1B参数实验**：8块NVIDIA A100 GPU。
- **SWARM去中心化实验**：24个L4 GPU（每阶段3个工作节点，共8阶段）。
- **训练时长**：未明确给出绝对时间，但比较了相对时间（图5、图10）。GPipe随阶段数增加训练时间增长显著（24阶段比4阶段慢8.5倍），而异步方法仅慢2.5倍。
- 说明：由于实现差异，未直接比较绝对壁钟时间，而是基于迭代次数（数据处理量）对比。

## 5. 实验数量与充分性

### 主要实验（3组数据集 × 基础模型）
- 图2、表1：WikiText、BookCorpus、OpenWebText上训练曲线和验证困惑度。三个数据集均一致表明本方法优于所有异步方法和同步GPipe。

### 扩展实验（4类）
1. **1B参数模型**（图3）：验证可扩展性，趋势与基础模型一致。
2. **与其他延迟校正方法对比**（图4）：训练损失 + RMSE权重差异（gap）。本方法最优，且与其它方法组合反而下降，验证权重空间校正优于梯度预测。
3. **不同阶段数（4/8/16/20/24）**（图5）：随阶段增加性能略有下降，但训练时间优势显著。
4. **消融实验**（图6、7）：
   - 动量系数：0.99固定优于自适应；对齐性分析支持理论。
   - 梯度折扣因子：去掉折扣后训练发散（图7），验证折扣必要性。
   - 学习率折扣、动量自适应的影响（图6c）。

### SWARM实验（图8）
- 真实去中心化场景，本方法显著优于同步和异步SWARM。

### 总结
- 实验覆盖**3个数据集、4种对比方法、多种延迟校正、不同规模模型、不同阶段数、去中心化场景**，消融全面，对比公平（超参数一致，仅优化器不同）。
- 结论稳健，充分验证了方法有效性和通用性。

## 6. 论文的主要结论与发现

- **首次**在异步PP中实现1B参数模型训练超越同步基线。
- 提出的NAG变体（本质是NAdam优化器 + 高β1）简单有效，无需额外超参数，即可显著缓解梯度陈旧。
- 重新验证了延迟校正的两种路径：权重空间外推（本文方法）优于梯度预测，且动量折扣因子是关键。
- 异步PP在内存高效版本中同样具有竞争力，且在去中心化场景中表现优越。

## 7. 优点

1. **方法简洁**：仅需将优化器切换为NAdam并调整β1，即可在现有框架（PipeDream）中部署，易于集成。
2. **理论支撑**：首次证明NAG变体在延迟梯度下的次线性收敛，为实践提供了理论基础。
3. **实验全面**：覆盖多种规模、数据集、对比方法和消融，结果一致且可信。
4. **性能卓越**：在语言建模任务中持续超越同步GPipe，打破了异步方法“不如同步”的传统认知。
5. **去中心化验证**：在SWARM中证明方法对网络延迟和节点异构具有鲁棒性。

## 8. 不足与局限

1. **理论假设较强**：收敛分析假设凸函数、固定延迟、有界梯度、非随机梯度（非随机设置），与实际深度学习（非凸、随机梯度、可变延迟）仍有差距。虽然实证实证，但理论完备性有限。
2. **延迟固定假设**：实际场景中延迟可能因硬件负载、网络波动而动态变化，文中未考虑非固定延迟。
3. **内存开销**：基本版本（有weight stashing）需要存储 `τ_i` 倍权重副本，内存线性增长于阶段数。虽可卸载至CPU，但仍可能成为资源瓶颈。
4. **实验范围有限**：仅测试了decoder-only架构（NanoGPT类），未涉及encoder-decoder（如T5）或其他任务（如图像分类）。也未测试更大规模（如10B+）模型或更多阶段。
5. **SWARM实验局限**：仅测试无权重存储版本（Ours-No-WS），未验证基本版本（有weight stashing）在SWARM中的表现。
6. **对比方法选择**：未包括最新的Zero Bubble等低气泡调度方法（虽然它们基于同步但气泡已减少），也未包括高效梯度压缩等异步替代方案。
7. **没有报告绝对训练时间**：仅基于迭代比较，未提供完整端到端加速比（但承认GPipe受微批次限制更新次数更少）。

（完）
