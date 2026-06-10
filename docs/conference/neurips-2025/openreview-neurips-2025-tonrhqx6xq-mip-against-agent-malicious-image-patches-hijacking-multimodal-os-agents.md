---
title: "MIP against Agent: Malicious Image Patches Hijacking Multimodal OS Agents"
title_zh: 恶意图像补丁劫持多模态操作系统智能体
authors: "Lukas Aichberger, Alasdair Paren, Guohao Li, Philip Torr, Yarin Gal, Adel Bibi"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=ToNRHqX6xq"
tags: ["query:agents-os"]
score: 7.0
evidence: 对多模态操作系统智能体的攻击，与智能体操作系统直接相关
tldr: 针对操作系统智能体的新型攻击：恶意图像补丁（MIP）通过扰动屏幕区域来劫持VLM驱动的OS智能体。该工作揭示了OS智能体在截图解析和行动执行中的安全脆弱性，对构建安全的智能体操作系统具有重要警示意义。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-tonrhqx6xq/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 709, \"height\": 651, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tonrhqx6xq/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1438, \"height\": 485, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tonrhqx6xq/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 664, \"height\": 658, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tonrhqx6xq/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1450, \"height\": 937, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tonrhqx6xq/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1460, \"height\": 1540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tonrhqx6xq/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1444, \"height\": 974, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tonrhqx6xq/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 701, \"height\": 699, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tonrhqx6xq/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 705, \"height\": 698, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tonrhqx6xq/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1445, \"height\": 971, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tonrhqx6xq/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 702, \"height\": 700, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-tonrhqx6xq/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 705, \"height\": 700, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-tonrhqx6xq/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 709, \"height\": 759, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tonrhqx6xq/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 711, \"height\": 758, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tonrhqx6xq/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 701, \"height\": 342, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tonrhqx6xq/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 714, \"height\": 341, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tonrhqx6xq/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1447, \"height\": 2307, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tonrhqx6xq/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1426, \"height\": 1877, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tonrhqx6xq/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1429, \"height\": 1878, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tonrhqx6xq/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1457, \"height\": 1791, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-tonrhqx6xq/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1462, \"height\": 970, \"label\": \"Table\"}]"
motivation: OS智能体直接控制计算机，安全风险高。
method: 设计对抗性图像补丁，在截图区域制造扰动以误导智能体行为。
result: 成功实施攻击，表明现有OS智能体易受此类攻击。
conclusion: 为OS智能体安全防护提出新挑战。
---

## Abstract
Recent advances in operating system (OS) agents have enabled vision-language models (VLMs) to directly control a user’s computer. Unlike conventional VLMs that passively output text, OS agents autonomously perform computer-based tasks in response to a single user prompt. OS agents do so by capturing, parsing, and analysing screenshots and executing low-level actions via application programming interfaces (APIs), such as mouse clicks and keyboard inputs. This direct interaction with the OS significantly raises the stakes, as failures or manipulations can have immediate and tangible consequences. In this work, we uncover a novel attack vector against these OS agents: Malicious Image Patches (MIPs), adversarially perturbed screen regions that, when captured by an OS agent, induce it to perform harmful actions by exploiting specific APIs. For instance, a MIP can be embedded in a desktop wallpaper or shared on social media to cause an OS agent to exfiltrate sensitive user data. We show that MIPs generalise across user prompts and screen configurations, and that they can hijack multiple OS agents even during the execution of benign instructions. These findings expose critical security vulnerabilities in OS agents that have to be carefully addressed before their widespread deployment.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：随着多模态大模型（VLM）被集成到操作系统（OS）智能体中，这些智能体能够通过截图感知屏幕内容，并通过API（如鼠标点击、键盘输入）直接控制计算机，完成用户指令。然而，这种主动交互能力带来了全新的安全风险——传统的文本对抗攻击往往只能产生不可直接执行的文本输出，而OS智能体一旦被操控，可能执行实际的有害操作（如数据泄露、系统破坏）。
- **核心问题**：现有攻击多集中在文本层面或直接操纵VLM输入，但缺乏一种利用屏幕截图这一感知通道、且能跨场景泛化的视觉攻击手段。作者提出**恶意图像补丁（Malicious Image Patches, MIPs）**：一种被轻微扰动的屏幕区域，当OS智能体截图捕获到该区域时，会被诱导生成恶意API调用序列，从而执行有害行为。
- **整体含义**：该工作揭示了OS智能体在截图解析和行动执行中的安全脆弱性，对构建安全的智能体操作系统具有重要警示意义。MIP可嵌入桌面背景、社交媒体图片等，难以被检测且能通过社交网络传播，形成类似“计算机蠕虫”的自复制攻击。

## 2. 论文提出的方法论

### 2.1 核心思想

