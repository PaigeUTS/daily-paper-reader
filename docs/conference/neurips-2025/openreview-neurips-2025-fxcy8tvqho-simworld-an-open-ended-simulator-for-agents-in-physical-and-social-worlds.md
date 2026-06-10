---
title: "SimWorld: An Open-ended Simulator for Agents in Physical and Social Worlds"
title_zh: SimWorld：面向物理和社会世界的开放式智能体模拟器
authors: "Xiaokang Ye, Jiawei Ren, Yan Zhuang, Xuhong He, Yiming Liang, Yiqing Yang, Mrinaal Dogra, Xianrui Zhong, Eric Liu, Kevin Benavente, Rajiv Mandya Nagaraju, Dhruv Vivek Sharma, Ziqiao Ma, Tianmin Shu, Zhiting Hu, Lianhui Qin"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=FxCy8TvQHO"
tags: ["query:agents-os"]
score: 4.0
evidence: 模拟器用于复杂环境中的AI智能体
tldr: 现有世界模拟器局限于手工场景和简化物理/社会规则，缺乏对LLM/VLM智能体的原生支持。本文基于Unreal Engine 5构建SimWorld，提供丰富的真实世界环境，支持智能体大规模交互、推理和训练。该模拟器为智能体基础设施设计提供了评估平台，但与服务器操作系统直接关联较弱。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1160, \"height\": 634, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1438, \"height\": 454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1441, \"height\": 509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 662, \"height\": 387, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 800, \"height\": 366, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 594, \"height\": 467, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 580, \"height\": 411, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1412, \"height\": 433, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1391, \"height\": 712, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1447, \"height\": 704, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1451, \"height\": 785, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1372, \"height\": 798, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1388, \"height\": 1064, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1446, \"height\": 289, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1450, \"height\": 250, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1428, \"height\": 1909, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1443, \"height\": 443, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1441, \"height\": 1301, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 452, \"height\": 324, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 455, \"height\": 327, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 451, \"height\": 327, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 449, \"height\": 270, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1442, \"height\": 1138, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1415, \"height\": 1110, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1441, \"height\": 1309, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 1451, \"height\": 402, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1326, \"height\": 372, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 1438, \"height\": 1389, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 1444, \"height\": 725, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-fxcy8tvqho/fig-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 1443, \"height\": 939, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-fxcy8tvqho/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1450, \"height\": 470, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fxcy8tvqho/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1346, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fxcy8tvqho/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1442, \"height\": 399, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fxcy8tvqho/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1356, \"height\": 924, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fxcy8tvqho/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 994, \"height\": 284, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fxcy8tvqho/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 934, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-fxcy8tvqho/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1450, \"height\": 439, \"label\": \"Table\"}]"
motivation: 现有模拟器无法支持LLM/VLM智能体在复杂真实世界中的开发。
method: 基于Unreal Engine 5构建开放世界模拟器，原生支持LLM/VLM智能体。
result: 提供了丰富的物理和社会环境用于智能体评估。
conclusion: SimWorld可作为智能体基础设施的测试床，但非核心系统。
---

## Abstract
While LLM/VLM-powered AI agents have advanced rapidly in math, coding, and computer use, their applications in complex physical and social environments remain challenging. Building agents that can survive and thrive in the real world (e.g., by autonomously earning income) requires massive-scale interaction, reasoning, training, and evaluation across diverse scenarios. However, existing world simulators for such development fall short: they often rely on limited hand-crafted environments, simulate simplified game-like physics and social rules, and lack native support for LLM/VLM agents. We introduce SimWorld, a new simulator built on Unreal Engine 5, designed for developing and evaluating LLM/VLM agents in rich, real-world-like settings. SimWorld offers three core capabilities: (1) realistic, open-ended world simulation, including accurate physical and social dynamics and language-driven procedural environment generation; (2) rich interface for LLM/VLM agents, with multi-modal world inputs/feedback and open-vocabulary action outputs at varying levels of abstraction; and (3) diverse physical and social reasoning scenarios that are easily customizable by users. We demonstrate SimWorld by deploying frontier LLM agents (e.g., Gemini-2.5-Flash, Claude-3.5, GPT-4o, and DeepSeek-Prover-V2) on both short-horizon navigation tasks requiring grounded re-planning, and long-horizon multi-agent food delivery tasks involving strategic cooperation and competition. The results reveal distinct reasoning patterns and limitations across models. We open-source SimWorld and hope it becomes a foundational platform for advancing real-world agent intelligence across disciplines. Please refer to the project website for the most up-to-date information: http://simworld.org/.

---

## 论文详细总结（自动生成）

## 论文总结：SimWorld——面向物理和社会世界的开放式智能体模拟器

### 1. 核心问题与整体含义（研究动机和背景）

- **背景**：当前LLM/VLM智能体在数学、编程和网页使用等领域取得了快速进展，但在复杂的物理和社会环境中（如城市导航、社会经济活动）的应用仍然充满挑战。构建能在真实世界中生存和繁衍的智能体（例如自主赚取收入）需要在多样化的场景中进行大规模交互、推理、训练和评估。
- **问题**：现有的世界模拟器存在明显不足：
  - 依赖有限的手工场景，缺乏开放性与多样性；
  - 物理和社会规则过于简化（如Minecraft的方块世界，缺乏真实重力、动量等）；
  - 对LLM/VLM智能体缺乏原生支持（如没有自然语言接口、多模态输入/反馈）。
