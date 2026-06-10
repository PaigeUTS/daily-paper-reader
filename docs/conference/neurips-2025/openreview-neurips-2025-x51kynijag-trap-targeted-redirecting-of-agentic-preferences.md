---
title: "TRAP: Targeted Redirecting of Agentic Preferences"
title_zh: TRAP：目标导向的智能体偏好重定向
authors: "Hangoo Kang, Jehyeok Yeon, Gagandeep Singh"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=X51kYnijag"
tags: ["query:agents-os"]
score: 8.0
evidence: 针对视觉语言智能体的对抗攻击，涉及智能体安全
tldr: 针对智能体系统的安全性问题，本文提出TRAP攻击框架，利用扩散模型在视觉-语言嵌入空间注入语义，操纵智能体决策。该方法结合负提示退化和正语义优化，能够在不显式修改像素的情况下实现隐蔽攻击。实验表明该攻击成功率较高，揭示了多模态智能体面临的新安全威胁，对智能体安全防护具有重要警示意义。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-x51kynijag/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1299, \"height\": 721, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-x51kynijag/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1158, \"height\": 563, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-x51kynijag/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1398, \"height\": 612, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-x51kynijag/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1123, \"height\": 725, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-x51kynijag/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1394, \"height\": 431, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x51kynijag/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1275, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x51kynijag/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1469, \"height\": 307, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x51kynijag/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1379, \"height\": 326, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x51kynijag/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1380, \"height\": 325, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x51kynijag/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1134, \"height\": 379, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x51kynijag/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1133, \"height\": 377, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x51kynijag/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1134, \"height\": 268, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x51kynijag/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1131, \"height\": 291, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x51kynijag/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1132, \"height\": 395, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-x51kynijag/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1273, \"height\": 304, \"label\": \"Table\"}]"
motivation: 现有对抗攻击依赖像素扰动或模型访问，缺乏针对多模态智能体语义层的隐蔽攻击方法。
method: 提出基于扩散模型的生成式对抗框架，通过负提示退化与正语义优化在嵌入层注入攻击。
result: 在多个VLM智能体上实现了高成功率的隐蔽攻击，暴露了跨模态推理的安全漏洞。
conclusion: 该工作凸显了智能体系统在语义层面的安全脆弱性，亟需新的防御机制。
---

## Abstract
Autonomous agentic AI systems powered by vision-language models (VLMs) are rapidly advancing toward real-world deployment, yet their cross-modal reasoning capabilities introduce new attack surfaces for adversarial manipulation that exploit semantic reasoning across modalities. Existing adversarial attacks typically rely on visible pixel perturbations or require privileged model or environment access, making them impractical for stealthy, real-world exploitation. We introduce TRAP, a novel generative adversarial framework that manipulates
the agent’s decision-making using diffusion-based semantic injections into the vision-language embedding space. Our method combines negative prompt–based degradation with positive semantic optimization, guided by a Siamese semantic network and layout-aware spatial masking. Without requiring access to model internals, TRAP produces visually natural images yet induces consistent selection
biases in agentic AI systems. We evaluate TRAP on the Microsoft Common Objects in Context (COCO) dataset, building multi-candidate decision scenarios. Across these scenarios, TRAP consistently induces decision-level preference redirection on leading models, including LLaVA-34B, Gemma3, GPT-4o, and Mistral-3.2, significantly outperforming existing baselines such as SPSA, Bandit, and standard diffusion approaches. These findings expose a critical, generalized vulnerability: autonomous agents can be consistently misled through visually subtle, semantically-guided cross-modal manipulations. Overall, our results show the need for defense strategies beyond pixel-level robustness to address semantic vulnerabilities in cross-modal decision-making. The code for TRAP is accessible on GitHub at https://github.com/uiuc-focal-lab/TRAP.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有的视觉-语言模型（VLM）驱动的自主智能体系统在跨模态推理中存在新的攻击面。传统对抗攻击依赖于明显的像素扰动或需要访问模型内部/环境，无法实现隐蔽的、真实世界的攻击。
- **背景**：自主智能体（如GUI代理）在无人类监督下决策，其信任感知输入的特性使其易受语义操纵。现有研究如提示注入、后门攻击等需要大量访问权限，不切实际。
- **研究动机**：探索一种黑盒、视觉自然、基于语义的对抗攻击方法，能够持续误导多种VLM智能体的决策，从而暴露跨模态决策中的安全漏洞。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：利用扩散模型在CLIP嵌入空间进行语义注入，生成视觉自然但语义偏斜的图像，从而操纵智能体对候选图像的选择偏好。攻击者仅能修改目标图像，无法访问模型参数或梯度（黑盒）。
- **关键技术细节**：
  - **问题形式化**：智能体M基于文本提示p和n个候选图像{x_i}，通过对比余弦相似度选择图像。攻击者将目标图像x_target替换为对抗图像x_adv，使其被选中概率最大化，同时保持x_adv与x_target的感知相似度（LPIPS约束）。
  - **TRAP框架**：
    - 步骤1：提取目标图像的CLIP嵌入和攻击者选择的引导提示ppos的嵌入。
    - 步骤2：使用Siamese语义网络对嵌入进行分解为共同特征和区分特征；通过布局感知掩码（由MLP和DeepLabv3分割生成）约束修改区域。
    - 步骤3：迭代优化对抗嵌入，最小化总损失L_total = λ1 L_sem + λ2 L_dist + λ3 L_LPIPS。L_sem是余弦距离（对齐ppos）；L_dist是区分特征L2距离（保留身份）；L_LPIPS是像素级感知距离。
    - 步骤4：通过Stable Diffusion解码优化后的嵌入生成最终图像x_adv。
  - **算法流程**（文字说明）：初始化嵌入、布局掩码；外层迭代至多20次，内层20次梯度下降优化；每轮解码出候选图像并评估选择概率，若超过多数阈值则停止。

