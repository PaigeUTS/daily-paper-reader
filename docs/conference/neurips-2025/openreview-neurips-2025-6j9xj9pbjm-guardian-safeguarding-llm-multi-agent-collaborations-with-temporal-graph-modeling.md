---
title: "GUARDIAN: Safeguarding LLM Multi-Agent Collaborations with Temporal Graph Modeling"
title_zh: GUARDIAN：用时序图建模保护大语言模型多智能体协作安全
authors: "Jialong Zhou, Lichao Wang, Xiao Yang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=6j9xJ9pBjm"
tags: ["query:agents-os"]
score: 7.0
evidence: 用时序图建模保护多智能体协作安全
tldr: 针对大语言模型多智能体协作中的幻觉放大和错误传播等安全问题，提出GUARDIAN方法。该方法将协作过程建模为离散时间时序属性图，利用无监督编码器-解码器结构学习重构节点属性，从而检测和缓解多类安全威胁。实验表明该方法能有效捕捉错误传播动态，为智能体系统的安全演进提供了关键技术支持。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-6j9xj9pbjm/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1448, \"height\": 553, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-6j9xj9pbjm/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1415, \"height\": 367, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-6j9xj9pbjm/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1282, \"height\": 660, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-6j9xj9pbjm/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1437, \"height\": 315, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-6j9xj9pbjm/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1456, \"height\": 352, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-6j9xj9pbjm/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 710, \"height\": 310, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-6j9xj9pbjm/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 570, \"height\": 458, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-6j9xj9pbjm/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1416, \"height\": 1953, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-6j9xj9pbjm/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1415, \"height\": 2364, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-6j9xj9pbjm/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1419, \"height\": 2081, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-6j9xj9pbjm/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1447, \"height\": 630, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6j9xj9pbjm/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1435, \"height\": 226, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6j9xj9pbjm/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 688, \"height\": 296, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6j9xj9pbjm/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 656, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6j9xj9pbjm/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 719, \"height\": 352, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6j9xj9pbjm/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1153, \"height\": 203, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6j9xj9pbjm/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1184, \"height\": 578, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6j9xj9pbjm/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1191, \"height\": 1209, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6j9xj9pbjm/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1090, \"height\": 1302, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6j9xj9pbjm/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1191, \"height\": 619, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6j9xj9pbjm/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 697, \"height\": 358, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6j9xj9pbjm/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1442, \"height\": 255, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6j9xj9pbjm/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1444, \"height\": 287, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6j9xj9pbjm/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1444, \"height\": 287, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6j9xj9pbjm/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 699, \"height\": 369, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6j9xj9pbjm/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 700, \"height\": 424, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-6j9xj9pbjm/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 700, \"height\": 425, \"label\": \"Table\"}]"
motivation: 多智能体协作面临幻觉放大和错误注入与传播等关键安全挑战。
method: 将协作过程建模为离散时间时序属性图，使用无监督编码器-解码器学习重构节点属性。
result: 能有效捕获并减轻幻觉和错误的传播动态。
conclusion: GUARDIAN为多智能体系统的安全检测与缓解提供了统一框架。
---

## Abstract
The emergence of large language models (LLMs) enables the development of intelligent agents capable of engaging in complex and multi-turn dialogues. However, multi-agent collaboration faces critical safety challenges, such as hallucination amplification and error injection and propagation. This paper presents GUARDIAN, a unified method for detecting and mitigating multiple safety concerns in GUARDing Intelligent Agent collaboratioNs. By modeling the multi-agent collaboration process as a discrete-time temporal attributed graph, GUARDIAN explicitly captures the propagation dynamics of hallucinations and errors. The unsupervised encoder-decoder architecture incorporating an incremental training paradigm learns to reconstruct node attributes and graph structures from latent embeddings, enabling the identification of anomalous nodes and edges with unparalleled precision. Moreover, we introduce a graph abstraction mechanism based on the Information Bottleneck Theory, which compresses temporal interaction graphs while preserving essential patterns. Extensive experiments demonstrate GUARDIAN's effectiveness in safeguarding LLM multi-agent collaborations against diverse safety vulnerabilities, achieving state-of-the-art accuracy with efficient resource utilization. The code is available at https://github.com/JialongZhou666/GUARDIAN.

---

## 论文详细总结（自动生成）

# GUARDIAN: 用时序图建模保护大语言模型多智能体协作安全 — 中文总结

