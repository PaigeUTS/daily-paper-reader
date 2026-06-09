---
title: "ShieldAgent: Shielding Agents via Verifiable Safety Policy Reasoning"
title_zh: ShieldAgent：通过可验证安全策略推理保护智能体
authors: "Zhaorun Chen, Mintong Kang, Bo Li"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=DkRYImuQA9"
tags: ["query:agents-os"]
score: 8.0
evidence: ShieldAgent通过可验证策略推理实现智能体安全防护，直接对应复合主题中的智能体安全演进
tldr: 针对自主智能体易受恶意指令攻击且现有大模型防护措施不适用的问题，提出ShieldAgent，这是一种基于逻辑推理的防护智能体，能够从策略文档中提取可验证规则并构建安全策略模型，通过动作轨迹合规检查确保其他智能体的安全行为。实验表明其有效防御多种攻击，为智能体安全提供可验证的保障机制，对AI系统安全演进具有重要价值。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-dkryimuqa9/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1766, \"height\": 835, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dkryimuqa9/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 848, \"height\": 492, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dkryimuqa9/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 862, \"height\": 391, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dkryimuqa9/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 830, \"height\": 497, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dkryimuqa9/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 988, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dkryimuqa9/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 824, \"height\": 495, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dkryimuqa9/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1627, \"height\": 1745, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dkryimuqa9/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1073, \"height\": 845, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dkryimuqa9/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1074, \"height\": 706, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dkryimuqa9/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1069, \"height\": 705, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dkryimuqa9/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1288, \"height\": 620, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dkryimuqa9/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1083, \"height\": 82, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dkryimuqa9/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1473, \"height\": 506, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dkryimuqa9/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1648, \"height\": 909, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dkryimuqa9/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1635, \"height\": 1641, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dkryimuqa9/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1520, \"height\": 459, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-dkryimuqa9/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1775, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dkryimuqa9/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1782, \"height\": 412, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dkryimuqa9/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 835, \"height\": 259, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dkryimuqa9/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 857, \"height\": 266, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dkryimuqa9/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1069, \"height\": 301, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dkryimuqa9/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1610, \"height\": 425, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dkryimuqa9/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1776, \"height\": 338, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dkryimuqa9/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1286, \"height\": 395, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dkryimuqa9/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 476, \"height\": 310, \"label\": \"Table\"}]"
motivation: 自主智能体面临恶意指令和攻击，现有大模型防护措施不适用于智能体的动态和复杂环境。
method: 提出ShieldAgent，从政策文档提取可验证规则构建安全策略模型，通过逻辑推理检查智能体动作轨迹的合规性。
result: ShieldAgent能有效检测和防御多种攻击，确保智能体行为符合预定义安全策略。
conclusion: ShieldAgent为智能体安全提供了可验证的防护方案，推动了自主智能体的安全演进。
---

## Abstract
Autonomous agents powered by foundation models have seen widespread adoption across various real-world applications. However, they remain highly vulnerable to malicious instructions and attacks, which can result in severe consequences such as privacy breaches and financial losses. More critically, existing guardrails for LLMs are not applicable due to the complex and dynamic nature of agents. To tackle these challenges, we propose ShieldAgent, the first guardrail agent designed to enforce explicit safety policy compliance for the action trajectory of other protected agents through logical reasoning. Specifically, ShieldAgent first constructs a safety policy model by extracting verifiable rules from policy documents and structuring them into a set of action-based probabilistic rule circuits. Given the action trajectory of the protected agent, ShieldAgent retrieves relevant rule circuits and generates a shielding plan, leveraging its comprehensive tool library and executable code for formal verification. In addition, given the lack of guardrail benchmarks for agents, we introduce ShieldAgent-Bench, a dataset with 3K safety-related pairs of agent instructions and action trajectories, collected via SOTA attacks across 6 web environments and 7 risk categories. Experiments show that ShieldAgent achieves SOTA on ShieldAgent-Bench and three existing benchmarks, outperforming prior methods by 11.3% on average with a high recall of 90.1%. Additionally, ShieldAgent reduces API queries by 64.7% and inference time by 58.2%, demonstrating its high precision and efficiency in safeguarding agents. Our project is available and continuously maintained here: https://shieldagent-aiguard.github.io/

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：基于大语言模型（LLM）的自主智能体（如 web agent）在真实应用中广泛使用，但极易受到恶意指令和对抗攻击，导致隐私泄露、财务损失等严重后果。现有的 LLM 防护机制（如 LlamaGuard）仅针对模型本身或文本内容过滤，无法应对智能体动态、多步交互和复杂策略环境。
- **整体含义**：本文提出 **ShieldAgent**，是首个**通过逻辑推理显式强制执行安全策略合规的防护智能体**，旨在对目标智能体的动作轨迹进行实时可验证防护，填补了智能体安全防护领域的空白。

