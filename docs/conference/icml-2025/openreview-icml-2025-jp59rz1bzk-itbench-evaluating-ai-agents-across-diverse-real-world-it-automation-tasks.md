---
title: "ITBench: Evaluating AI Agents across Diverse Real-World IT Automation Tasks"
title_zh: ITBench：跨多样化真实IT自动化任务评估AI智能体
authors: "Saurabh Jha, Rohan R. Arora, Yuji Watanabe, Takumi Yanagawa, Yinfang Chen, Jackson Clark, Bhavya Bhavya, Mudit Verma, Harshit Kumar, Hirokuni Kitahara, Noah Zheutlin, Saki Takano, Divya Pathak, Felix George, Xinbo Wu, Bekir O Turkkan, Gerard Vanloo, Michael Nidd, Ting Dai, Oishik Chatterjee, Pranjal Gupta, Suranjana Samanta, Pooja Aggarwal, Rong Lee, Jae-wook Ahn, Debanjana Kar, Amit Paradkar, Yu Deng, Pratibha Moogi, Prateeti Mohapatra, Naoki Abe, Chandrasekhar Narayanaswami, Tianyin Xu, Lav R. Varshney, Ruchi Mahindru, Anca Sailer, Laura Shwartz, Daby Sow, Nicholas C. M. Fuller, Ruchir Puri"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=jP59rz1bZk"
tags: ["query:agents-os"]
score: 6.0
evidence: 对AI智能体进行IT自动化基准测试，与服务基础设施智能体相关
tldr: ITBench是一个系统化的基准框架，用于评估AI智能体在真实IT自动化任务（如站点可靠性工程、安全合规、财务运营）中的表现。该框架包含102个场景，提供可解释指标，帮助研究者在服务基础设施中部署智能体时理解其能力与局限。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1766, \"height\": 371, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1358, \"height\": 410, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 854, \"height\": 315, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1736, \"height\": 375, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1726, \"height\": 633, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 860, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1781, \"height\": 1040, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1669, \"height\": 1176, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 551, \"height\": 425, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1419, \"height\": 640, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1749, \"height\": 646, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 385, \"height\": 278, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 857, \"height\": 498, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 860, \"height\": 680, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 683, \"height\": 1170, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 679, \"height\": 718, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1745, \"height\": 1896, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 1755, \"height\": 1940, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1755, \"height\": 1914, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1746, \"height\": 1898, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1696, \"height\": 1007, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1535, \"height\": 824, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1706, \"height\": 876, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 1399, \"height\": 686, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 385, \"height\": 280, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 1446, \"height\": 853, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 683, \"height\": 2019, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 687, \"height\": 1765, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 1763, \"height\": 2364, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 684, \"height\": 1200, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-jp59rz1bzk/fig-031.webp\", \"caption\": \"\", \"page\": 0, \"index\": 31, \"width\": 702, \"height\": 394, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1808, \"height\": 445, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1778, \"height\": 962, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 869, \"height\": 676, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1728, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1759, \"height\": 440, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1481, \"height\": 349, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 774, \"height\": 581, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 851, \"height\": 532, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1762, \"height\": 1521, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1753, \"height\": 407, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1769, \"height\": 620, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1705, \"height\": 1013, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1452, \"height\": 713, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 790, \"height\": 212, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1477, \"height\": 669, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 558, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-017.webp\", \"caption\": \"\", \"page\": 0, \"index\": 17, \"width\": 1254, \"height\": 342, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-018.webp\", \"caption\": \"\", \"page\": 0, \"index\": 18, \"width\": 995, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-019.webp\", \"caption\": \"\", \"page\": 0, \"index\": 19, \"width\": 1005, \"height\": 244, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-020.webp\", \"caption\": \"\", \"page\": 0, \"index\": 20, \"width\": 1780, \"height\": 294, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-021.webp\", \"caption\": \"\", \"page\": 0, \"index\": 21, \"width\": 1815, \"height\": 296, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-022.webp\", \"caption\": \"\", \"page\": 0, \"index\": 22, \"width\": 1784, \"height\": 1070, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-023.webp\", \"caption\": \"\", \"page\": 0, \"index\": 23, \"width\": 1807, \"height\": 2048, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-024.webp\", \"caption\": \"\", \"page\": 0, \"index\": 24, \"width\": 859, \"height\": 588, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-025.webp\", \"caption\": \"\", \"page\": 0, \"index\": 25, \"width\": 1470, \"height\": 442, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-026.webp\", \"caption\": \"\", \"page\": 0, \"index\": 26, \"width\": 1842, \"height\": 440, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-027.webp\", \"caption\": \"\", \"page\": 0, \"index\": 27, \"width\": 1786, \"height\": 886, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-028.webp\", \"caption\": \"\", \"page\": 0, \"index\": 28, \"width\": 1784, \"height\": 494, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-029.webp\", \"caption\": \"\", \"page\": 0, \"index\": 29, \"width\": 1771, \"height\": 954, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-030.webp\", \"caption\": \"\", \"page\": 0, \"index\": 30, \"width\": 1769, \"height\": 1029, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-031.webp\", \"caption\": \"\", \"page\": 0, \"index\": 31, \"width\": 1763, \"height\": 254, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-032.webp\", \"caption\": \"\", \"page\": 0, \"index\": 32, \"width\": 851, \"height\": 256, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-033.webp\", \"caption\": \"\", \"page\": 0, \"index\": 33, \"width\": 1752, \"height\": 404, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-jp59rz1bzk/table-034.webp\", \"caption\": \"\", \"page\": 0, \"index\": 34, \"width\": 795, \"height\": 639, \"label\": \"Table\"}]"
motivation: 缺乏系统化方法衡量AI智能体在IT自动化中的有效性。
method: 构建了包含102个真实场景的基准框架，覆盖SRE、CISO和FinOps领域。
result: 提供了可复现的评估流程和可解释指标，支持社区扩展。
conclusion: ITBench能够帮助AI研究者理解智能体在IT自动化中的挑战与机遇。
---