- **本文贡献**：提出SimWorld——基于Unreal Engine 5构建的下一代模拟器，旨在为LLM/VLM智能体提供逼真、开放、可扩展的物理和社会世界，支持智能体的开发、训练和评估。

### 2. 方法论：核心思想、关键技术细节

- **核心架构**：SimWorld采用双层架构：
  - **Unreal Engine 5后端**：提供高保真3D渲染、实时物理模拟（重力、惯性、摩擦等）、动态照明和天气、行人流等。
  - **Python层**：桥接高层功能，包括程序化场景生成、LLM可控编辑、丰富的智能体输入/输出接口，以及模块化的任务构造器。
- **关键技术**：
  - **开放世界生成**：
    - **程序化生成**：基于四叉树结构自动生成城市道路网络、建筑物布局、街道家具等，支持参数化调整（规模、密度、车辆/行人数量），实现近乎无限的场景多样性。
    - **语言驱动的场景编辑**：通过自然语言命令（如“在医院旁添加一棵树”）实时修改环境。系统利用检索增强的LLM解析命令，从场景图中定位目标位置，从资产库中检索或调用文本转3D生成模型（如Hunyuan3D）合成新物体并插入。
  - **真实物理与社交模拟**：
    - **物理模拟**：利用UE-5的PhysX引擎，实现重力、质量、惯性等真实物理效果（如上下坡、碰撞后失去平衡）。
    - **社交模拟**：集成动态交通系统（车辆、行人），遵守交通信号、斑马线、个人空间等社会规范。
  - **丰富的LLM/VLM智能体接口**：
    - **输入**：多模态感知信息——RGB图像、深度图、语义分割图、结构化场景图，以及行动反馈（如碰撞事件）。
    - **输出**：开放词汇的高层自然语言动作（如“去最近的椅子并坐下”），由内置的本地动作规划器解析为低层可执行动作序列（包含规则型或视觉型执行器）。这允许智能体专注于高层推理，而将低层物理控制交由模拟器处理。
  - **多样化的推理场景**：提供可定制的任务定义、角色、奖励和评估指标，支持构建物理和社会推理案例。

### 3. 实验设计：数据集、基准方法与对比方法

- **案例1：物理导航任务（Case Study 1）**
  - **场景**：在两个程序生成的城市中，智能体需从起点导航到目标点，同时避开静态障碍物（树、长椅）和动态障碍物（行人），并遵守交通规则（红灯停）。
  - **设置**：
    - 使用**本地动作规划器**（基于A*的预处理路径）时，智能体按路径逐点导航并自主避障；**无规划器**时，智能体需自主规划轨迹。
    - 难度分级：Easy（单直线段）、Medium（单个转弯）、Hard（多段多转弯）、Dynamic（直线上有动态行人）。
    - 动作空间：Do Nothing、Step（前进/后退）、Turn、Change View（调整视角）、Change Next Waypoint（仅规划器模式）。
  - **对比方法**：
    - **规则型基线**：严格跟随规划器路径，无视障碍和信号。
    - **VLM智能体**：GPT-4o-mini、GPT-4o、Claude-3.7-Sonnet、Gemini-2.5-Pro（分别对应不同版本）。
  - **评估指标**：成功率(SR)、碰撞次数(CC/CCS)、红灯违规率(RVR)、卡住率(STR)、归一化决策次数(NDC)等。

- **案例2：多智能体配送任务（Case Study 2）**
  - **场景**：在一个城市尺度环境中，多个LLM智能体作为配送员，通过竞标订单、配送、投资（买自行车）、合作（共享订单）等行为，最大化最终利润。
  - **环境系统**：能量系统（体能管理）、经济系统（货币收支）、订单共享机制、竞争与合作。
  - **动作空间**：Bid Order、Pick Up、Deliver、Share/Cancel Share、Go to Meet-point、Purchase Scooter/Beverage、Adjust Speed等。
  - **对比方法**：Claude-3.5-Sonnet、DeepSeek-V3、GPT-4o、Gemini-2.5-Flash、Gemini-2.0-Flash、Qwen3-32B、DeepSeek-Prover-V2、QwQ、GPT-4o-mini等。使用ReAct框架。
  - **评估指标**：总利润、成功订单数、能量效率、共享次数、投资次数等。
  - **消融实验**：
    - **模型竞争**：12个模型各控制2个智能体，在高度竞争环境下运行1000步，分析出价策略和胜负矩阵。
    - **环境配置**：改变全局订单总量和智能体初始资金，观察行为变化。
    - **人格影响**：为大五人格特质（开放性、尽责性、外倾性、宜人性、神经质）不同的智能体设置提示，分析行为差异。

### 4. 资源与算力

