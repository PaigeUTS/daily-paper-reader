---
title: "OWL: Optimized Workforce Learning for General Multi-Agent Assistance in Real-World Task Automation"
title_zh: OWL：面向通用多智能体协助的优化工作力学习
authors: "Mengkang Hu, Yuhang Zhou, Wendong Fan, Yuzhou Nie, Ziyu Ye, Bowei Xia, Tao Sun, Zhaoxuan Jin, Yingru Li, Zeyu Zhang, Yifeng Wang, Qianshuo Ye, Bernard Ghanem, Ping Luo, Guohao Li"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=MBJ46gd1CT"
tags: ["query:agents-os"]
score: 7.0
evidence: 分层多智能体框架用于任务自动化
tldr: 现有LLM多智能体系统领域专用性强，迁移需完全重设计。本文提出Workforce分层框架，将规划、协调和执行解耦，包含领域无关的规划器、协调器和领域专用的工作者。该架构支持跨域迁移，为智能体异构计算基础设施的设计提供了模块化方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-mbj46gd1ct/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1352, \"height\": 772, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mbj46gd1ct/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1425, \"height\": 518, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mbj46gd1ct/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 501, \"height\": 443, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mbj46gd1ct/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1435, \"height\": 557, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mbj46gd1ct/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1352, \"height\": 719, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-mbj46gd1ct/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1396, \"height\": 834, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-mbj46gd1ct/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1496, \"height\": 1079, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mbj46gd1ct/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 931, \"height\": 262, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mbj46gd1ct/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1404, \"height\": 374, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mbj46gd1ct/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1435, \"height\": 601, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mbj46gd1ct/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1388, \"height\": 672, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mbj46gd1ct/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1505, \"height\": 378, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mbj46gd1ct/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1448, \"height\": 738, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mbj46gd1ct/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1018, \"height\": 705, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mbj46gd1ct/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1158, \"height\": 274, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-mbj46gd1ct/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1382, \"height\": 310, \"label\": \"Table\"}]"
motivation: 多智能体系统跨域迁移需要完全重设计，缺乏泛化性。
method: 提出分层解耦框架：领域无关规划器、协调器和领域专用工作者。
result: 实现了跨域迁移能力，无需完全重训练。
conclusion: 层次化解耦设计是构建通用智能体基础设施的有效途径。
---

## Abstract
Large Language Model (LLM)-based multi-agent systems show promise for automating real-world tasks but struggle to transfer across domains due to their domain-specific nature.
Current approaches face two critical shortcomings: they require complete architectural redesign and full retraining of all components when applied to new domains.
We introduce **Workforce**, a hierarchical multi-agent framework that decouples strategic planning from specialized execution through a modular architecture comprising:
*(i)* a *domain-agnostic* **Planner** for task decomposition,
*(ii)* a **Coordinator** for subtask management, and
*(iii)* specialized **Workers** with *domain-specific* tool-calling capabilities.
This decoupling enables cross-domain transferability during both inference and training phases:
During inference, Workforce seamlessly adapts to new domains by adding or modifying worker agents;
For training, we introduce **Optimized Workforce Learning (OWL)**, which improves generalization across domains by optimizing a domain-agnostic planner with reinforcement learning from real-world feedback.
To validate our approach, we evaluate Workforce on the GAIA benchmark, covering various realistic, multi-domain agentic tasks.
Experimental results demonstrate Workforce achieves open-source state-of-the-art performance (**69.70%**), outperforming commercial systems like OpenAI's Deep Research by **2.34%**.
More notably, our OWL-trained 32B model achieves **52.73%** accuracy (**+16.37%**) and demonstrates performance comparable to GPT-4o on challenging tasks.
To summarize, by enabling scalable generalization and modular domain transfer, our work establishes a foundation for the next generation of general-purpose AI assistants.

