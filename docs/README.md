<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-06-15 ~ 2026-06-24
- 运行时间：2026-06-24 03:44:52 UTC
- 运行状态：成功
- 本次总论文数：19
- 精读区：8
- 速读区：11

### 今日简报（AI）
今日推荐聚焦KV缓存优化与边缘AI协同推理，两篇高分精读论文分别探讨多轮对话缓存共享与编码智能体工作负载分析。值得重点精读《SwiftCache》和《CacheWise》，它们从底层机制入手提升大模型服务效率；若感兴趣边缘计算，可速读RISE等三篇论文。后续建议结合具体业务场景（如对话系统或代码助手）验证缓存策略的收益。
- 详情：[/20260615-20260624/README](/20260615-20260624/README)

### 精读区论文标签
1. [SwiftCache: Efficient LLM Serving for Multi-turn Conversations with Heterogeneous KV Cache Sharing](/20260615-20260624/2606.16135v1-swiftcache-efficient-llm-serving-for-multi-turn-conversations-with-heterogeneous-kv-cache-sharing)  
   标签：评分：9.0/10、query:cdn-ai-edge
   evidence：多轮对话中跨异构设备的KV缓存高效共享
2. [CacheWise: Understanding Workloads and Optimizing KVCache Management for Efficiently Serving LLM Coding Agents](/20260615-20260624/2606.16824v1-cachewise-understanding-workloads-and-optimizing-kvcache-management-for-efficiently-serving-llm-coding-agents)  
   标签：评分：9.0/10、query:cdn-ai-edge
   evidence：针对LLM编程代理的KVCache优化，结合前缀感知调度
3. [Distributed General-Purpose Agent Networks: Architecture, Key Mechanisms, and Prototypes](/20260615-20260624/2606.17368v1-distributed-general-purpose-agent-networks-architecture-key-mechanisms-and-prototypes)  
   标签：评分：9.0/10、query:agents-os
   evidence：边缘节点和个人设备上异构代理的分布式代理网络
4. [SAC: Disaggregated KV Cache System for Sparse Attention LLMs with CXL](/20260615-20260624/2606.19746v1-sac-disaggregated-kv-cache-system-for-sparse-attention-llms-with-cxl)  
   标签：评分：9.0/10、query:cdn-ai-edge
   evidence：针对稀疏注意力模型优化的解耦KV缓存系统，基于CXL互连
5. [UltraQuant: 4-bit KV Caching for Context-Heavy Agents](/20260615-20260624/2606.20474v2-ultraquant-4-bit-kv-caching-for-context-heavy-agents)  
   标签：评分：9.0/10、query:cdn-ai-edge
   evidence：面向上下文重型代理的4位KV缓存压缩
6. [Recency/Frequency Adaptive KV Caching for Large Language Model Serving](/20260615-20260624/2606.21238v1-recencyfrequency-adaptive-kv-caching-for-large-language-model-serving)  
   标签：评分：9.0/10、query:cdn-ai-edge
   evidence：基于最近性和频率的自适应KV缓存，用于LLM服务
7. [Does Mixture-of-Experts Actually Help Inference on Consumer and Edge Hardware? An Empirical Study](/20260615-20260624/2606.21428v1-does-mixture-of-experts-actually-help-inference-on-consumer-and-edge-hardware-an-empirical-study)  
   标签：评分：9.0/10、query:cdn-ai-edge
   evidence：MoE在消费级和边缘硬件上推理的实证研究
8. [Keyless Attention: Value-Space Routing and Value-Only Caching for Efficient Transformers](/20260615-20260624/2606.21848v1-keyless-attention-value-space-routing-and-value-only-caching-for-efficient-transformers)  
   标签：评分：9.0/10、query:cdn-ai-edge
   evidence：仅值KV缓存减少50%内存

### 速读区论文标签
1. [KVEraser: Learning to Steer KV Cache for Efficient Localized Context Erasing](/20260615-20260624/2606.17034v1-kveraser-learning-to-steer-kv-cache-for-efficient-localized-context-erasing)  
   标签：评分：8.0/10、query:cdn-ai-edge
   evidence：学习型KV缓存编辑方法，用于LLM中高效的局部上下文擦除