### 2. 方法论

- **核心思想**：
  - 构建**基于动作的安全策略模型（ASPM）**：从政策文档（如 EU AI Act、公司手册）中自动提取可验证规则，经迭代优化（验证性细化 + 冗余剪枝）后，按动作类型聚类形成结构化概率规则电路。
  - **推理阶段**：给定被保护智能体的动作轨迹，ShieldAgent 检索对应的规则电路，生成防护计划，利用工具库（搜索、检测、形式验证）等操作为谓词赋值，运行形式化验证代码（如 Prover9），最后通过概率推断（基于马尔可夫逻辑网络）输出安全标签、违反规则及详细解释。
- **关键技术细节**：
  - **规则提取**：基于 GPT-4o 将政策文档转为结构化的 LTL（线性时序逻辑）规则，每条规则包含谓词集、自然语言描述、LTL 表达式、规则类型（动作/物理）。
  - **结构优化**：先进行**验证性细化（VR）**：将模糊或复合规则分解为原子、可验证的规则；后进行**冗余剪枝（RP）**：通过嵌入相似度聚类合并语义相似的谓词和规则，交替迭代直到收敛。
  - **ASPM 聚类与推断**：对状态谓词进行谱聚类，将涉及相同动作的规则合并为动作电路 C_{pa}；推理时，对被检查动作 pa 对应的电路，利用 Markov Logic Network 计算所有谓词赋值下的联合概率，并通过**相对安全条件**给出标签：
    - \( l_s(a_i) = 1 \iff P_\theta(\mu_{pa=1}) - P_\theta(\mu_{pa=0}) \ge \epsilon \)
    - 该条件控制动作执行前后安全概率的变化，确保动态安全。
  - **权重学习**：通过优化守卫铰链损失 \( L_g(\theta) \) 学习规则权重，避免将规则视为硬约束，降低误报率。
- **算法流程**：Algorithm 1 给出推理流程：提取动作谓词→检索电路→依次验证每条规则（检索历史工作流、生成防护计划、执行操作赋值、形式验证）→概率推断→输出结果。

### 3. 实验设计

- **数据集 / 场景**：
  - **自建基准 ShieldAgent-Bench**：包含 **3110** 个安全相关动作轨迹对（每个指令配一条安全轨迹和两条由不同攻击产生的风险轨迹），覆盖 **6** 个 web 环境（Shopping、CMS、Reddit、GitLab、Maps、SuiteCRM），**7** 个风险类别（访问限制、内容限制、幻觉、指令遵从、操作限制、典型错误模式、长期风险）。
  - **现有基准**：ST-WebAgentBench（234 个任务）、VWA-Adv（200 个对抗任务，基于 VisualWebArena）、AgentHarm（110 个恶意任务，11 类危害）。需为这些基准补充完整轨迹和策略标签。
- **对比方法**：
  - **Direct**：直接提供完整策略给 GPT-4o 要求输出安全标签。
  - **Rule traverse**：逐条遍历规则，调用 GPT-4o 判断是否违反。
  - **GuardAgent**：按照其流水线设置防护请求（Xiang et al., 2024）。