- 论文中未明确报告使用了多少GPU型号、数量和训练时长。由于主要任务是对现成的LLM/VLM进行API调用评估，而非模型训练，因此计算资源依赖于第三方API服务。附录提及每次API请求平均约7000 tokens，实验运行时间因模型和场景而异，但未给出具体硬件规格或总计时长。

### 5. 实验数量与充分性

- **实验数量**：
  - 导航任务：静态障碍物下设3个难度×4个模型（每种约10个任务）+ 动态障碍物（10个任务）；无规划器（Medium难度×3个模型）。
  - 配送任务：主实验每个模型运行3轮，每轮5000步；模型竞争实验运行3个随机种子（1000步）；环境配置实验（2个因素各若干级别）；人格实验（5个特质，每个特质2个智能体）。
- **充分性与公平性**：
  - 实验覆盖了多个主流LLM家族，体现了模型间的差异；设置了不同难度和动态条件，具有一定的全面性。
  - 导航任务中的红灯违规率计算仅基于成功任务，避免了成功/失败不对等的影响。
  - 配送任务中多次运行取均值和标准差，体现了统计稳定性；消融实验探究了环境、人格、竞争等维度。
  - **但仍存在一些局限**：导航任务的任务数量相对有限（每个难度10个任务），可能不足以完全统计；配送任务的随机性（订单生成、对手行为）可能导致较大方差，但通过多轮平均部分缓解；所有实验均在程序生成的同一地图上进行，未测试跨场景泛化性。

### 6. 主要结论与发现

- **导航任务**：
  - GPT-4o和Claude-3.7-Sonnet表现出较高的成功率和规划效率，但经常忽视红灯（红绿违规率高），且未能主动调整视角去感知交通信号，暴露出VLM在主动注意方面的局限。
  - Gemini-2.5-Pro对障碍物更敏感（碰撞更少），但更容易卡住，任务成功率较低。
  - 无规划器时，Gemini-2.5-Pro的自主导航能力最强，而GPT-4o完全失败。
- **配送任务**：
  - DeepSeek-V3和Claude-3.5-Sonnet获得最高平均利润，但波动大（Std约20）。
  - Gemini-2.5-Flash利润中等但最为稳定；GPT-4o-mini完全失效。
  - 出价策略方面，Claude-3.7-Sonnet和Gemini系列出价范围广（灵活），而LLaMA系列出价窄，竞争力弱。
  - 环境资源稀缺时，智能体更积极竞争；初始资金充足时更倾向于投资和休闲行为。
  - 人格显著影响行为：尽责性高的智能体更注重任务完成（少出价、多提货）；宜人性高的智能体更少无所事事；开放性高的智能体探索性强但易亏损。
- **总体**：当前前沿LLM作为智能体在感知-动作闭环中仍存在明显短板，如空间推理不足、难以遵守抽象规则、行为一致性差等。SimWorld提供了一个能揭示这些差异的可靠测试平台。

### 7. 优点

- **真实感与开放世界**：基于UE5的逼真渲染和物理模拟远超游戏化平台；程序化生成+语言编辑支持近乎无限的自定义场景。
- **原生LLM/VLM支持**：多模态输入和开放词汇的高层动作接口降低了智能体部署的门槛；本地动作规划器隔离了低层控制，使LLM专注于高层推理。
- **双维案例**：同时覆盖物理推理（导航）和社会推理（多智能体经济），展示了平台的综合性。
- **开源与可扩展性**：代码开源，模块化设计便于社区贡献新场景、新任务、新智能体。
- **丰富的评估指标**：不仅关注任务成功率，还引入安全（碰撞、红绿灯）、效率（决策次数）、经济（利润、投资）等多维度指标，支持细粒度分析。
- **消融实验深入**：探讨了环境资源、初始资金、人格特质等对行为的影响，加深了对智能体决策的理解。

### 8. 不足与局限

- **大规模训练效率有待优化**：论文指出SimWorld在支持在线强化学习等大规模训练时的效率仍有提升空间（尽管支持禁用渲染加速）。
- **导航任务场景有限**：仅在城市人行道场景中测试，未涉及室内、自然地形或其他复杂环境；静态障碍物和动态行人模式相对固定。
- **任务数量有限**：导航任务每个难度仅10个任务，统计显著性可能不足；配送任务中每轮5000步，但仅进行了3轮，随机性可能影响结论稳健性。
- **人格影响实验的因果性**：人格通过提示词注入，智能体行为与人格的相关性可能部分源自提示中的描述性语言，而非内在特质模拟。
- **缺少跨模型公平性控制**：不同模型API版本、延迟、成本各异，可能影响决策质量和实验进度（如GPT-4o-mini完全失效可能是因为能力不足或提示理解偏差）。
- **资源与算力不透明**：未报告API调用总次数、token消耗或计算费用，不利于复现和成本评估。
- **社会模拟的广度**：配送任务中的社会交互（共享订单、竞争）仍较为简单，未涉及议价、欺骗、声誉等深层社会机制。

SimWorld是一个强大的智能体评估平台，但其在训练效率和场景广度上仍有改进空间。未来的工作可以集成更自然的多智能体协商机制、更丰富的环境具身交互（如驾驶、操作物体），并优化大规模并行模拟的能力。

（完）
