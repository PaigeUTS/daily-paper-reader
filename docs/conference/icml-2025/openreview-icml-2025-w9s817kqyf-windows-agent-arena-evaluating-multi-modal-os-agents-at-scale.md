---
title: "Windows Agent Arena: Evaluating Multi-Modal OS Agents at Scale"
title_zh: Windows智能体竞技场：大规模评估多模态操作系统智能体
authors: "Rogerio Bonatti, Dan Zhao, Francesco Bonacci, Dillon Dupont, Sara Abdali, Yinheng Li, Yadong Lu, Justin Wagle, Kazuhito Koishida, Arthur Bucker, Lawrence Keunho Jang, Zheng Hui"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=W9s817KqYf"
tags: ["query:agents-os"]
score: 7.0
evidence: 在Windows上大规模评估操作系统智能体，与服务智能体操作系统相关
tldr: Windows Agent Arena构建了一个大规模评估环境，允许AI智能体在真实Windows操作系统中自由操作，使用与人类相同的应用程序和工具。该平台支持多模态任务，解决了现有基准在领域广泛性和评估速度上的局限，推动了操作系统智能体的发展。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1295, \"height\": 337, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 715, \"height\": 939, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1754, \"height\": 980, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 629, \"height\": 882, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1649, \"height\": 357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 862, \"height\": 486, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 801, \"height\": 354, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1429, \"height\": 915, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1431, \"height\": 907, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1427, \"height\": 913, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1418, \"height\": 909, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1584, \"height\": 1033, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1075, \"height\": 798, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1076, \"height\": 974, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 897, \"height\": 1228, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1794, \"height\": 687, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 763, \"height\": 471, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 761, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 762, \"height\": 471, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 765, \"height\": 470, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 555, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 557, \"height\": 343, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 556, \"height\": 343, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 555, \"height\": 344, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 560, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 564, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 581, \"height\": 336, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 578, \"height\": 338, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 576, \"height\": 356, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 583, \"height\": 357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-031.webp\", \"caption\": \"\", \"page\": 0, \"index\": 31, \"width\": 557, \"height\": 338, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-032.webp\", \"caption\": \"\", \"page\": 0, \"index\": 32, \"width\": 559, \"height\": 361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-033.webp\", \"caption\": \"\", \"page\": 0, \"index\": 33, \"width\": 1731, \"height\": 1018, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-w9s817kqyf/fig-034.webp\", \"caption\": \"\", \"page\": 0, \"index\": 34, \"width\": 578, \"height\": 354, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-w9s817kqyf/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1374, \"height\": 552, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-w9s817kqyf/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 749, \"height\": 647, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-w9s817kqyf/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 721, \"height\": 651, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-w9s817kqyf/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1708, \"height\": 1178, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-w9s817kqyf/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1275, \"height\": 1474, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-w9s817kqyf/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1441, \"height\": 853, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-w9s817kqyf/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1428, \"height\": 1032, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-w9s817kqyf/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1430, \"height\": 1346, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-w9s817kqyf/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1428, \"height\": 796, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-w9s817kqyf/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1423, \"height\": 1041, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-w9s817kqyf/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1419, \"height\": 462, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-w9s817kqyf/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1433, \"height\": 1475, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-w9s817kqyf/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 804, \"height\": 208, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-w9s817kqyf/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1090, \"height\": 757, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-w9s817kqyf/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1444, \"height\": 206, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-w9s817kqyf/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1537, \"height\": 236, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-w9s817kqyf/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 801, \"height\": 342, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-w9s817kqyf/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1797, \"height\": 609, \"label\": \"Table\"}]"
motivation: 现有基准领域有限且评估耗时长。
method: 构建Windows Agent Arena环境，支持智能体在真实OS中自由操作。
result: 提供可扩展的评估平台，加速OS智能体研究。
conclusion: 该系统有助于推动操作系统智能体的实际部署。
---