## Abstract
Realizing the vision of using AI agents to automate critical IT tasks depends on the ability to measure and understand effectiveness of proposed solutions. We introduce ITBench, a framework that offers a systematic methodology for benchmarking AI agents to address real-world IT automation tasks. Our initial release targets three key areas: Site Reliability Engineering (SRE), Compliance and Security Operations (CISO), and Financial Operations (FinOps). The design enables AI researchers to understand the challenges and opportunities of AI agents for IT automation with push-button workflows and interpretable metrics. IT-Bench includes an initial set of 102 real-world scenarios, which can be easily extended by community contributions. Our results show that agents powered by state-of-the-art models resolve only 11.4% of SRE scenarios, 25.2% of CISO scenarios, and 25.8% of FinOps scenarios (excluding anomaly detection). For FinOps-specific anomaly detection (AD) scenarios, AI agents achieve an F1 score of 0.35. We expect ITBench to be a key enabler of AI-driven IT automation that is correct, safe, and fast. IT-Bench, along with a leaderboard and sample agent implementations, is available at https://github.com/ibm/itbench.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现代 IT 系统（云原生、微服务）日益复杂，运营人员（SRE、CISO、FinOps）面临巨大的运维挑战，亟需 AI 智能体自动执行故障诊断、合规评估、成本优化等关键任务。然而，目前缺乏系统化的方法在部署前评估 AI 智能体的有效性。
- **研究动机**：不同实验室已有一些面向 IT 运维的基准，但多存在场景少、任务单一、无真实环境、无自动化评估、缺乏排行榜等问题。ITBench 旨在填补空白，提供首个涵盖 SRE、CISO、FinOps 三大领域、基于真实问题的可复现评估框架。
- **整体意义**：通过标准化评测推动 AI 智能体在 IT 自动化中的发展，最终实现安全、正确、高效的自动化运维。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：ITBench 定义了一个包含环境、触发事件、目标状态的场景形式化描述（`p = <M, E, T, D>`），智能体与环境形成部分可观测马尔可夫决策过程（POMDP）。通过预定义的场景、工具、评估函数，对智能体进行推按钮式自动化评测。
- **关键技术细节**：
  - **场景生成**：SRE 场景来自真实 SaaS 产品故障（如缓存失效、高 CPU、镜像损坏）；CISO 场景基于 CIS 基准（Kubernetes、RHEL9）的合规要求；FinOps 场景基于 FinOps Foundation 定义的 KPI（成本超支告警、资源利用率、异常检测等）。
  - **智能体架构**：采用 CrewAI 框架，支持 ReAct、反思（Reflection）、解耦（Decompose）等技术。针对 SRE 提供 NL2Kubectl、NL2Traces、NL2Metrics、NL2Logs 等工具；对 CISO 提供策略生成（Kyverno/OPA Rego）和证据收集脚本工具；对 FinOps 提供 SQL 查询、异常检测工具。
  - **评估体系**：每个任务有明确的指标（如 pass@1、NTAM（归一化拓扑感知匹配）、MTTD、MTTR、F1、秩得分等）。NTAM 是论文提出的新指标，兼顾拓扑距离、节点重要性和链长惩罚。
