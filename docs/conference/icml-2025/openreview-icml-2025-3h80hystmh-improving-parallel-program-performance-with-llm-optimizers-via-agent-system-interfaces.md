---
title: Improving Parallel Program Performance with LLM Optimizers via Agent-System Interfaces
title_zh: 通过智能体-系统接口利用LLM优化器提升并行程序性能
authors: "Anjiang Wei, Allen Nie, Thiago S. F. X. Teixeira, Rohan Yadav, Wonchan Lee, Ke Wang, Alex Aiken"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=3h80HyStMH"
tags: ["query:agents-os"]
score: 7.0
evidence: 提出智能体-系统接口以自动化并行程序映射器开发
tldr: 针对高性能计算中并行程序映射器手动调优耗时问题，提出基于LLM优化器和智能体-系统接口的框架，通过领域特定语言抽象底层复杂性，自动化生成高性能映射器，实验表明显著提升并行程序性能且降低人工成本。
source: ICML-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/openreview/openreview-icml-2025-3h80hystmh/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1755, \"height\": 541, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3h80hystmh/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1742, \"height\": 597, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3h80hystmh/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1754, \"height\": 542, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3h80hystmh/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1757, \"height\": 1206, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3h80hystmh/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 853, \"height\": 480, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3h80hystmh/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1768, \"height\": 501, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3h80hystmh/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1578, \"height\": 792, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3h80hystmh/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1786, \"height\": 1661, \"label\": \"Figure\"}, {\"url\": \"assets/figures/openreview/openreview-icml-2025-3h80hystmh/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1746, \"height\": 986, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/openreview/openreview-icml-2025-3h80hystmh/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1774, \"height\": 340, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3h80hystmh/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1386, \"height\": 325, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3h80hystmh/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 884, \"height\": 419, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3h80hystmh/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 881, \"height\": 424, \"label\": \"Table\"}, {\"url\": \"assets/tables/openreview/openreview-icml-2025-3h80hystmh/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1783, \"height\": 1237, \"label\": \"Table\"}]"
motivation: 并行程序性能优化中，映射器开发依赖手工调优，缺乏系统专业知识的人员难以高效完成。
method: 提出Agent-System Interface框架，包含领域特定语言和LLM优化器，自动生成并优化映射器代码。
result: 在多个科学计算基准上，该方法自动生成的映射器性能超越手工调优版本，且耗时大幅减少。
conclusion: 该工作展示了智能体与系统接口结合LLM优化器自动化系统编程的潜力，可扩展到更广泛的系统优化任务。
---

## Abstract
Modern scientific discovery increasingly relies on high-performance computing for complex modeling and simulation. A key challenge in improving parallel program performance is efficiently mapping tasks to processors and data to memory, a process dictated by intricate, low-level system code known as *mappers*. Developing high-performance mappers demands days of manual tuning, posing a significant barrier for domain scientists without systems expertise. We introduce a framework that automates mapper development with generative optimization, leveraging richer feedback beyond scalar performance metrics. Our approach features the Agent-System Interface, which includes a Domain-Specific Language (DSL) to abstract away the low-level complexity of system code and define a structured search space, as well as AutoGuide, a mechanism that interprets raw execution output into actionable feedback. Unlike traditional reinforcement learning methods such as OpenTuner, which rely solely on scalar feedback, our method finds superior mappers in far fewer iterations. With just 10 iterations, it outperforms OpenTuner even after 1000 iterations, achieving $3.8\times$ faster performance. Our approach finds mappers that surpass expert-written mappers by up to $1.34\times$ speedup across nine benchmarks while reducing tuning time from days to minutes.

---

## 论文详细总结（自动生成）

好的，作为一名资深学术论文分析助手，我将按照您的要求，对这篇论文进行结构化、深入、客观的中文总结。

---

### 论文核心内容总结

#### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：在高性能计算领域，并行程序的性能优化高度依赖“映射器”——一个负责将计算任务分配到处理器、数据分配到内存的低级系统代码。手动编写和调优高性能映射器需要数天时间，且需要深厚的系统专业知识，这对广大领域科学家（如物理学家、生物学家）构成了巨大的技术障碍，导致他们难以充分利用超算资源。
- **研究动机**：自动化映射器的开发过程，让非系统专家也能高效地优化并行程序，从而释放高性能计算在科学发现中的巨大潜力。传统方法（如基于强化学习的OpenTuner）仅依赖标量性能指标进行优化，搜索效率低。
- **整体含义**：本文首次将基于大语言模型的“生成式优化”技术应用于系统代码优化领域，提出了一种“智能体-系统接口”（Agent-System Interface），使得LLM能够自动化地探索和生成比专家手动编写的更优的映射器，显著提升了并行程序的性能，并将调优时间从天级缩短到分钟级。

#### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：通过设计一个智能体-系统接口作为LLM和底层系统之间的抽象层，将生成式优化问题转化为一个迭代的代码改进过程。该接口包含两个关键技术：

    1.  **领域特定语言（DSL）**：
        - **作用**：将映射器的编写从复杂的低级C++代码抽象为简洁、声明式的高级DSL代码。DSL定义了结构化的搜索空间，涵盖了所有关键性能决策（如处理器选择、内存放置、数据布局、索引映射）。
        - **优势**：大幅降低代码量（平均减少14倍），减小了LLM生成代码的“语义鸿沟”，使得即使DSL未在训练语料中出现，LLM也能高效生成正确代码。

    2.  **AutoGuide机制**：
        - **作用**：将系统执行的原始反馈（如晦涩的断言失败、简单的性能数字）转化为对LLM更丰富、更具可操作性的自然语言反馈，包括错误解释和改进建议。
        - **优势**：相比于传统强化学习仅依赖标量奖励（如执行时间），AutoGuide提供了方向性更强的文本反馈，使得LLM优化器能更快地找到更优的映射器。

- **技术流程（生成式优化）**：
    1.  **输入**：服务器硬件规格和应用元数据（任务名、数据依赖等）。
    2.  **生成**：LLM智能体根据输入，生成DSL代码（映射器）。
    3.  **执行与反馈**：系统执行映射器并运行应用，生成原始执行输出。
    4.  **反馈加工**：AutoGuide机制将原始输出加工成带有解释和建议的丰富文本反馈。
    5.  **迭代优化**：LLM优化器根据加工后的反馈，迭代地修改DSL代码，旨在提升性能。
    6.  **输出**：迭代结束后，输出性能最高的映射器。

#### 3. 实验设计

- **数据集/场景**：使用了9个基准测试程序，包括3个科学计算负载（Circuit电路仿真、Stencil 2D网格仿真、Pennant非结构化网格流体动力学）和6个知名的并行矩阵乘法算法（Cannon's, SUMMA, PUMMA, Johnson's, Solomonik's, COSMA）。这个基准套件兼顾了应用多样性和算法深度。
- **对比方法**：
    - **专家编写的映射器**：代表了当前手工调优最高标准。
    - **随机映射器**：随机搜索基线。
    - **OpenTuner**：经典的基于强化学习的自动调优框架。
    - **OPRO**：另一种LLM优化器框架。
    - **本文方法（Trace）**：使用Trace框架实现的智能体优化器。

#### 4. 资源与算力

- **硬件平台**：单节点，配备2颗Intel 10核E5-2640 v4 CPU，256GB主存，4块NVIDIA Tesla P100 GPU。
- **LLM**：使用 `gpt-4o-2024-08-06` 模型。
- **训练时长**：论文未提及LLM的训练信息。优化过程的单应用调优时间约为 **10分钟** (**论文明确提及**)。
- **算力总结**：论文硬件配置描述清晰，但未说明在调优过程中调用LLM API的总次数或成本。

#### 5. 实验数量与充分性

- **实验数量**：
    - **主实验**：在9个基准测试上进行了性能对比，每个基准的优化过程重复了5次，并报告了平均值和最优值，结果以吞吐量图呈现，统计量充足。
    - **消融实验**：针对DSL和AutoGuide分别进行了消融研究。
        - **DSL消融**：设置了10种映射策略，在单次生成和10次迭代两种设置下，对比LLM用DSL和C++生成代码的成功率。
        - **AutoGuide消融**：在3个基准测试上，对比了无反馈、仅执行反馈、执行反馈+解释、以及完整反馈（解释+建议）等不同反馈设计的效果。
    - **对比实验**：将本文方法（10次迭代）与OpenTuner进行对比，并专门将OpenTuner的迭代次数延长到1000次以进行比较。