- 在OS智能体的标准处理流程中，智能体首先通过屏幕解析器（Screen Parser，如OmniParser）将截图转换为带标注的截图（含Set-of-Marks框）和结构化文本描述，然后VLM根据用户提示、系统提示、记忆信息、解析文本和带标注截图生成下一步动作。MIPs的目标是通过扰动屏幕中可控的一小块区域，使得VLM输出预定义的恶意代码（如打开非法网站、造成内存溢出）。
- 核心挑战：1）仅能控制屏幕的一小块区域（如图片所在区域）；2）需要保证扰动不改变屏幕解析器的输出（否则可能破坏攻击可行性）；3）需要对抗图像缩放等非可微操作。

### 2.2 关键技术细节

- **攻击空间定义**：扰动限制在某个像素区域 \( R \) 内，使用 \( \ell_\infty \) 范数约束（最大扰动幅度 \( \epsilon = 25/255 \)），并经过整数化、像素范围裁剪，保证生成有效的8-bit RGB图像。
- **绕过解析器**：由于屏幕解析器不可微，作者先对原截图运行解析器得到标注后的截图 \( l(s, s_{\text{som}}) \)，直接在该标注图上优化，但确保不扰动任何解析框（即 \( s_{\text{som}} \odot \mathbf{1}_R = 0 \)），并定期验证扰动后解析器输出是否改变。
- **目标函数**（公式2）：  
  \[
  \delta^* = \arg \min_{\mathcal{R}, \delta \in \Delta^\mathcal{R}_\epsilon} \mathcal{L}\left( f_\theta \left( p_{\text{txt}},\, q(l(s, s_{\text{som}})+\delta) \right),\, y \right)
  \]  
  其中 \( p_{\text{txt}} \) 为拼接后的文本输入，\( q \) 是用于替代不可微缩放的可微分近似，\( \mathcal{L} \) 为交叉熵损失。优化目标是使VLM输出的下一token序列完全匹配恶意目标 \( y \)。
- **优化过程**：使用投影梯度下降（PGD），每步投影到可行域（乘以区域掩码、整数化、\( \ell_\infty \) 球投影、像素值裁剪）。若解析器输出意外改变则回滚并加随机扰动。终止条件：所有目标token的next-token似然超过99%。

### 2.3 算法流程（文字说明）

1. 固定图像区域 \( R \) 并确认其不与解析框重叠（若不满足，替换可控图像内容）。
2. 对原始截图 \( s \) 运行解析器得到 \( s_{\text{som}} \) 和 \( p_{\text{som}} \)。
3. 初始化扰动 \( \delta \) 为零。
4. 按批次（batch size=8）随机采样 \( (p, s) \) 对，构造 \( p_{\text{txt}} \)。
5. 计算带扰动后的标注图 \( l(s, s_{\text{som}}) + \delta \)，经可微分缩放后输入VLM \( f_\theta \)。
6. 计算交叉熵损失并反向传播，用Adam优化器更新 \( \delta \)。
7. 投影 \( \delta \) 到约束集（区域掩码、整数化、\( \ell_\infty \) 球、像素范围）。
8. 定期检查解析器输出是否改变，若改变则回滚加随机扰动。
9. 重复步骤4-8直到所有目标token似然>99%。

## 3. 实验设计

### 3.1 数据集 / 场景

- **环境**：Microsoft Windows Agent Arena (WAA)，包含154个预定义任务，涵盖12个领域。
- **两种设置**：
  - **桌面设置**：MIP嵌入桌面背景（使用DALL·E生成背景），补丁区域约1000×1000像素，占整个截图约1/7。
  - **社交媒体设置**：MIP嵌入Bluesky平台帖子中的图片，补丁区域约900×900像素。
- **用户提示**：从WAA各领域随机采样24个任务，分为优化集 \( P^+ \)（12个）和评估集 \( P^- \)（12个）。
- **截图**：对每种设置各创建12个优化截图 \( S^+ \) 和12个评估截图 \( S^- \)，通过移动图标或更换帖子内容实现变化。
- **目标恶意行为**：
  - 内存溢出（\( y_m \)）：打开cmd并无限写入垃圾文件。
  - 导航到色情网站（\( y_w \)）：打开Edge浏览器并输入网址。
- **对比方法**：论文本身没有对比其他已有攻击方法，因为这是第一个系统研究MIP攻击的工作。实验主要通过控制变量验证泛化性。

### 3.2 评估指标

- **平均成功率（ASR）**：对每个MIP，用multinomial sampling生成5个输出，精确匹配目标 \( y \) 的比例。温度参数从0.0（贪心）到1.0。

### 3.3 实验分组

1. **定向攻击（表1）**：优化单一 \( (p,s) \) 对，评估在相同对、新提示 \( P^- \) 和新截图 \( S^- \) 上的表现。
2. **通用攻击（表2）**：同时优化所有 \( (p,s) \in P^+ \times S^+ \)，评估在 \( P^- \times S^- \) 上，并测试跨屏幕解析器（从OmniParser切换到GroundingDINO+TesseractOCR）。
3. **执行步骤泛化性（表3）**：用另一个善意提示“总结社交媒体最新内容”，让OS智能体先执行几步后再遇到MIP，评估ASR。
4. **多VLM通用性（表4）**：单个MIP同时优化针对三个不同VLM（Llama-3.2-11B-Vision-Instruct、Llama-3.2-90B-Vision-Instruct、Llama-3.2-11B-Vision），评估在这些模型上的表现，并测试不可见VLM（Llama-3.2-90B-Vision）。