## Abstract
Large language models (LLMs) show potential as computer agents, enhancing productivity and software accessibility in multi-modal tasks. 
However, measuring agent performance in sufficiently realistic and complex environments becomes increasingly challenging as: 
(i) most benchmarks are limited to specific modalities/domains (e.g., text-only, web navigation, Q&A) and 
(ii) full benchmark evaluations are slow (on order of magnitude of multiple hours/days) given the multi-step sequential nature of tasks.
To address these challenges, we introduce Windows Agent Arena: a general environment focusing exclusively on the Windows operating system (OS) where agents can operate freely within a real OS to use the same applications and tools available to human users when performing tasks.
We create 150+ diverse tasks across representative domains that require agentic abilities in planning, screen understanding, and tool usage.
Our benchmark is scalable and can be seamlessly parallelized for a full benchmark evaluation in as little as $20$ minutes.
Our work not only speeds up the development and evaluation cycle of multi-modal agents, but also highlights and analyzes existing shortfalls in the agentic  abilities of several multimodal LLMs as agents within the Windows computing environment---with the best achieving only a 19.5\% success rate compared to a human success rate of 74.5\%.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- 现有计算机智能体基准存在两个主要局限：一是大多局限于特定模态或领域（如文本、网页导航、问答），缺乏对多模态、跨应用真实操作系统的覆盖；二是评估效率低下，由于任务的顺序多步特性，全基准评估通常需要数小时甚至数天。
- 尽管Windows操作系统占据桌面市场约73%的份额，但其闭源性质导致针对Windows的智能体研究进展缓慢。
- 为解决上述问题，作者提出了 **Windows Agent Arena**：一个专注于Windows OS的通用、可扩展基准环境，允许智能体在真实操作系统中自由操作，使用与人类相同的应用程序和工具，并支持大规模并行化评估，将全基准完成时间缩短至约20分钟。

## 2. 论文提出的方法论

### 核心思想
- 构建一个**真实Windows 11虚拟机环境**，智能体通过Docker容器内的客户端与虚拟机交互，能够执行鼠标、键盘、剪贴板、窗口切换等操作。
- 任务被形式化为**部分可观察马尔可夫决策过程（POMDP）**：智能体根据当前观察（屏幕截图、窗口标题、剪贴板内容、无障碍树等）生成动作，获得奖励（基于任务完成度）。

### 关键技术细节
- **观察空间**：包括任务指令、当前窗口标题、所有打开窗口列表、剪贴板内容、屏幕截图（原始图、带Set-of-Marks的标注图）以及**UIA无障碍树**。
- **动作空间**：提供两种方式——**自由格式的pyautogui/Python代码**，以及**预定义的Computer类**（包含鼠标移动/点击、键盘输入、剪贴板操作、程序启动、窗口切换等函数）。
- **视觉解析方法**：支持多种Set-of-Marks生成方式：
  - UIA树解析（提取Windows原生UI元素）
  - DOM树解析（浏览器中）
  - OCR（Tesseract或专有模型）
  - 图标/图像检测（Grounding DINO）
  - **OmniParser**（统一的多元素检测+图标描述）
- **智能体工作流**：基于**ReAct/链式思维提示**，要求智能体先输出屏幕理解、规划、动作选择，再生成单步代码。每一步只执行一个动作，并等待屏幕更新。
- **并行化基础设施**：通过Azure虚拟机集群，将任务分发至多个独立Worker（每个Worker运行一个Docker容器+Windows VM），实现高效并行评估。使用Azure Blob Store管理镜像和日志，确保安全隔离。

### 公式或算法流程（文字说明）
- 状态转移：\( s_{t+1} = T(s_t, a_t) \) 由真实VM执行动作实现。
- 奖励函数 \( R(s,a) \)：仅在最终步骤返回非零值（任务完成则返回1或连续值，否则0；对于不可行任务，正确识别失败也视为成功）。
- 智能体循环：初始状态 → 观察 \(o_t\) → 生成动作 \(a_t\) → 执行并更新状态 → 重复直到终止（DONE/FAIL或超步数限制）。

## 3. 实验设计

- **基准/场景**：**Windows Agent Arena** 包含 **154个任务**，覆盖6大领域：
  - Office（LibreOffice Calc/Writer）：文档编辑、表格计算、排版等（43个）
  - Web Browsing（Edge/Chrome）：网上购物、隐私设置、书签等（30个）
  - Windows System（文件资源管理器、设置）：文件管理、系统配置（24个）
  - Coding（VSCode）：代码编辑、扩展安装、配置修改（24个）
  - Media & Video（VLC）：播放控制、截图、格式转换（21个）
  - Windows Utilities（记事本、时钟、画图）：基础工具使用（12个）