- **充分性评价**：
    - **客观公平**：实验设计相对客观。对比了有代表性的基线方法，包括传统RL（OpenTuner）和另一种LLM优化器（OPRO）。消融实验清晰地验证了DSL和AutoGuide两个核心组件的有效性。
    - **实验充分**：主实验覆盖了多种科学计算和矩阵乘法场景，消融实验针对关键设计点进行，对比实验展示了本文方法与传统方法的巨大差距。5次重复实验考虑了LLM生成结果的随机性。实验总体上是充分且具有说服力的。

#### 6. 论文的主要结论与发现

1.  **性能超越专家**：LLM智能体自动生成的映射器在所有9个基准测试中都能匹配或超越专家手工编写的映射器，最高实现 **1.34倍** 的加速。
2.  **效率远超传统方法**：在仅运行10次迭代的情况下，本文方法（Trace）的性能优于运行1000次迭代的OpenTuner，达到 **3.8倍** 的吞吐量优势。若两者都运行10次迭代，Trace的优势达到 **11倍**。
3.  **代码生成成功率更高**：DSL相比C++，无论是单次生成还是迭代修正，成功率均显著更高（单次：80% vs 0%；迭代：100% vs 0%），证明了DSL作为智能体-系统接口核心设计的有效性。
4.  **丰富反馈至关重要**：AutoGuide提供的完整反馈（错误解释+修改建议）是实现高效优化的关键，其效果显著优于仅提供执行输出或无反馈的变体。
5.  **调优时间大幅缩短**：将映射器开发从数天缩短至 **10分钟**。

#### 7. 优点

- **方法创新性**：首次将“生成式优化”应用于系统代码优化，并创造性地提出“智能体-系统接口”这一概念，系统性地解决了LLM在复杂系统编程任务中面临的代码生成和反馈理解两大挑战。
- **DSL设计精巧**：DSL不仅简化了代码生成，更重要的是它定义了一个结构化的、可控的搜索空间，这比直接让LLM在庞大的C++代码空间中搜索要高效得多。这是一种有效的“问题简化”策略。
- **AutoGuide机制实用**：将从系统得到的原始、不透明的反馈转化为对LLM友好的自然语言解释和建议，这一设计非常巧妙，充分发挥了LLM在理解和生成语言方面的优势。
- **实验结果极具说服力**：不仅在与专家和随机基线对比中表现出色，更在与业界著名的自动调优框架OpenTuner的对比中取得了数量级上的优势，凸显了方法的巨大潜力。
- **极高的实用价值**：将调优时间从天级缩短到分钟级，解决了领域科学家的实际痛点，具有重要的应用推广价值。

#### 8. 不足与局限

1.  **搜索空间限制**：DSL虽然高效，但也意味着它定义了一个比通用C++更小的搜索空间。结构化的搜索空间（导致专家映射器并不是最优的，且所有比专家更好的映射器都在DSL定义的范围内，这恰恰证明了DSL的有效性）。但论文也承认，对于某些无法用当前DSL表达的极端优化，该方法将无能为力。未来的工作可能需要考虑更灵活的DSL或混合方法。
2.  **计算成本依赖**：该方法依赖于调用强大的商业LLM (GPT-4o)。虽然每个应用的调优只需10分钟，但背后有API调用成本。论文未分析总token消耗或API成本，这对于实际部署的经济性评估是缺失的。
3.  **单一框架依赖**：所有实验都基于Legion并行编程框架。虽然Legion具有代表性，但方法的通用性在其他框架（如StarPU, Chapel）上尚未得到验证。扩展到其他框架需要开发相应的DSL编译器。
4.  **性能波动分析**：虽然报告了多次运行的平均值和最差值，但在部分基准（如SUMMA, PUMMA, Solomonik）上出现了零吞吐量的最差情况。论文将此归因于搜索空间中的无效配置。虽然最终用户会选择最佳结果，但对于优化过程的稳定性和鲁棒性有更高要求。
5.  **系统未涉及**：论文没有讨论如何自动选择LLM提示的最佳构建方式或如何自动调整迭代次数等元问题。

（完）