2. [Beyond Benchmarks: Continuous Edge Inference for Fine-Grained Roadside Perception](/20260615-20260624/2606.17241v1-beyond-benchmarks-continuous-edge-inference-for-fine-grained-roadside-perception)  
   标签：评分：8.0/10、query:cdn-ai-edge
   evidence：在Jetson Orin Nano上的持续边缘推理系统，用于道路感知
3. [RISE: Relay Inference and Online Scheduling for Efficient Edge-Device Collaborative Diffusion Model Services](/20260615-20260624/2606.17378v1-rise-relay-inference-and-online-scheduling-for-efficient-edge-device-collaborative-diffusion-model-services)  
   标签：评分：8.0/10、query:cdn-ai-edge
   evidence：边缘设备协同扩散模型服务的中继推理与在线调度
4. [AnchorKV: Safety-Aware KV Cache Compression via Soft Penalty with a Refusal Anchor](/20260615-20260624/2606.17872v1-anchorkv-safety-aware-kv-cache-compression-via-soft-penalty-with-a-refusal-anchor)  
   标签：评分：8.0/10、query:cdn-ai-edge
   evidence：安全感知的KV缓存压缩
5. [MonaVec: A Training-Free Embedded Vector Search Kernel for Edge and Offline AI Systems](/20260615-20260624/2606.19458v1-monavec-a-training-free-embedded-vector-search-kernel-for-edge-and-offline-ai-systems)  
   标签：评分：8.0/10、query:cdn-ai-edge
   evidence：为边缘和离线AI系统设计的嵌入式向量搜索内核
6. [Low-Energy Reduced RISC-V Instruction Subset Processor for Tsetlin Machine Inference at the Edge](/20260615-20260624/2606.19964v1-low-energy-reduced-risc-v-instruction-subset-processor-for-tsetlin-machine-inference-at-the-edge)  
   标签：评分：7.0/10、query:cdn-ai-edge
   evidence：面向边缘Tsetlin机器推理的低能耗RISC-V处理器
7. [Execution-State Capsules: Graph-Bound Execution-State Checkpoint and Restore for Low-Latency, Small-Batch, On-Device Physical-AI Serving](/20260615-20260624/2606.20537v1-execution-state-capsules-graph-bound-execution-state-checkpoint-and-restore-for-low-latency-small-batch-on-device-physical-ai-serving)  
   标签：评分：7.0/10、query:cdn-ai-edge
   evidence：执行状态胶囊实现低延迟设备端AI服务，扩展KV缓存至完整状态检查点
8. [A3C3: AI Algorithm and Accelerator Co-design, Co-search, and Co-generation](/20260615-20260624/2606.20869v1-a3c3-ai-algorithm-and-accelerator-co-design-co-search-and-co-generation)  
   标签：评分：7.0/10、query:agents-os
   evidence：面向异构平台的AI算法与加速器协同设计、搜索和生成
9. [WiSP: A Working-Set View of Mixture-of-Experts Serving on Extremely Low-Resource Hardware](/20260615-20260624/2606.21868v1-wisp-a-working-set-view-of-mixture-of-experts-serving-on-extremely-low-resource-hardware)  
   标签：评分：7.0/10、query:cdn-ai-edge
   evidence：低资源MoE推理中的KV缓存管理
10. [Agent-Assisted Side-Channel Attacks on Non-Prefix KV Cache in RAG](/20260615-20260624/2606.21842v1-agent-assisted-side-channel-attacks-on-non-prefix-kv-cache-in-rag)  
   标签：评分：6.0/10、query:cdn-ai-edge
   evidence：RAG中KV缓存的侧信道攻击
11. [Service-Cut Certificates for Aligned Eviction in Tiered Cache Networks](/20260615-20260624/2606.22270v1-service-cut-certificates-for-aligned-eviction-in-tiered-cache-networks)  
   标签：评分：6.0/10、query:cdn-ai-edge
   evidence：分层缓存网络中对齐驱逐的服务切割证书方法


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
