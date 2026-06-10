---
title: "Mozart: Modularized and Efficient MoE Training on 3.5D Wafer-Scale Chiplet Architectures"
title_zh: Mozart：在3.5D晶圆级芯片架构上的模块化高效MoE训练
authors: "Shuqing Luo, Ye Han, Pingzhi Li, Jiayin Qin, Jie Peng, Yang Katie Zhao, Yu Cao, Tianlong Chen"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=zWHKKspghT"
tags: ["query:agents-os"]
score: 8.0
evidence: 在晶圆级芯片架构上针对MoE训练的算法-硬件协同设计
tldr: 针对MoE大模型在晶圆级芯片上训练面临的存储局部性和通信开销问题，提出Mozart算法-硬件协同设计框架。算法侧利用芯片模组模块化实现高效全对全通信，硬件侧优化资源利用。该工作在异构计算硬件上显著提升训练效率。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-neurips-2025-zwhkkspght/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1324, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zwhkkspght/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1421, \"height\": 379, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zwhkkspght/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 756, \"height\": 366, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zwhkkspght/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1400, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zwhkkspght/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1445, \"height\": 481, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zwhkkspght/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1416, \"height\": 351, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zwhkkspght/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1421, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zwhkkspght/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1420, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zwhkkspght/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1422, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zwhkkspght/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1428, \"height\": 282, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zwhkkspght/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 1421, \"height\": 284, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zwhkkspght/fig-012.webp\", \"caption\": \"\", \"page\": 0, \"index\": 12, \"width\": 1431, \"height\": 282, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zwhkkspght/fig-013.webp\", \"caption\": \"\", \"page\": 0, \"index\": 13, \"width\": 1409, \"height\": 467, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zwhkkspght/fig-014.webp\", \"caption\": \"\", \"page\": 0, \"index\": 14, \"width\": 1421, \"height\": 364, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zwhkkspght/fig-015.webp\", \"caption\": \"\", \"page\": 0, \"index\": 15, \"width\": 1405, \"height\": 473, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-neurips-2025-zwhkkspght/fig-016.webp\", \"caption\": \"\", \"page\": 0, \"index\": 16, \"width\": 1409, \"height\": 468, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-neurips-2025-zwhkkspght/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1421, \"height\": 210, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zwhkkspght/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1394, \"height\": 268, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zwhkkspght/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1451, \"height\": 216, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-neurips-2025-zwhkkspght/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1426, \"height\": 182, \"label\": \"Table\"}]"
motivation: MoE大模型部署在晶圆级芯片上存在存储和通信瓶颈。
method: 结合芯片模组模块化提出专家分配策略和硬件协同优化。
result: 实现高效片内全对全通信，提升资源利用率。
conclusion: 为异构计算架构支持大模型训练提供有效方案。
---

## Abstract
Mixture-of-Experts (MoE) architecture offers enhanced efficiency for Large Language Models (LLMs) with modularized computation, yet its inherent sparsity poses significant hardware deployment challenges, including memory locality issues, communication overhead, and inefficient computing resource utilization. Inspired by the modular organization of the human brain, we propose $\texttt{Mozart}$, a novel algorithm-hardware co-design framework tailored for efficient training of MoE-based LLMs on 3.5D wafer-scale chiplet architectures. On the algorithm side, $\texttt{Mozart}$ exploits the inherent modularity of chiplets and introduces: 
($1$) an expert allocation strategy that enables efficient on-package all-to-all communication, and ($2$) a fine-grained scheduling mechanism that improves communication-computation overlap through streaming tokens and experts. On the architecture side, $\texttt{Mozart}$ adaptively co-locates heterogeneous modules on specialized chiplets with a 2.5D NoP-Tree topology and hierarchical memory structure.
Evaluation across three popular MoE models demonstrates significant efficiency gains, enabling more effective parallelization and resource utilization for large-scale modularized MoE-LLMs.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义

混合专家模型（MoE）通过模块化计算提升了大型语言模型（LLM）的效率，但MoE固有的稀疏性带来了显著的硬件部署挑战，包括：
- **存储局部性差**：专家激活动态变化导致内存管理低效。
- **通信开销高**：专家并行中的全对全（All-to-All）通信需要跨所有单元同步，受限于带宽。
- **计算资源利用率低**：负载动态不均限制批大小，导致GPU/芯片利用率不足。

现有2.5D/3.5D芯片架构（如Maestro、Cambricon-LLM、FRED）大多针对密集均匀计算或推理设计，忽视了MoE的细粒度模块化特性，导致跨芯片通信和资源利用低下。