## 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法

- **数据集/场景**：
  - **主要数据集**：Microsoft COCO Captions中的100个图像-字幕对。构建多候选决策场景（n-way选择），其中目标图像初始选择概率低于多数阈值。
  - **额外数据集**：Flickr8k_sketch（素描/抽象图）、ArtCap（艺术风格图）。
  - **现实场景**：电商网页场景（更接近真实应用）。
- **基准方法**：
  - 初始“坏图像”（未经优化的负提示生成图像）
  - SPSA（同时扰动随机逼近）
  - Bandit（基于bandit的查询攻击）
  - 标准Stable Diffusion（直接生成无优化）
  - SSA_CWA（基于嵌入的攻击，Chen et al., 2024）
  - SA_AET（语义对齐攻击，Jia et al., 2025）
- **评估模型**：LLaVA-1.5-34B、Gemma3-8B、Mistral-small-3.1-24B、Mistral-small-3.2-24B、GPT-4o、CogVLM（覆盖开源和闭源、对比和非对比架构）。
- **防御评估**：添加高斯噪声、CIDER过滤、MirrorCheck检测。
- **鲁棒性测试**：系统提示变体、采样温度（0.1和0.7）。

## 4. 资源与算力

- 硬件：4块NVIDIA A100-PCIE-40GB GPU，48核Intel Xeon Silver 4214R CPU。
- 计算时间：TRAP每迭代平均约520秒；SPSA约376秒；Bandit约110秒。总计算量未明确报告，但可推算（20外迭代×20内迭代≈400次梯度步骤）。

## 5. 实验数量与充分性

- **实验数量**：
  - 主实验：6种模型×100个实例，共600个攻击评估。
  - 消融实验：超参数（λ系数增减）、嵌入模型（ViT-B/32, SigLIP, Jina-CLIP）、扩散模型（SD-2.1, SD-XL, SD-1.5）。
  - 额外数据集（Flickr8k_sketch, ArtCap）：4种模型（含GPT-4o）的攻击成功率。
  - 电商场景：4种模型。
  - 防御测试、系统提示变体、温度影响。
- **充分性与公平性**：实验覆盖了多种模型架构、数据集类型和现实场景；对比了多种主流及最先进的基线方法；进行了统计稳定性（R=100随机排序）和鲁棒性测试。但实验仅限于图像选择任务，未涉及更复杂的多步决策。

## 6. 论文的主要结论与发现

- TRAP在所有评估的VLM模型上实现了极高的攻击成功率（ASR），在LLaVA、Gemma3、Mistral上达100%（GPT-4o 63%，CogVLM 94%），远超所有基线（最高SA_AET约85%，但TRAP在多数模型上更高）。
- 攻击具有强可迁移性：从基于CLIP的模型转移到非对比架构（CogVLM）和闭源模型（GPT-4o）。
- 攻击对标准防御（高斯噪声、CIDER、MirrorCheck）和系统提示变化、温度扰动具有鲁棒性。
- 语义层面的操纵比像素级攻击更隐蔽且更有效；现有防御无法有效应对此类攻击。
- 暴露了自主智能体在跨模态决策中的关键安全漏洞，亟需嵌入级语义防御。

## 7. 优点：方法或实验设计上的亮点

- **方法创新性**：首次将扩散模型与Siamese语义分解、布局感知掩码结合，在黑盒设置下实现视觉自然的语义攻击。区别于传统像素扰动。
- **实验全面性**：评估了多种模型（包含GPT-4o）、多种数据集（包括抽象/艺术图）和真实应用场景（电商）。对比基线充分且最新。
- **鲁棒性分析**：对防御、提示变化、温度等因素进行了系统测试，增强了结论可信度。
- **可复现性**：提供了算法伪代码和GitHub代码链接。

## 8. 不足与局限

- **假设依赖**：方法假设智能体依赖对比视觉-语言相似度（如CLIP），对于未来完全非对比架构可能不适用。
- **组件质量依赖**：性能受布局掩码、分割模型、扩散模型质量影响；在边缘案例或资源受限场景下可能下降。
- **计算开销**：TRAP比像素级攻击更昂贵（每样本约520秒），难以用于实时场景；虽可通过蒸馏/缓存缓解，但未验证。
- **场景限制**：仅针对图像选择任务，未扩展到多步智能体行为（如网页导航、对话）。
- **实验覆盖**：仅100个COCO实例，虽统计显著但样本量有限；额外数据集规模未说明。
- **缺乏理论基础**：未提供攻击成功率的理论分析或收敛保证。
- **未评估更复杂防御**：未测试对抗训练（除Robust-LLaVA外）或更高级的输入清洗机制。

（完）