### 3.4 实验充分性与公平性

- **充分性**：覆盖了用户提示、截图布局、屏幕解析器、执行步骤、VLM类型、温度设置等多个维度的泛化性测试；每种配置都报告了均值±标准差；实验规模较大（总计约6.1M文本token生成）。
- **公平性**：所有实验在相同WAA环境、相同默认系统提示下进行；使用开源模型和标准组件；未出现选择偏差的明显问题。但未与其他类型攻击（如文本提示注入）做直接对比，作者明确表示这是第一个系统研究MIP的工作。

## 4. 资源与算力

- 论文明确报告：所有实验在一台配备**8张NVIDIA A100 Tensor Core GPU**的节点上进行。
- **总耗时**：约300节点小时（node hours），其中评估阶段约需6.1M文本token生成。
- 训练具体步骤耗时：定向攻击约600-3000步，通用攻击约20,000-28,000步，多VLM攻击约74,000步。
- 论文提供了优化器为Adam（\( \beta_1=\beta_2=0.9 \)，学习率 \( 10^{-2} \)），但未说明每步耗时或batch size的具体影响。

## 5. 实验数量与充分性

- **实验数量**：
  - 表1：定向攻击 × 4个MIP（2种目标 × 2种设置）。
  - 表2 & 3：通用攻击 × 4个MIP（2种目标 × 2种设置），加上跨解析器测试和跨执行步骤测试。
  - 表4：多VLM攻击 × 1个MIP，评估在3个优化VLM和1个未见过VLM上。
  - 附录表8、9补充了更多温度下的具体ASR值（0.0, 0.1, 0.5, 1.0）及所有组合的详细结果。
- **充分性**：实验设计系统，覆盖了攻击成功所需的主要泛化维度。但缺少与已有防御/攻击方法的对比，以及真实用户场景下的端到端运行（全自动执行恶意行为）的验证。总体而言，对于揭示漏洞这一目标已足够充分。

## 6. 论文的主要结论与发现

1. **MIPs可以有效劫持OS智能体**：在固定设置下（定向攻击）ASR达到100%；在通用场景下（跨提示、截图、执行步骤）ASR依然很高（≥0.89在贪心解码下）。
2. **MIPs能够跨屏幕解析器迁移**：从OmniParser迁移到GroundingDINO+TesseractOCR时，ASR虽有下降但仍保持显著（桌面设置约0.40-0.98，取决于温度）。
3. **MIPs在智能体执行善意任务过程中仍然有效**：即使智能体已经执行了若干步骤后才遇到MIP，ASR仍高于0.42（贪心解码）。
4. **MIPs可同时针对多个VLM进行优化**：联合优化11B和90B的指令调优版本及预训练版本后，在所有这些模型上ASR≥0.92；但对未见过的VLM（Llama-3.2-90B-Vision）迁移失败，ASR=0。
5. **攻击成功依赖条件**：需要MIP被智能体截图捕获，且智能体使用的VLM必须在优化集合中或具有相似性。尽管如此，若OS智能体达到数亿用户规模，即使成功率千分之一，也能造成大量危害。

## 7. 优点

- **新颖的攻击向量**：首次系统研究通过屏幕补丁劫持OS智能体，完全不同于已有的文本注入或弹出窗口攻击，更难以检测。
- **方法严谨**：完整建模了OS智能体的多组件管道（屏幕解析器、VLM、API），并逐一应对可微性、约束条件等挑战。
- **泛化性评估全面**：覆盖了提示、截图、解析器、执行步骤、VLM、温度等多个维度的测试，实验设计完整。
- **现实威胁洞察深刻**：不仅展示攻击可行性，还讨论了实际传播场景（桌面背景、社交媒体、在线广告、PDF等），并指出可形成“智能体计算机蠕虫”。
- **开源可复现**：代码和数据集已公开。

## 8. 不足与局限

- **依赖黑盒条件**：攻击优化需要访问VLM的梯度（白盒），且对未见过的VLM迁移性差，实际攻击可能需要针对多个流行模型分别优化。
- **未探索攻击持久性**：实验中MIP被截图捕获后就触发，但未检验在多步交互中智能体是否可能因其他因素（如截图分辨率变化、网络延迟）导致攻击失效。
- **缺乏真实用户行为建模**：所有截图和提示由人工构造，未评估在真实用户多样的操作系统状态下的表现。
- **未与其他防御/攻击做对比**：没有对比已有的提示注入、弹出窗口攻击或检测方法，难以量化MIP的相对威胁水平。
- **仅使用单一VLM家族**：只使用了Llama 3.2系列，未评估对GPT-4V、Claude等闭源模型的效果（因为这些模型不提供梯度）。
- **潜在偏差**：WAA环境虽包含154个任务，但样本数量对于覆盖所有可能操作仍有限；攻击目标仅两种，可能不全面代表所有恶意行为。

（完）