受人类大脑模块化组织启发，论文提出 **Mozart** ——一个面向3.5D晶圆级芯片架构的算法-硬件协同设计框架，旨在通过软件和硬件联合优化，实现MoE-LLM在芯片系统上的高效训练。

## 2. 方法论

### 核心思想
利用芯片的物理模块化来匹配MoE的逻辑模块化，通过分析专家激活先验（路由策略），优化专家布局、通信和调度，同时设计专用3.5D芯片架构以支持这些优化。

### 关键技术细节

#### 算法侧

1. **专家聚类与分配**  
   - 先验分析：使用指令微调数据集（如Alpaca）进行推理预填充阶段，收集路由选择。
   - 计算两个指标：  
     - 单个专家工作负载分布向量 **V**（归一化激活频率）。  
     - 专家对共激活模式矩阵 **C** 和归一化矩阵 **P**。  
   - **专家聚类**：基于共激活模式，采用类似最远点采样的算法，将专家聚类为 $N_c$ 个簇，增强簇内合作，减少簇间合作（见Algorithm 1）。  
   - **簇分配**：将簇分配到芯片组，通过二进制整数规划最小化各组的负载差异（公式5）。

2. **高效全对全通信**  
   - 标准专家并行中，每个令牌需 **k** 次复制（top-k路由）。若将频繁共激活的专家放在同一芯片上，则每个令牌的复制次数 **$C_T$** 可降低。论文证明了 **$C_T$** 是实际通信数据量与令牌数之比的最小上界。

3. **细粒度调度**（通信-计算重叠）  
   - **流式专家**：根据工作负载优先级，先加载计算量大的专家权重到芯片。  
   - **流式令牌**：将全局批次划分为微批（流式令牌），实现注意力计算与专家权重加载的重叠。  
   - **流水线执行**：利用专家选择的时间局部性，预取频繁激活的专家权重，在FFN计算时并发加载下一微批的权重（见图4）。

#### 硬件侧

1. **2.5D NoP-Tree拓扑**  
   - 将注意力芯片（中央调度节点）和专家芯片（叶节点）分离，交换机提供网络内MoE聚合，减少通信延迟。

2. **三维集成**：每个计算芯片垂直堆叠逻辑层和SRAM层，通过混合键合连接，实现高带宽低延迟的激活缓存。

3. **两级存储层次**：  
   - 模型权重存储在DRAM（每个4个专家簇共享一个DRAM I/O）。  
   - 激活缓存于芯片上的SRAM，利用3D堆叠实现快速访问。

4. **算法到硬件的映射**：  
   - 每个训练步处理32个样本，分为4个微批（每批8个序列）。  
   - 采用权重流式策略，一次只加载一个Transformer块。  
   - 注意力部分使用多个脉动阵列（SA），结果通过NoP-Tree路由到交换机进行令牌分发。  
   - 反向传播时梯度逆流，参数更新后写回DRAM。

## 3. 实验设计

### 使用模型与数据集
- **MoE模型**：  
  - Qwen3-30B-A3B（总参30.5B，激活3.3B，128个路由专家，top-8）  
  - OLMoE-1B-7B-0924（总参6.92B，激活1.3B，64个路由专家，top-8）  
  - deepseek-moe-16b-base（总参16.4B，激活2.7B，64个路由专家+2共享专家，top-6）  
- **数据集**：Alpaca（52K指令样本），用于先验分析和后训练仿真。

### Benchmark与对比方法
- **基线**：不使用任何优化的Mozart配置（Baseline）。  
- **三种变体**：  
  - Mozart-A：仅启用通信-计算重叠（细粒度调度）  
  - Mozart-B：在A基础上增加高效全对全通信  
  - Mozart-C：在B基础上增加专用专家布局（完整Mozart）  
- **对比指标**：训练每步平均延迟（seconds）和归一化延迟。

### 实验场景
- 固定序列长度256，使用HBM2 DRAM（主实验）。  
- 序列长度变化实验（128、256、512）。  
- DRAM带宽对照实验（SSD 15.8GB/s vs HBM2 256GB/s）。  
- 所有结果报告为每步平均延迟，经过1k迭代平均。

## 4. 资源与算力

论文未明确说明实际训练/微调时使用的GPU数量和训练时长。  
- 先验分析使用的是NVIDIA A100 80G GPU和PyTorch。  
- 硬件仿真基于Verilog实现的逻辑/互连/开关，使用Synopsys Design Compiler综合（28nm工艺），功耗由Synopsys PrimePower报告。  
- 仿真时采用了周期精确模拟器，并与Verilog结果验证一致。  
- 芯片配置：16个专家芯片（分4组，每组共享一个DRAM I/O）、1个注意力芯片，每个芯片36–100个Tile，每个Tile 16个SA，每个SA有256–576个PE。使用6个HBM2 DRAM（4个分给专家组，2个专用于注意力芯片）。所有设计运行在1 GHz时钟、FP16精度。