*Our code is available at [Anonymous URL](https://anonymous.4open.science/r/annonymous-owl/), and our data is available at [Anonymous URL](https://huggingface.co/anonymous21016).*

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：当前基于大型语言模型（LLM）的多智能体系统在自动化真实世界任务上展现出潜力，但存在严重的**领域专用性**问题：迁移到新领域时，必须完全重新设计架构并重新训练所有组件，导致灵活性极差。
- **整体含义**：本文旨在构建一种**可跨域迁移、模块化、无需完全重训**的通用多智能体系统，为下一代通用AI助手提供可扩展的基础。

## 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

### 核心思想
- **解耦战略规划与领域专用执行**。将系统划分为三个独立模块：
  - **领域无关的规划器（Domain-agnostic Planner）**：负责高层任务分解，生成抽象子任务序列。
  - **协调器（Coordinator）**：管理子任务分配、依赖关系和中间结果集成。
  - **领域专用工作者节点（Worker Nodes）**：每个工作者配备专用工具集，执行具体子任务（如网络搜索、文档处理、推理编码）。

### 关键技术细节
- **通信机制**：通过共享任务通道（Task Channel）实现集中式通信，工作者仅提交最终结果，保持上下文清洁。
- **重规划机制**：当工作者报告子任务失败时，规划器可根据失败信息重新计划新的子任务，实现测试时缩放（test-time scaling）。
- **训练方法（OWL）**：
  - **两阶段训练**：
    1. **监督微调（SFT）**：使用专家轨迹初始化规划器，轨迹由Workforce框架（使用GPT-4o-mini）在四个数据集上合成并过滤。
    2. **强化学习（DPO）**：从SFT模型生成多条轨迹，构建偏好对（正确/错误答案），进一步提升规划器的泛化能力。
  - **任务课程**：精心选择四个覆盖不同认知能力的数据集（HotpotQA、WikiTableQuestions、Math、Infinity-MM），确保规划器接触多样化的推理模式。

### 算法流程（文字说明）
1. 规划器根据任务描述和工作者能力注册表，分解任务为子任务列表。
2. 协调器为每个子任务分配最合适的工作者。
3. 工作者执行子任务，若成功则返回结果，若失败则报告失败信息。
4. 若出现失败，规划器根据反馈生成新的子任务（重规划），最多尝试K次。
5. 最终，规划器综合所有子任务结果，生成最终输出。

## 3. 实验设计

### 基准数据集
- **GAIA基准（General AI Assistants）**：包含三个难度级别（Level 1～3），涵盖多模态推理、代码执行、实时网络搜索等复杂真实任务。

### 对比方法
- **商业闭源系统**：OpenAI Deep Research、h2oGPTe Agent、Trase Agent、Langfun Agent等。
- **开源框架**：HuggingFace Agents、Magnetic-One、AutoAgent、Open Deep Research、TapeAgents等。
- **基线模型**：单智能体（Single Agent）、角色扮演（Role Playing）——均使用与Workforce相同的工具集。

### 主要结果
- **Workforce（Claude-3.7-Sonnet）** 达到 **69.70%** 准确率，超越OpenAI Deep Research（67.36%）2.34%，且在所有开源框架中最佳。
- **OWL训练的Qwen2.5-32B** 在GAIA上从36.36%提升至 **52.73%**（+16.37%），超越GPT-4o-mini（47.27%）和Qwen2.5-72B（49.09%），在Level 3任务上与GPT-4o相当。

## 4. 资源与算力
- **训练硬件**：8块 **NVIDIA H100 GPU**（文中未明确说明具体型号，推断为标准H100 80GB）。
- **训练框架**：使用 **LlamaFactory**，bfloat16混合精度训练。
- **超参数**：学习率1e-5，有效batch size 12（per-device batch size 1，梯度累积12步），训练2个epoch。
- **推理**：通过API调用模型，无需GPU。
- **数据合成**：使用GPT-4o-mini生成轨迹，SFT数据集1599条，DPO数据集1009对。

## 5. 实验数量与充分性
- **主表对比**：表1对比了14种以上基线（含不同模型与方法），涵盖商业、开源、单智能体、多智能体。
- **训练方法对比**：表3对比了不同规划器模型（GPT-4o-mini、Qwen2.5-72B、Claude-3.7-Sonnet等）及OWL的影响。
- **消融实验**：图2a（轨迹过滤效果）、图4c（Planner vs Worker训练）、图3a（按能力类型分析）、图3b（测试时缩放）、图4b（不同能力需求下的鲁棒性）。
- **误差分析**：表7给出详细错误类型分布（6大类、14小类），并附示例（附录E）。
- **统计显著性**：附录H进行了Wilcoxon符号秩检验，p值均小于0.05，表明改进显著。
- **充分性评价**：实验覆盖了系统性能、训练策略、泛化性、鲁棒性、错误分析等多方面，设计较为完整。但GAIA基准本身可能存在数据污染问题（作者已屏蔽部分网站），结果可信。

## 6. 论文的主要结论与发现
1. **分层解耦架构有效**：将规划与执行分离，实现了跨域迁移，无需重新训练整个系统。
2. **开源SOTA性能**：Workforce在GAIA上超越所有开源系统，甚至超过商业Deep Research。
3. **训练规划器比训练工作者更高效**：仅训练规划器即可显著提升性能（+16.37%），而训练工作者反而可能下降；两者联合训练增益有限。
4. **强化学习改善泛化**：SFT单独提升简单任务，但损害复杂任务（Level 3下降3.85%）；DPO恢复了并超过基线。
5. **重规划机制实现测试时缩放**：增加重规划次数可提高性能，系统具备自我修正能力。

## 7. 优点
- **模块化与可迁移性**：通过解耦规划与执行，新领域仅需替换或增加工作者节点，无需修改规划器。
- **训练效率高**：仅优化一个规划器（32B模型），计算开销远低于全系统训练。
- **性能领先**：在开源框架中首次超越商业系统，且使用相对较小的模型（32B）即可接近GPT-4o。
- **完全开源**：代码、模型、数据均已公开，便于复现与社区发展。

## 8. 不足与局限
1. **依赖高质量工具集**：系统性能受限于工作者工具的质量与可用性，在新领域若缺乏可靠工具则可能形成执行瓶颈。
2. **强化学习训练耗时**：从真实世界反馈（如网络搜索）进行RL存在延迟问题，影响训练效率。
3. **数据集污染风险**：GAIA的部分答案可能已在互联网泄露，作者虽采取了屏蔽措施，但无法完全避免。
4. **实验覆盖有限**：仅在GAIA一个基准上验证，未在其他多智能体任务（如WebArena、SWE-bench等）上进行广泛测试。
5. **模型规模局限**：OWL训练仅针对32B模型，更大模型（如70B+）或不同架构上的效果未探讨。
6. **错误分析显示规划器错误仍是主要失败类型（21.15%）**，说明规划能力仍有优化空间。
7. **工具层面的失败（如网络搜索超时、验证码拦截等）占比大（32.69%）**，系统对网络环境的鲁棒性有待提升。

（完）
