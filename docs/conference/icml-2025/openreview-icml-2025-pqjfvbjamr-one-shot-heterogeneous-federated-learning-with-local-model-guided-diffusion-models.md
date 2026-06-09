---
title: One-Shot Heterogeneous Federated Learning with Local Model-Guided Diffusion Models
title_zh: 基于本地模型引导扩散模型的一次性异构联邦学习
authors: "Mingzhao Yang, Shangchao Su, Bin Li, Xiangyang Xue"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=PqJFVbJAMR"
tags: ["query:agents-os"]
score: 5.0
evidence: 异构联邦学习与扩散模型，处理异构客户端模型
tldr: 该论文提出FedLMG，一种异构一次性联邦学习方法。客户端无需部署基础模型，仅训练和上传本地模型。服务端利用本地模型引导扩散模型生成合成数据以聚合异构模型。该方法降低客户端计算需求，同时保持良好性能。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-pqjfvbjamr/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1697, \"height\": 751, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pqjfvbjamr/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 830, \"height\": 968, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pqjfvbjamr/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 815, \"height\": 461, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pqjfvbjamr/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 824, \"height\": 998, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pqjfvbjamr/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1429, \"height\": 959, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pqjfvbjamr/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1417, \"height\": 980, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-pqjfvbjamr/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1432, \"height\": 1206, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-pqjfvbjamr/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1603, \"height\": 806, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pqjfvbjamr/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 859, \"height\": 171, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pqjfvbjamr/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 861, \"height\": 162, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pqjfvbjamr/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1737, \"height\": 148, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pqjfvbjamr/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 685, \"height\": 93, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pqjfvbjamr/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1736, \"height\": 231, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pqjfvbjamr/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 862, \"height\": 186, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pqjfvbjamr/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1767, \"height\": 385, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pqjfvbjamr/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1735, \"height\": 197, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pqjfvbjamr/table-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1239, \"height\": 151, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pqjfvbjamr/table-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1773, \"height\": 380, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-pqjfvbjamr/table-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1739, \"height\": 442, \"label\": \"Table\"}]"
motivation: 现有基于扩散模型的联邦学习方法需要客户端部署基础模型，计算需求高且不适用于异构模型。
method: 提出FedLMG，客户端仅训练本地模型，服务端用本地模型引导扩散生成聚合数据。
result: 在异构客户端模型上取得良好性能，且客户端计算负担轻。
conclusion: 为异构联邦学习提供了无需基础模型的高效方案。
---

## Abstract
In recent years, One-shot Federated Learning (OSFL) methods based on Diffusion Models (DMs) have garnered increasing attention due to their remarkable performance. However, most of these methods require the deployment of foundation models on client devices, which significantly raises the computational requirements and reduces their adaptability to heterogeneous client models. In this paper, we propose FedLMG, a heterogeneous one-shot Federated learning method with Local Model-Guided diffusion models. In our method, clients do not need access to any foundation models but only train and upload their local models, which is consistent with traditional FL methods. On the clients, we employ classification loss and batch normalization loss to capture the broad category features and detailed contextual features of the client distributions. On the server, based on the uploaded client models, we utilize backpropagation to guide the server’s DM in generating synthetic datasets that comply with the client distributions, which are then used to train the aggregated model. By using the local models as a medium to transfer client knowledge, our method significantly reduces the computational requirements on client devices and effectively adapts to scenarios with heterogeneous clients. Extensive quantitation and visualization experiments on three large-scale real-world datasets, along with theoretical analysis, demonstrate that the synthetic datasets generated by FedLMG exhibit comparable quality and diversity to the client datasets, which leads to an aggregated model that outperforms all compared methods and even the performance ceiling, further elucidating the significant potential of utilizing DMs in FL.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
异构联邦学习与扩散模型，处理异构客户端模型。

### 2. 核心内容
该论文提出FedLMG，一种异构一次性联邦学习方法。客户端无需部署基础模型，仅训练和上传本地模型。服务端利用本地模型引导扩散模型生成合成数据以聚合异构模型。该方法降低客户端计算需求，同时保持良好性能。

### 3. 对应检索需求
heterogeneous computing infrastructure for AI workloads。

### 4. 来源与原文
- Source：ICML-2025-Accepted
- OpenReview：[https://openreview.net/forum?id=PqJFVbJAMR](https://openreview.net/forum?id=PqJFVbJAMR)