## 1. 核心问题与研究动机
- **研究背景**：大语言模型（LLM）的发展使得构建能够进行复杂多轮对话的智能体成为可能。多智能体协作系统（如基于Agent2Agent协议）允许多个LLM智能体通过交互通信和协作推理共同解决复杂问题。
- **核心安全问题**：协作过程中面临两类关键安全挑战：
  - **幻觉放大（Hallucination Amplification）**：一个智能体产生的非事实性信息在网络中传播并放大，导致所有智能体输出被污染。
  - **错误注入与传播（Error Injection and Propagation）**：恶意行为者通过智能体定向攻击（修改提示）或通信定向攻击（篡改智能体间信息流）故意引入错误，使原本可靠的智能体继承并扩散错误。
- **现有方法不足**：现有防御方法（如交叉检查、外部反馈、多数投票、不确定性估计）要么忽略多智能体环境下的传播动力学，要么简化智能体依赖关系，或需要对基础模型进行修改（不适用于闭源模型）。
- **研究目标**：开发一种**统一方法**，能够检测并缓解多智能体协作中的多种安全问题（幻觉放大和错误注入/传播），且保持模型无关性。

## 2. 方法论：核心思想与关键技术
### 2.1 核心思想
- **时序属性图建模**：将多智能体协作过程建模为**离散时间时序属性图**（Discrete-time Temporal Attributed Graph），其中：
  - **节点**：每个智能体在不同时间步的实例（\(v_{t,i}\)），节点特征为智能体响应的BERT嵌入。
  - **边**：连续时间步间的有向通信边（\(v_{t-1,i} \to v_{t,j}\)），表示信息传递。
- **异常检测**：通过无监督编码器-解码器架构学习重构正常模式，异常节点/边导致高重构误差，从而被识别并移除。

### 2.2 关键技术细节
1. **编码器-解码器架构（四组件）**：
   - **属性图编码器**：使用两层GCN聚合邻居信息，获得节点嵌入 \(Z_t\)。
   - **时间信息编码器**：基于Transformer的时序自注意力机制，处理 \(\{Z_1,...,Z_T\}\) 序列，生成当前时间步最终表示 \(\bar{Z}_T\)。
   - **属性重构解码器**：从 \(\bar{Z}_T\) 重构节点属性 \(\hat{X}_T\)，计算均方误差损失 \(L_{att}\)。
   - **结构重构解码器**：重构邻接矩阵 \(\hat{E}_T\)，计算二元交叉熵损失 \(L_{stru}\)。
2. **信息瓶颈（IB）图抽象**：
   - 目标：最小化 \(L_{GIB} = I(X_t;Z_t) - \beta I(Z_t;Y_t)\)，在压缩信息的同时保留任务相关模式。
   - 理论保证：智能体间信息流受可控压缩率 \(\eta\) 约束，历史与当前状态间的信息流受先验约束。
3. **增量训练范式**：
   - 利用时序结构：用早期时间步训练模型，检测后期时间步的异常。
   - 每轮检测后移除已识别的异常节点，不断微调模型以适应动态变化。
   - 总损失：\(L_{total} = L_{rec} + \lambda L_{GIB}\)，其中 \(L_{rec} = \alpha L_{att} + (1-\alpha)L_{stru}\)。

### 2.3 算法流程（文字说明）
1. 输入：时序图序列 \(\{G_t\}\)，每图含节点、边和属性。
2. 图预处理：用BERT生成节点嵌入；构建邻接矩阵。
3. 属性图编码器（GCN）生成节点嵌入 \(Z_t\)。
4. 时间信息编码器（Transformer）融合历史信息得到 \(\bar{Z}_T\)。
5. 属性重构解码器输出 \(\hat{X}_T\)，结构重构解码器输出 \(\hat{E}_T\)。
6. 计算重构误差，得到节点异常分数 \(s_v\)，剔除分数高于阈值 \(\tau\) 的节点。
7. 更新图序列，重复步骤2-6进行增量学习。

## 3. 实验设计
### 3.1 数据集
- **MMLU**：多学科知识问答（57个主题，多项选择）。
- **MATH**：数学推理（12,500道竞赛题）。
- **FEVER**：事实性验证（维基百科声明，标注支持/反驳/信息不足）。
- **Biographies**：计算机科学家传记生成（524个实体）。
- 每个数据集随机抽样100个问题，进行3次独立测试。

### 3.2 场景设置
- **幻觉放大**：不涉及人为因素，智能体自发产生并传播幻觉。
- **错误注入与传播**：
  - **智能体定向攻击**：第一轮随机选择1个恶意智能体。
  - **通信定向攻击**：中间轮次随机干扰多个通信边。
