---
title: Auto-reconfiguration for Latency Minimization in CPU-based DNN Serving
title_zh: 基于CPU的DNN服务延迟最小化的自动重配置
authors: "Ankit Bhardwaj, Amar Phanishayee, Deepak Narayanan, Ryan Stutsman"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=Dg24PyeWsI"
tags: ["query:agents-os"]
score: 8.0
evidence: CPU服务器上延迟最小化的自动重配置，异构资源管理
tldr: 该论文针对CPU服务器上DNN推理延迟问题，提出自动重配置方法。通过动态调整模型实例数和线程分配，在多样化的模型和服务器配置下最小化推理延迟。实验表明该方法显著优于静态配置策略，为CPU服务的性能优化提供了实用方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-dg24pyewsi/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1659, \"height\": 451, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dg24pyewsi/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 778, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dg24pyewsi/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 860, \"height\": 515, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dg24pyewsi/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1648, \"height\": 354, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dg24pyewsi/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1557, \"height\": 283, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dg24pyewsi/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 747, \"height\": 361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dg24pyewsi/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 701, \"height\": 301, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dg24pyewsi/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 808, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dg24pyewsi/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 776, \"height\": 457, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-dg24pyewsi/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 762, \"height\": 453, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-dg24pyewsi/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 856, \"height\": 226, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dg24pyewsi/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 862, \"height\": 390, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-dg24pyewsi/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 817, \"height\": 200, \"label\": \"Table\"}]"
motivation: CPU服务器上DNN推理中，单实例多线程并行存在收益递减，需要动态调整配置。
method: 提出自动重配置系统，根据工作负载和CPU核心数动态选择实例数和线程分配。
result: 在不同模型和服务器配置下均能降低推理延迟，优于静态方案。
conclusion: 自动重配置是CPU服务优化的有效方法，可推广至异构环境。
---

## Abstract
In this paper, we investigate how to push the performance limits of serving Deep Neural Network (DNN) models on CPU-based servers. Specifically, we observe that while intra-operator parallelism across multiple threads is an effective way to reduce inference latency, it provides diminishing returns. Our primary insight is that instead of running a single instance of a model with all available threads on a server, running multiple instances each with smaller batch sizes and fewer threads for intra-op parallelism can provide lower inference latency. However, the right configuration is hard to determine manually since it is workload- (DNN model and batch size used by the serving system) and deployment-dependent (number of CPU cores on server). We present Packrat, a new serving system for online inference that given a model and batch size (𝐵) algorithmically picks the optimal number of instances (𝑖), the number of threads each should be allocated (𝑡), and the batch sizes each should operate on (𝑏) that minimizes latency. Packrat is built as an extension to TorchServe and supports online reconfigurations to avoid serving downtime. Averaged across a range of batch sizes, Packrat improves inference latency by 1.43× to 1.83× on a range of commonly used DNNs.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：深度神经网络（DNN）在线服务（如语音识别、文本补全、聊天机器人等）需要低延迟实时响应。当前主流系统（TensorFlow Serving、TorchServe、Triton）多基于GPU，但GPU成本高、功耗大且推理场景下利用率低。而现代CPU拥有众多核心（56-64核）及专用指令（AVX-512、AMX），使得CPU服务器成为可行且经济的选择。然而，现有CPU服务默认采用单实例、全部线程进行算子内并行（intra-op parallelism），这会导致收益递减——线程增多后延迟改善迅速下降。

- **核心问题**：如何自动确定最优的实例数（i）、每个实例的线程数（t）和每个实例处理的批量大小（b），以最小化CPU上DNN推理的延迟？该配置依赖模型、批量大小、CPU核心数等，手动调节困难。

- **整体含义**：本文提出Packrat系统，通过自动重配置来突破CPU服务延迟瓶颈，实现1.43×~1.83×的延迟改进，为CPU推理服务提供实用优化方案。

## 2. 方法论：核心思想、关键技术细节、算法流程

- **核心思想**：取代“用一个实例占用所有线程”的默认做法，将大批量拆分成多个小批量，由多个实例并行处理，每个实例分配较少线程进行算子内并行，从而更高效利用资源。

- **关键技术细节**：
  - **系统架构**：基于TorchServe扩展，包括批量大小估计器、优化器、资源分配器、调度器和工作实例等模块。
  - **离线配置文件分析**：对模型进行有限配置的离线文件分析，覆盖 \(t \in \{1,...,T\}\) 和 \(b \in \{2^0,2^1,...,2^n\}\) 的组合，记录每种配置的平均批量延迟 \(L_{t,b}\)。使用幂次2的b可大幅减少组合数（如T=16,n=10时从16384减至176），文件分析时间从30天降至几小时。
  - **优化器算法**：将问题建模为二维背包问题，使用动态规划求解。定义 \(opt[t,b]\) 为用t个线程处理b个输入的最小延迟。递推公式：
    \[
    opt[t,b] = \min_{t' \le t, b' \le b} \left( \max\left( opt[t-t', b-b'], L_{t',b'} \right) \right)
    \]
    其中 \(L_{t',b'}\) 是文件分析的配置延迟。最终最优配置对应 \(opt[T,B]\)。
  - **容错设计**：利用主动-被动缩放机制实现无停机重配置：先为新配置创建被动实例，切换流量后逐步销毁旧实例。
  - **批量大小估计**：使用指数加权移动平均与模式平滑，避免频繁重配置。