- **公式或算法流程**：智能体与环境交互公式 `a_t = f(o_t | o̅_{t-1}, ā_{t-1})`（式 1），环境状态转移 `s_t = g(s_{t-1}, a_{t-1})`（式 2），观测 `o_t = h(s_t)`（式 3）。目标是最大化 `E_{p∼π}[I(g(s_{t*}, ...) = s_p^G)]`（式 5）。NTAM 涉及加权距离、GI 重要性、链长惩罚等参数，详见附录 F。

## 3. 实验设计：使用的数据集/场景、基准、对比方法

- **数据集/场景**：初始共 102 个真实场景 —— SRE 42 个、CISO 50 个、FinOps 10 个。SRE 场景基于真实 SaaS 产品故障；CISO 场景基于 CIS 基准（分 Kyverno、OPA、RHEL9、更新类 4 个复杂度等级）；FinOps 包括告警驱动（成本超支诊断与修复）、数据洞察（自然语言查询云账单）、异常检测与排序。
- **基准**：ITBench 本身作为基准框架；对比了多个 LLM 基座模型：GPT-4o、GPT-4o-mini、Llama-3.3-70B-instruct、Llama-3.1-8B-instruct、Llama-3.1-405B-instruct、Granite-3.1-8B-instruct、Mixtral-8x7B-instruct、Mistral-Large-2 等。
- **对比方法**：在同场景、同工具链下，不同基座模型作为智能体的“大脑”进行对比；SRE 任务还对比有无 trace 数据的影响。

## 4. 资源与算力

- **明确算力**：论文明确说明 SRE 实验使用 AWS m4.xlarge 集群（1 控制节点 + 3 工作节点，每个 12 核 48 GiB RAM），Kind 集群也可替代。FinOps 和 CISO 实验同样基于 AWS m4.xlarge。未给出具体 GPU 型号和训练时长（因为全部使用预训练 LLM 的 API 调用或本地推理，未进行模型微调）。所有模型使用 128K 上下文窗口。

## 5. 实验数量与充分性

- **实验数量**：
  - SRE：42 个场景 × 10 轮 × 4 模型 = 1680 次独立运行。
  - CISO：50 个场景 × 8 轮 × 8 模型 = 3200 次运行（部分模型因中断未完全执行，完成率 90-95%）。
  - FinOps：数据洞察 6 场景、异常检测 2 场景、告警驱动 2 场景，每个模型 10 轮。