- **对比方法**：测试了多种**多模态LLM作为智能体骨干**：
  - 闭源：GPT-4V-1106、GPT-4o、GPT-4o-mini、o1（仅文本+OmniParser）
  - 开源：Phi-3-V、Phi-3.5-V
- **输入解析方法消融**：
  - 原始截图（无SoM）
  - 不同像素检测器（Pytesseract+DOM+Grounding DINO、OneOCR+专有模型、OmniParser）
  - 是否使用UIA树辅助
- **人类基线**：一名Windows用户完成所有任务，成功率为**74.5%**。
- **额外实验**：Reflexion式提示（表10）；仅原始截图+UIA树（无SoM，表9）。

## 4. 资源与算力

- **未明确说明GPU算力**：仅提到使用Azure **Standard D8 v3** CPU虚拟机（8核、32GB RAM），推理OmniParser等模型时在CPU上运行，未提及GPU型号、数量或训练时长。
- **并行化规模**：约**50个Worker**同时运行，每个Worker一个独立VM。全基准评估时间（有SoM）中位数约**20~45分钟**，o1模型因推理慢需**4~5小时**。
- **成本**：D8 v3 VM每小时$0.384，总成本较低。强调无需高性能GPU资源。

## 5. 实验数量与充分性

- **实验数量充足**：表4列出了**超过20种配置组合**（5种骨干模型 × 4种输入解析方法 × 2种UIA使用与否），表9和表10补充了额外消融。
- **对比公平性**：各配置在同一套154个任务上运行，使用相同的评估脚本。但不同模型的API版本（如GPT-4V已弃用）和随机性可能影响可复现性。
- **充分性**：涵盖了主流VLM、多种视觉解析策略、有无结构信息，且包含人类基线。但未测试模型微调或强化学习方法，也缺少多任务或长期记忆场景。
- **客观性**：评估基于任务结束时的系统状态，由确定性脚本判定，避免主观偏见。人类评估仅单参与者，可能有个体差异。

## 6. 论文的主要结论与发现

- **当前最佳智能体仍有巨大差距**：最好配置（UIA+OmniParser+GPT-4V-1106）成功率仅**19.5%**，远低于人类**74.5%**。
- **精确Set-of-Marks至关重要**：使用UIA树后性能提升57%（OmniParser提升52%），元素定位失误是常见失败原因。
- **视觉-语言错配是主要瓶颈**：智能体常正确描述动作但误选视觉ID（如想选红色却选黄色）。
- **文本推理模型o1表现优异**：尽管只依赖OmniParser的文本描述，o1成功率16.3%，超过多数多模态模型，但推理时间极长。
- **小模型能力不足**：Phi-3/3.5-V成功率极低（<5%），容易产生幻觉。
- **并行化显著加速**：全基准评估从数十小时缩短至约20分钟，降低了研究门槛。

## 7. 优点

- **填补空白**：首个专注于Windows OS的大规模、可并行基准，开源基础设施促进复现与扩展。
- **任务多样性**：154个真实应用场景任务，覆盖办公、网页、系统、编程、媒体、工具。
- **快速评估**：20分钟完成全基准，便于快速迭代。
- **深入消融**：系统比较了多种VLM骨干、视觉解析方法（包括OmniParser）、结构信息（UIA树）的影响，揭示了关键因素。
- **关注视觉-语言对齐问题**：详细分析了失败案例（如误选ID、元素检测重叠），为改进提供方向。
- **安全性与可扩展性**：使用隔离VM和Azure并行化，支持按需扩展。

## 8. 不足与局限

- **任务数量有限**：154个任务可能不足以覆盖所有Windows应用场景，且部分领域（如安全、网络故障排查）缺失。
- **版本过时风险**：GPT-4V已弃用，部分结果可能不适用于最新模型。
- **评估粒度粗**：仅基于最终状态（二进制或连续分），缺乏对中间步骤的奖励（部分完成未考虑）。
- **o1推理时间过长**：不适合实际部署，应用价值受限。
- **人类基线单一**：仅一名用户，可能存在偏差，且未报告用户经验水平。
- **未探索训练/微调**：仅零样本评估，未测试模型在Windows数据上的微调。
- **未考虑多任务并发或持续学习**：只能逐个执行任务。
- **安全与隐私风险提及不足**：虽有关注，但未深入测试对抗性提示注入或数据泄露。
- **不同模型版本不一致**：闭源模型API版本更迭可能导致不可复现。

（完）