**注意**：论文只给出了硬件仿真和模拟的延迟/功耗结果，没有报告实际GPU训练成本（如GPU小时数）。

## 5. 实验数量与充分性

### 实验数量
- **主实验**：3种模型 × 4种配置（Baseline、A、B、C）= 12个数据点（图6a、表3）。  
- **序列长度消融**：3种模型 × 4种配置 × 3种长度（128/256/512）= 36个数据点（图6b、附录B）。  
- **DRAM带宽消融**：1种模型（Qwen3） × 4种配置 × 2种DRAM类型 = 8个数据点（图6c）。  
- **通信复杂度分析**：表4给出了各模型下Mozart-A/B/C的 $C_T$ 和归一化延迟。  
- **硬件资源参数**：表1、表2列出模型配置和芯片参数。  
- **额外消融**：回答了三个深入问题（Q1~Q3），通过对延迟瓶颈分析和算法贡献排序给出定性分析。

### 实验充分性与公平性
- **充分**：覆盖了多种模型规模、多种优化策略组合、关键硬件参数（带宽、序列长度）影响，结果有归一化对比。  
- **客观公平**：  
  - 所有变体基于同一基线逐步增加优化，归因清晰。  
  - 使用周期精确模拟器，结果可重复。  
  - 论文公开了代码仓库（附录A）。  
- **潜在偏差**：  
  - 仅使用了Alpaca一个数据集进行先验分析和训练模拟，未见跨数据集验证。  
  - 模拟环境假设固定芯片配置，未考虑实际制造变异性。  
  - 没有与真实GPU集群（如8×A100）上的实际训练时间对比，仅与自身基线对比。

## 6. 主要结论与发现

1. **性能提升显著**：完整Mozart在三种模型上分别实现1.92×、2.37×、2.17×的加速（相对于无优化基线）。  
2. **关键优化排序**：通信-计算重叠贡献最大（约1.3~1.5×加速），其次是高效全对全通信，最后是专家布局。  
3. **系统瓶颈**：Mozart整体受限于DRAM到芯片的权重流式加载（memory-bound），而非计算。  
4. **带宽影响**：HBM2下优化效果更显著；SSD下由于流式延迟占主导，优化收益有限。  
5. **兼容性**：与参数高效微调方法（LoRA、QLoRA）正交。

## 7. 优点

- **算法-硬件联合设计**：从实际硬件瓶颈出发设计专家布局和调度，而非仅软件层面优化。  
- **充分利用MoE先验**：利用路由策略的统计特性（专家专业化和合作模式）指导芯片级映射，具备实际可行性。  
- **细粒度流水线**：流式令牌和流式专家有效重叠DRAM通信与计算，降低同步开销。  
- **架构创新**：2.5D NoP-Tree拓扑+3D逻辑-存储堆叠，为MoE设计专用层次存储和网络内聚合。  
- **实验设计完善**：消融实验覆盖序列长度、DRAM类型、不同优化组合，给出深入分析（Q1~Q3）。  
- **可复现性**：开源代码，详细硬件参数和仿真设置公开。

## 8. 不足与局限

- **模拟而非实测**：所有结果来自周期精确模拟器，缺乏真实芯片流片或实际GPU集群对比。  
- **单数据集验证**：先验分析和后训练模拟仅基于Alpaca，未评估其他数据集（如自然语言推理、代码生成等）对路由模式的影响。  
- **注意力芯片单点瓶颈**：注意力模块被映射到单个芯片，可能因资源有限导致延迟，论文承认可通过数据/张量并行改进但未实验。  
- **交换机可能成为瓶颈**：高通信需求下交换机带宽可能受限，论文仅通过调度缓解，未来可能需要更多芯片面积给交换机。  
- **未考虑训练动态变化**：路由模式在训练过程中会变化，论文的专家布局基于初始先验，未探讨重新聚类与重映射的自适应方案。  
- **未与现有GPU/ASIC对比**：未报告在A100等GPU上采用Tutel/MegaBlocks的实际延迟，无法评估相较于现有方案的绝对优势。  
- **能耗评估有限**：硬件功耗基于28nm工艺门级仿真，未与先进工艺（如7nm/5nm）对比。

（完）