## 3. 实验设计

- **数据集/场景**：使用4个常用DNN模型：ResNet-50、Inception-v3（图像分类），GPT-2、BERT（语言模型）。所有模型来自PyTorch模型仓库。
- **Benchmark**：对比“胖实例”基线（单实例用所有16个线程处理整个批量）。Packrat自动搜索的配置与基线比较。
- **对比方法**：
  - 微基准：PyTorch直接推理（eager模式和graph模式）。
  - 端到端：集成在TorchServe中运行；另与16个单线程实例对比（附录）。
  - 额外硬件：在AMD EPYC和Intel Emerald Rapids CPU上验证。
- **评估指标**：延迟、吞吐量（几乎一致）；配置变化时的延迟时间线。

## 4. 资源与算力

- 论文明确说明了实验硬件：
  - 主测试机：2×16核 Intel Xeon Gold 6142 @2.6GHz，384GB RAM，Ubuntu 20.04，PyTorch 1.12.1，TorchServe 0.6.1，Intel MKL-DNN v2.6.0，OpenMP 4.5。
  - 额外机器：16核 AMD EPYC 7302P @3.0GHz，128GB RAM；28核 Intel Xeon 5512U @2.1GHz，128GB RAM（DDR5）。
  - 超线程关闭以防干扰。
- 未提及GPU使用（纯CPU实验），也未报告具体训练时长（论文聚焦推理服务）。

## 5. 实验数量与充分性

- **实验数量**：包含4个模型，每个模型多个批量大小（2的幂次，如8、32、128、512、1024等），共约数十组微基准+端到端实验。此外还包括：
  - 配置切换的延迟时间分析（Inception-v3）。
  - 预期速度与实际速度对比分析（附录A）。
  - 非均匀实例配置示例（附录B）。
  - 两个额外CPU架构的验证（附录C）。
- **充分性**：较充分。覆盖了不同模型类型（CNN与Transformer）、不同批量大小、不同硬件架构；提供了速度提升统计（均值与最大值）；分析了性能差距原因（CPU降频、内存带宽竞争）。但缺少与其他优化系统（如TVM、TensorTuner）的直接对比，也未在多样化真实负载（如多模型并发）下测试。

## 6. 主要结论与发现

- **核心发现**：多实例（“瘦实例”）比单实例（“胖实例”）能显著降低延迟，因为缓解了OpenMP barrier同步和资源竞争问题。
- **量化结果**：
  - 微基准：ResNet-50和Inception-v3平均加速1.53×和1.52×；GPT-2和BERT平均1.18×和1.13×。
  - 端到端TorchServe：平均加速1.43×~1.83×，最大1.72×~2.09×。
  - 配置切换可在约5秒内完成，暂不影响服务可用性。
- **性能差距原因**：实际速度低于预期速度，主要源于CPU license-based downclocking（降频~15%）和内存带宽竞争导致的访问延迟增加。
- **系统特性**：自动化、无停机重配置，适应工作负载变化。

## 7. 优点

- **创新性**：提出多实例并行替代全线程单实例的思路，解决了算子内并行收益递减问题。
- **实用性**：作为TorchServe扩展，可直接在现有系统上部署；自动配置无需人工介入；支持在线重配置不停服。
- **高效性**：通过使用幂次2的批量大小，文件分析组合数减少两个数量级；动态规划在合理时间内找到最优解。
- **实验设计全面**：涵盖多种模型、批量大小、硬件架构，并对性能差距进行了深入归因分析。
- **开源**：代码公开（github链接），可复现。

## 8. 不足与局限

- **实验覆盖局限性**：
  - 未与其他自动调优系统（如TensorTuner、TVM自动调度）进行直接对比，未充分证明优于已有优化方法。
  - 仅测试单一服务器单模型场景，未涉及多模型并发、流水线（如InferLine）等复杂服务场景。
  - 未在真实生产负载（如动态请求速率波动、多任务混合）下评估长期鲁棒性。
- **方法局限**：
  - 离线文件分析假定模型固定，若模型更新或硬件变化需重新文件分析。
  - 优化器假设实例间无相互干扰（忽略CPU降频和内存竞争），实际存在偏差，但作者论证这种偏差对配置选择影响不大。
  - 仅适用于CPU推理，未扩展到GPU或其他加速器。
- **偏差风险**：
  - 实验均在Cloudlab固定硬件上进行，可能无法代表所有CPU服务器（尤其带不同NUMA配置或不同SIMD扩展的机器）。
  - 主要对比“胖实例”基线，未评估与其他多实例策略（如MICA式严格核分割）的优劣。
- **应用限制**：
  - 重配置耗时数秒，仅适合工作负载变化不频繁的场景。
  - 需用户指定可接受的批量超时等参数。

（完）