- **充分性与公平性**：
  - 每种模型使用相同温度（0）、top_p=1e-7、seed=42，确保可重复性。
  - 场景复杂度分布：Easy 约 20-24%，Medium 约 52-60%，Hard 约 20-24%，覆盖不同难度。
  - 消融实验：在 SRE 上对比有无 trace 数据的影响；CISO 按场景类（Easy/Medium/Hard）分析；FinOps 区分不同任务类型。
  - 存在少量未完成（Agent 未返回结果、环境故障），但总体比例低（<10%），作者已注明。
- **结论**：实验设计全面，指标多样，对比公平，但未覆盖所有可能 LLM（如 Claude）、未做多智能体协作等高级方案。

## 6. 论文的主要结论与发现

- **总体性能偏低**：当前最优模型 GPT-4o 在 SRE 上的诊断 pass@1 仅 13.81%，修复 11.43%；CISO pass@1 为 24.74%；FinOps 数据洞察 29%，异常检测 F1 仅 0.6。说明 LLM 在真实 IT 自动化任务上仍有巨大提升空间。
- **复杂度影响显著**：三个领域从 Easy 到 Hard，成功率急剧下降（SRE Hard 场景修复率为 0%；CISO 的 Kyverno-update 类通过率最低；FinOps 所有模型无法解决 Hard 场景）。
- **诊断与修复可分离**：存在“诊断错误但仍修复成功”的案例（如通过泛化操作恢复服务），也存在“诊断正确但无法修复”的案例，表明两个任务不完全依赖。
- **观测数据的影响**：缺少 trace 数据会使 SRE 诊断准确率大幅下降（GPT-4o 从 18.1% 降至 9.52%）。
- **模型规模与性能正相关**：GPT-4o > Llama-3.3-70B > 8B 模型，但 8B 级模型在某些指标（如 MTTD）反而更快。
- **智能体推理模式**：成功诊断的智能体轨迹显示更少的“绕路服务”和更高的覆盖度，而失败者常过度依赖 NL2Kubectl 工具。

## 7. 优点

- **全面性**：首次将 SRE、CISO、FinOps 三大运维领域统一到同一测评框架中，场景真实且有细微粒度（复杂度、技术栈、故障链长度）。
- **真实性与可复现性**：基于真实 SaaS 故障、CIS 基准、FinOps Foundation KPI，通过容器化和 Ansible 实现完全可复现。
- **自动化评估**：支持自动部署、故障注入、评价、清理，以及排行榜，显著降低研究门槛。
- **新颖评价指标**：提出 NTAM（归一化拓扑感知匹配），比传统精确匹配更精细，能区分“接近正确”和“相差甚远”的预测。
- **开源与可扩展**：框架、场景、智能体代码均开源，社区可自由添加新应用、新场景、新手人。
- **可解释性分析**：通过智能体轨迹深入分析失败原因（工具误调用、推理错误、观测缺失等）。

## 8. 不足与局限

- **场景数量有限**：102 个场景与海量真实运维场景相比仍不足；部分场景仅 2-10 个，统计意义受限。
- **模型覆盖不全**：未测试 Claude、Gemini、多模态模型等；未测试微调模型。
- **评价粒度**：CISO 和 FinOps 的部分任务（如自然语言输出）尚未自动评估（仅靠 exact match），未来需引入 LLM-as-Judge。
- **环境简化**：使用 Kind 或小型 Kubernetes 集群，无法完全模拟超大规模、多层混合云的复杂性。
- **安全风险**：智能体执行 kubectl 等命令可能引入破坏，论文虽提到容器化隔离和 guardrails，但风险仍需进一步评估。
- **偏差风险**：CISO 场景仅基于 CIS 基准，未覆盖 ISO 27001、SOC2 等其他标准；FinOps 场景仅使用开源样例数据，商用账单模式不同。
- **可扩展性局限**：当前版本主要面向事件驱动的反应式任务，未涵盖预防性维护、主动优化等前瞻场景。

（完）