- **评估指标**：防护准确率（ACC）、假阳性率（FPR）、规则召回率（ARR）、API 查询次数（NoQ）、推理时间（秒/样本）。此外还进行了**在线防护评估**（与 AWM 代理集成，逐步反馈提高策略遵守率）。

### 4. 资源与算力

- 论文**未明确说明**使用的 GPU 型号、数量及训练时长。仅提及使用 GPT-4o 进行策略提取和细化，训练权重时可能使用少量 GPU（未具体给出）。附录中未提供计算资源细节。

### 5. 实验数量与充分性

- **实验组数丰富**：在自建基准上对比了 4 种方法在两种攻击源（agent-based、environment-based）下的 7 个风险类别准确率、总体 ACC/FPR/ARR 和成本；在 3 个外部基准上分别对比 ACC/FPR；额外进行了在线防护实验（6 个环境，对比 4 种方法）。还提供了 ASPM 结构优化的统计（表 8）和迭代曲线（图 4-6）。
- **充分性与公平性**：所有方法输入相同的安全策略，输出要求一致的标签和违规规则列表；指标涵盖准确率、误报、召回、成本，较全面。消融实验（VR 和 RP 优化）展示了规则数目和模糊度变化。实验设计合理，结果客观。

### 6. 论文的主要结论与发现

- ShieldAgent 在 ShieldAgent-Bench 上达到 SOTA，比最佳基线（Rule traverse）平均准确率高出 **11.3%**，假阳性率最低（**4.8%**），规则召回率高达 **90.1%**，API 查询减少 **64.7%**，推理时间减少 **58.2%**。
- 在三个现有基准（ST-WebAgentBench、VWA-Adv、AgentHarm）上平均 ACC 提升 **7.4%**，且 FPR 均低于或接近基线方法。
- 在线防护设置下，ShieldAgent 在所有 6 个环境中都取得最高策略遵守率（平均约 60~80%），证明了其作为 System 2 与任务代理集成的有效性。
- 结论：通过逻辑推理和结构化策略模型，ShieldAgent 能实现高效、强健、可解释的智能体安全防护，且显著降低计算开销。

### 7. 优点

- **创新性**：首个专门针对智能体动作序列进行显式策略合规的防护方案，区别于仅处理文本的 LLM 守卫。
- **理论扎实**：结合概率推理（马尔可夫逻辑网络）和形式化验证（LTL、Prover9），并引入控制屏障证书思想设计相对安全条件。
- **自动化程度高**：自动提取策略、迭代优化规则、学习权重，减少人工成本。
- **效率与精度兼顾**：通过动作电路聚类、混合记忆模块、专用微调模型，实现了低 API 调用和低延迟。
- **可解释性**：输出违反规则、详细解释和补救建议，便于用户理解与纠正。
- **基准贡献**：构建了首个覆盖多环境、多风险类别、带显式规则标注的智能体防护基准 ShieldAgent-Bench，推动领域评估标准化。

### 8. 不足与局限

- **资源消耗不完全明确**：未公开训练/推理的具体硬件需求和能耗，可能影响可复现性评估。
- **对 LLM 的依赖**：策略提取和规则细化依赖 GPT-4o，存在成本、延迟和潜在偏差；且对无官方政策文档的环境需人工预设规则。
- **风险类别覆盖有限**：仅针对 web 环境，未扩展到 GUI、具身、代码等其它智能体类型；对幻觉类风险表现稍弱（需外部知识验证）。
- **对抗鲁棒性有待进一步检验**：虽然针对两类攻击进行了评估，但未分析对抗性策略绕过 ShieldAgent 本身的可能性。
- **规则优化依赖嵌入模型**：使用基于文本嵌入的相似度阈值进行冗余剪枝，可能遗漏语义相似但语境不同的规则，引入错误合并。
- **实验公平性约束**：现有基线（Direct、Rule traverse、GuardAgent）在提供策略后可能因上下文长度限制而性能受损，但文章已尽力实现同等输入条件。
- **在线评估仅用 AWM 代理**：未验证与其他类型代理（如基于视觉的代理）的兼容性。

（完）