- 测试拓扑鲁棒性：连接稀疏度25%、50%、75%。
- 可扩展性测试：智能体数量3-7个。

### 3.3 对比方法
- **基础多智能体框架**：LLM Debate、DyLAN。
- **幻觉检测**：SelfCheckGPT。
- **错误检测**：Challenger、Inspector。
- **GUARDIAN变体**：
  - GUARDIAN.s：仅用当前时间步静态图。
  - GUARDIAN：使用历史图信息（完整方法）。
- 骨干模型：GPT-3.5-turbo、GPT-4o、Claude-3.5-sonnet、Llama3.1-8B。

### 3.4 评估指标
- 准确率、异常检测率、错误发现率（FDR）、API调用次数、运行时效率。

## 4. 资源与算力
- 论文**未明确提供具体的GPU型号、数量或训练时长**。
- 但报告了运行时效率（平均每问题耗时）和API调用次数，表明GUARDIAN在MMLU和FEVER上耗时最低，在MATH上略高于LLM Debate但远低于其他防御方法。
- 提到模型为“无监督”，且增量训练仅需轻量级微调（小规模时序图），整体计算开销较低。

## 5. 实验数量与充分性
- **大量实验**：涵盖3种安全场景、4个数据集、5种骨干模型、多种对比方法、多组消融实验（参数α和γ）、拓扑鲁棒性分析、可扩展性分析（3-7智能体）。
- **充分性评价**：实验设计较为全面，包括与多种基线对比（共6种）、在多个LLM上验证、消融研究关键超参数、提供FDR分析异常检测可靠性、展示真实案例（图4）。实验设置公平（均采用零样本CoT设置，统一回合数）。
- **潜在不足**：未报告误差棒（如标准差），未进行统计显著性检验；仅在有限数据集上测试（非全部基准）。

## 6. 主要结论与发现
- **GUARDIAN在幻觉放大下**：平均准确率比最佳基线提升4.2%，在MATH数据集上提升7.1%（GPT-3.5-turbo达15.4%）。
- **在错误注入与传播下**：
  - 智能体定向攻击：MATH上提升4.3%，GPT-3.5-turbo提升8.6%。
  - 通信定向攻击：MMLU和MATH上提升3.6%，GPT-3.5-turbo提升7.5%-7.7%。
- **异常检测率**：平均超过80%，最高达94.74%。
- **FDR较低**：多数场景下小于20%，在MATH上仅8.32%。
- **拓扑鲁棒性**：在稀疏连接（25%）下仍优于所有基线。
- **可扩展性**：智能体数3-7时性能稳定（4为最优）。
- **API调用最少**：相比所有基线显著降低。
- **运行时效率**：大多数数据集耗时最低或接近最优。

## 7. 优点
1. **统一框架**：同时检测幻觉放大和错误注入/传播，无需修改底层LLM。
2. **时序图建模创新**：将协作过程显式表示为时序属性图，自然捕捉错误传播动态。
3. **信息瓶颈理论应用**：首次系统性地将IB原理用于LLM多智能体安全，提供理论保证。
4. **无监督学习**：不依赖标注数据，适应动态环境。
5. **增量训练范式**：利用时序结构持续学习，有效利用历史信息。
6. **实验全面**：覆盖多种场景、模型、数据集，消融研究验证关键组件。
7. **低开销**：API调用和运行时均较低，实用性强。

## 8. 不足与局限
1. **未报告误差棒**：缺乏统计显著性指标，结果稳定性需进一步验证。
2. **数据集规模有限**：每个数据集仅抽样100题，可能无法代表整体难度分布。
3. **仅测试有限模型**：虽覆盖GPT-3.5/4o、Claude-3.5、Llama3.1-8B，但未测试更多开源模型或更大参数模型。
4. **虚假发现率存在波动**：部分场景FDR达30.67%（MMLU通信攻击），存在误删正常智能体的风险。
5. **依赖预定义拓扑**：实验假设固定通信拓扑（完全连接或稀疏模式），未探索动态拓扑变化。
6. **未讨论可解释性**：虽然提供可视化，但未深入分析异常判据的可解释性。
7. **训练细节缺失**：未提供GPU型号、训练时长等资源消耗，影响可复现性。
8. **仅限文本属性**：节点特征仅使用BERT嵌入，未尝试其他语义特征（如知识图谱增强）。

（完）
