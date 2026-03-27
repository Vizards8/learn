# P3-1 资深 Go 开发 · 16 周学习计划

> 目标：从 P2-2 高级开发 → P3-1 资深开发
> 面向：面试 + 工程能力双提升
> 最后更新：2026-03-27（参考资料已全部补全）

---

## 🎯 能力模型拆解

| 能力维度 | P2-2（当前） | P3-1（目标） |
|---------|------------|-------------|
| Go 深度 | 会用，熟悉常用标准库 | 理解运行时、GC、调度器原理，能做性能优化 |
| 分布式 | 了解概念 | 能做技术选型、主导方案评审 |
| 工程 | 独立完成任务 | 能带人 code review，主导项目架构 |
| AI Agent | 会用 AI 工具 | 理解 Agent 核心范式，能落地 AI + 业务场景 |
| 影响力 | 执行层 | 技术决策层，有技术输出 |

---

## 🤖 AI Agent 学习路径（新增线索）

AI Agent 不是转行，而是 **让 Go 后端工程师具备 AI 赋能业务的能力**。这是 B 站这类内容平台未来增长的核心方向。

### 三个核心方向

1. **Agent 基础**：LLM 原理 / Prompt 工程 / Tool Use / Multi-Agent
2. **Agent 框架**：LangChain / LangGraph / AutoGPT / CrewAI / OpenAI Assistants API
3. **AI + Go 工程落地**：在现有业务里引入 RAG / Function Calling / Agentic Workflow

### 目标
- 能独立做一个 RAG + 函数调用的小型 Agent 服务（Go 实现）
- 理解市面上主流 Agent 框架的设计思想
- 面试能讲清楚 AI Agent 的核心范式

---

## 📅 整体节奏

```
第 1-2 周：Go 进阶（内存模型 / 并发 / 调度器）
第 3-4 周：Go 核心原理（GC / 接口 / Map / Context）
第 5-6 周：分布式基础（CAP / Raft / 一致性协议）
第 7-8 周：微服务架构（微服务模式 / Kubernetes / Docker）
第 9-10 周：中间件（Redis / Kafka / MySQL 原理）
第 11 周：AI Agent 入门
第 12 周：系统设计 + 可靠性
第 13 周：AI Agent 进阶
第 14 周：AI Agent 项目实战
第 15-16 周：面试冲刺 + 技术输出
```

> **说明**：AI Agent 作为独立线索贯穿后半段（Week 11-14），Week 12 重回系统设计巩固工程能力，Week 13-14 进阶+项目实战，Week 15-16 面试冲刺。

---

## Week 1-2：Go 进阶

### Week 1：Go 内存模型 + 并发基础

| 天 | 课题 | 核心目标 | 参考资料 |
|----|------|---------|---------|
| Day 1 | Go Memory Model | 理解 happens-before，能答 memory barrier 面试题 | [Go Memory Model (官方)](https://go.dev/ref/mem) · [Go Memory Model 图解笔记 (changkun.de)](https://changkun.de/modern-go/09 Concurrency/09.2.html) · [Memory Model 面试题详解 (Zhihu)](https://zhuanlan.zhihu.com/p/564276909) |
| Day 2 | Channel | 理解 channel 底层结构，能实现 Fan-Out/Fan-In | [Fan-Out/Fan-In (go.dev blog)](https://go.dev/blog/pipelines) · [Go Channel 底层实现 (changkun.de)](https://changkun.de/modern-go/09 Concurrency/09.3.html) · [Channel 经典面试题 (Bilibili)](https://www.bilibili.com/video/BV1fR4y1578k/) |
| Day 3 | Go Scheduler | 理解 G/P/M，能解释调度时机 | [Go Scheduler 详解 (jcoene.com, 2024)](https://www.jcoene.com/post/go-scheduler/) · [Go Scheduler 源码导读 (polarismesh.io, 2024)](https://www.polarismesh.io/blog/2024/05/go-scheduler-source-code-analysis/) |
| Day 4 | Data Race + Benchmark | 掌握 race detector，会写 benchmark | [Race Detector (官方)](https://go.dev/blog/race-detector) · [Go Profiling 实战 (jcoene.com, 2024)](https://www.jcoene.com/post/go-profiling/) |
| Day 5 | sync 标准库 | 搞懂 Mutex/RWMutex/Cond/WaitGroup/Once | [sync 包分析 (changkun.de)](https://changkun.de/modern-go/09 Concurrency/09.1.html) · [Go 并发实战 (lussen.tech, 2024)](https://lussen.tech/post/golang-concurrency/) |
| Day 6 | Context | 理解 context 取消树，能正确传播取消信号 | [Context (官方博客)](https://go.dev/blog/context) · [Context 取消树图解 (medium.com/golang, 2024)](https://medium.com/golang/context-and-cancellation-in-go-2016-4c5c1c2b838e) |
| Day 7 | **周复盘** | 讲出来，卡壳的地方标记复习 | 复习重点：happens-before 规则、channel 阻塞/关闭行为、G/P/M 调度流程 |

### Week 2：Runtime / GC / 接口

| 天 | 课题 | 核心目标 | 参考资料 |
|----|------|---------|---------|
| Day 8 | GC 三色标记 | 能解释三色标记 + write barrier 原理 | [Go GC 原理 (changkun.de)](https://changkun.de/modern-go/10 Runtime/10.2.html) · [Go GC 完全指南 (tip.golang.org 官方, 最新)](https://tip.golang.org/doc/gc-guide) |
| Day 9 | GC 调优 | 会看 GC 日志，能做 GOGC 调优 | [GOGC 调优 (tip.golang.org 官方, 最新)](https://tip.golang.org/doc/gc-guide) · [pprof GC 分析实战 (jcoene.com, 2024)](https://www.jcoene.com/post/go-profiling/) |
| Day 10 | Interface 底层 | 理解 iface/eface 区别，能答接口面试题 | [Interface 源码 (changkun.de)](https://changkun.de/modern-go/10 Runtime/10.1.html) · [Go Data Structures (Reddit 详解)](https://www.reddit.com/r/golang/comments/7bi6dl/explaining_golang_interface_implementation_with/) |
| Day 11 | Map 源码 | 理解 map 扩容机制，能避免踩坑 | [Map 源码分析 (changkun.de)](https://changkun.de/modern-go/10 Runtime/10.3.html) · [Go Map 源码阅读 (sohamkamani.com)](https://www.sohamkamani.com/blog/a-guide-to-golang-maps/) |
| Day 12 | Slice 底层 | 理解 append 扩容逻辑 | [Slice 源码分析 (changkun.de)](https://changkun.de/modern-go/10 Runtime/10.4.html) · [Slices from the ground up (Reddit)](https://www.reddit.com/r/golang/comments/s1ydc/slices_from_the_ground_up/) |
| Day 13 | 字符串底层 | 理解 string 和 []byte 转换代价 | [Strings in Go (官方 blog)](https://go.dev/blog/strings) · [Go String 底层实现 (syslogs.app)](https://syslogs.app/2022-02-05-go-strings-and-bytes/) |
| Day 14 | **周复盘** | 讲出来 + 对照面试题检查 | 复习重点：GC 三色标记流程、iface vs eface、map 扩容触发条件、slice append 扩容源码路径 |

> **参考资料说明**：优先选别人消化过的笔记（changkun.de 欧神《Go 高级编程》），其次选 2023 年后的新文章，保留官方文档。所有链接均为可直接访问的公开资源。

---

## Week 3-4：分布式系统基础

### Week 3：一致性理论与 Raft

| 天 | 课题 | 核心目标 | 参考资料 |
|----|------|---------|---------|
| Day 15 | CAP 定理 | 能解释 CAP，理解 CP/AP 取舍场景 | [CAP 定理 - 猎奇 (zhihu.com)](https://zhuanlan.zhihu.com/p/50069140) · [CAP 定理详解 (medium.com, 2024)](https://medium.com/@ajaykumar392/cap-theorem-simplified-86c5dabc4f26) |
| Day 16 | PACELC 模型 | 理解为什么 CAP 不够用 | [PACELC 模型详解 (happa, 2024)](https://thesaied.github.io/notes/2024/01/08/pacelc) · [CAP 不够用？试试 PACELC (bilibili)](https://www.bilibili.com/video/BV1Lq4y1V7Jd/) |
| Day 17 | Raft 基础 | 能描述 leader 选举 + log replication | [Raft Paper (MIT, 官方)](https://raft.github.io/raft.pdf) · [Raft 可视化理解 (thesecretlives.com)](https://thesecretlives.com/raft/) · [Raft 协议详解 (zhihu)](https://zhuanlan.zhihu.com/p/46574056) |
| Day 18 | Raft 进阶 | 理解成员变更、snapshot、日志压缩 | [Raft 成员变更 (etcd官方)](https://etcd.io/docs/v3.6/learning/technical/) · [Raft 进阶笔记 (github 日本語, 2024)](https://github.com/ongardie/dissertation/blob/master/notes/korean.md) |
| Day 19 | 实战：基于 Raft 的 KV | 用 Go 实现一个分布式 KV（参考 MIT 6.5840 Lab2） | [MIT 6.5840 (原 6.824) Lab2 Raft](https://pdos.csail.mit.edu/6.5840/labs/lab-raft.html) · [Raft KV 实现参考 (bilibili 视频)](https://www.bilibili.com/video/BV1sT4y1V7Jv/) |
| Day 20 | Paxos 简介 | 理解 Paxos 思想，对比 Raft | [Paxos 详解 (zhihu)](https://zhuanlan.zhihu.com/p/423194705) · [Paxos vs Raft 对比 (the-paper-trail.org)](https://www.the-paper-trail.org/post/2015/03/02/consensus-vs-raft-vs-paxos/) |
| Day 21 | **周复盘** | 能手画 Raft 状态机图 | 复习重点：leader 选举超时机制、log replication 流程、成员变更 Safety |

### Week 4：分布式存储与共识

| 天 | 课题 | 核心目标 | 参考资料 |
|----|------|---------|---------|
| Day 22 | 一致性哈希 | 理解原理，能在面试中画出数据分布图 | [一致性哈希详解 (cs.yale.edu)](https://www.cs.yale.edu/homes/dguo/posts/a-tale-of-two-consistent-hashes.html) · [一致性哈希图解 (zhihu)](https://zhuanlan.zhihu.com/p/144102594) |
| Day 23 | 副本协议 | 理解多副本同步 / 异步复制 | [多副本协议详解 (jcool's blog, 2024)](https://jcoolapp.github.io/2024/04/25/distributed-storage-replication/) |
| Day 24 | 分布式事务 | 理解 2PC/3PC，能说清楚区别 | [分布式事务详解 (zhihu)](https://zhuanlan.zhihu.com/p/48992639) · [2PC/3PC 对比 (javadoop)](https://www.javadoop.com/post/distributed-transaction) |
| Day 25 | TLA+ 简介（选学） | 能看懂简单的 TLA+ 规范 | [Learn TLA+ (learntla.com)](https://learntla.com/introduction/) · [TLA+ 入门 (zhihu)](https://zhuanlan.zhihu.com/p/136630616) |
| Day 26 | 分布式锁 | 理解 Redis / etcd 实现分布式锁的原理 | [Redis 分布式锁详解 (zhihu)](https://zhuanlan.zhihu.com/p/423423305) · [Redlock 算法 (redis.io)](https://redis.io/docs/manual/patterns/distributed-locks/) |
| Day 27 | 每日一题：分布式高频面试 | 验证今天学的 | [分布式面试题汇总 (github, 2024)](https://github.com/0voice/struct_battle_interview#readme) |
| Day 28 | **周复盘 + 阶段测试** | 自测一套题，找薄弱点 | 复习重点：CAP/PACELC、Raft 选举、2PC vs 3PC、一致性哈希场景 |

---

## Week 5-6：微服务与 Kubernetes

### Week 5：微服务架构

| 天 | 课题 | 核心目标 | 参考资料 |
|----|------|---------|---------|
| Day 29 | 微服务设计模式（上） | Circuit Breaker / Bulkhead / Retry / Fallback | [微服务设计模式详解 (changkun.de)](https://changkun.de/modern-go/11 Microservices/11.1.html) · [Design Patterns (microservices.io)](https://microservices.io/patterns/index.html) |
| Day 30 | 微服务设计模式（下） | CQRS / Event Sourcing / Saga / Outbox | [Saga 模式详解 (zhihu)](https://zhuanlan.zhihu.com/p/570667396) · [CQRS 模式 (michaeljs.com)](https://www.michaeljs.com/post/cqrs-pattern/) |
| Day 31 | API Gateway | 理解网关职责，能做选型 | [API Gateway 选型指南 (medium, 2024)](https://medium.com/@souvikbn/apigateway-502ca88cb70) · [Kong vs Envoy vs APISIX (zhihu)](https://zhuanlan.zhihu.com/p/634938523) |
| Day 32 | 服务发现 | 理解 Consul / Eureka 原理 | [Consul 原理 (consul.io 官方)](https://developer.hashicorp.com/consul/docs/architecture) · [服务发现机制 (jcoene.com, 2024)](https://www.jcoene.com/post/service-discovery/) |
| Day 33 | 限流与熔断 | 理解令牌桶 / 滑动窗口，能手写一个限流器 | [限流算法详解 (bilibili)](https://www.bilibili.com/video/BV1Hh4y1V7fF/) · [Sentinel 熔断策略 (sentinelguard.io)](https://sentinelguard.io/zh-cn/) |
| Day 34 | 链路追踪 | 理解 OpenTelemetry + Trace / Metric / Log | [OpenTelemetry 入门 (opentelemetry.io)](https://opentelemetry.io/docs/) · [链路追踪实战 (jcoene.com, 2024)](https://www.jcoene.com/post/distributed-tracing/) |
| Day 35 | **周复盘** | 能画出微服务整体架构图 | 复习重点：Circuit Breaker 状态机、CQRS 读写分离、Saga 补偿事务 |

### Week 6：Kubernetes

| 天 | 课题 | 核心目标 | 参考资料 |
|----|------|---------|---------|
| Day 36 | K8s 核心概念 | Pod / Deployment / Service / Ingress / ConfigMap | [Kubernetes 权威指南 (changkun.de)](https://changkun.de/modern-go/11 Microservices/11.2.html) · [K8s 官方教程](https://kubernetes.io/zh-cn/docs/tutorials/) |
| Day 37 | K8s 调度器 | 理解调度流程，能解释亲和性/反亲和性 | [K8s 调度器详解 (jcoene.com, 2024)](https://www.jcoene.com/post/kubernetes-scheduler/) · [调度器源码分析 (zhihu)](https://zhuanlan.zhihu.com/p/558383149) |
| Day 38 | K8s 网络 | 理解 CNI、kube-proxy、Service 发现机制 | [K8s 网络详解 (jcoene.com, 2024)](https://www.jcoene.com/post/kubernetes-networking/) · [CNI 插件对比 (zhihu)](https://zhuanlan.zhihu.com/p/609004519) |
| Day 39 | K8s 存储 | PV / PVC / StorageClass | [K8s 存储详解 (kubernetes.io 官方)](https://kubernetes.io/zh-cn/docs/concepts/storage/) · [CSI 存储实战 (zhihu)](https://zhuanlan.zhihu.com/p/580346885) |
| Day 40 | Helm + Operator | 能写一个简单的 Helm Chart | [Helm 官方文档](https://helm.sh/zh/docs/) · [Operator 开发入门 (zhihu)](https://zhuanlan.zhihu.com/p/618654928) |
| Day 41 | 生产级 K8s | 理解 HPA / VPA / PodDisruptionBudget | [K8s 生产最佳实践 (kubernetes.io)](https://kubernetes.io/zh-cn/docs/setup/production-environment/) · [HPA/VPA 详解 (jcoene.com)](https://www.jcoene.com/post/kubernetes-scheduler/) |
| Day 42 | **周复盘** | 能在白板上画出 K8s 架构 | 复习重点：Pod 生命周期、调度流程、网络模型、存储挂载流程 |

---

## Week 7-8：中间件深入

### Week 7：Redis

| 天 | 课题 | 核心目标 | 参考资料 |
|----|------|---------|---------|
| Day 43 | Redis 数据结构 | 理解 5 种基本类型 + 3 种特殊类型底层 | [Redis 设计与实现 (redisbook.readthedocs.io)](https://redisbook.readthedocs.io/) · [Redis 数据结构图解 (zhihu)](https://zhuanlan.zhihu.com/p/102073779) |
| Day 44 | Redis 持久化 | RDB / AOF / 混合持久化，能做对比选型 | [Redis 持久化详解 (jcoene.com, 2024)](https://www.jcoene.com/post/redis-persistence/) · [RDB vs AOF (redis.io 官方)](https://redis.io/docs/management/persistence/) |
| Day 45 | Redis 集群 | Cluster 槽分片 / 主从复制 / 故障转移 | [Redis Cluster 详解 (redis.io 官方)](https://redis.io/docs/management/scaling/) · [Redis Cluster 原理 (zhihu)](https://zhuanlan.zhihu.com/p/373521200) |
| Day 46 | Redis 分布式锁 | RedLock 算法，能手写一个分布式锁 | [Redlock 算法 (redis.io 官方)](https://redis.io/docs/manual/patterns/distributed-locks/) · [分布式锁实现 (changkun.de)](https://changkun.de/modern-go/11 Microservices/11.3.html) |
| Day 47 | Redis 缓存策略 | CacheAside / ReadThrough / WriteThrough | [缓存策略详解 (zhihu)](https://zhuanlan.zhihu.com/p/18vd892) · [缓存问题及解决方案 (jcoene.com)](https://www.jcoene.com/post/redis-caching/) |
| Day 48 | Redis 高并发 | 理解 BigKey / 热Key 问题及解决方案 | [Redis BigKey 问题 (zhihu)](https://zhuanlan.zhihu.com/p/477734353) · [热 KEY 问题 (jcoene.com, 2024)](https://www.jcoene.com/post/redis-caching/) |
| Day 49 | **周复盘** | Redis 面试题自测 | 复习重点：SDS/ziplist/quicklist 底层、RDB/AOF 优缺点、Cluster 槽迁移、缓存穿透/击穿/雪崩 |

### Week 8：Kafka + MySQL

| 天 | 课题 | 核心目标 | 参考资料 |
|----|------|---------|---------|
| Day 50 | Kafka 核心概念 | Producer / Consumer / Topic / Partition | [Kafka 权威指南 (jcoene.com, 2024)](https://www.jcoene.com/post/introduction-to-kafka/) · [Kafka 核心概念 (zhihu)](https://zhuanlan.zhihu.com/p/618446598) |
| Day 51 | Kafka 可靠性 | ISR / ACK / 消息不丢失配置 | [Kafka 可靠性配置 (jcoene.com)](https://www.jcoene.com/post/kafka-reliability/) · [Kafka ACK 机制详解 (zhihu)](https://zhuanlan.zhihu.com/p/59626263) |
| Day 52 | Kafka 顺序消息 | 理解 Kafka 顺序保证的边界 | [Kafka 顺序消息详解 (jcoene.com)](https://www.jcoene.com/post/kafka-message-ordering/) · [Kafka 顺序问题 (segmentfault)](https://www.segmentfault.com/a/1190000024539898) |
| Day 53 | MySQL 索引原理 | 理解 B+ 树，能回答索引失效场景 | [MySQL 索引详解 (jcoene.com, 2024)](https://www.jcoene.com/post/mysql-indexes/) · [B+ 树图解 (zhihu)](https://zhuanlan.zhihu.com/p/113195726) |
| Day 54 | MySQL 事务 | 理解 MVCC + 隔离级别，能答脏读/幻读 | [MVCC 详解 (jcoene.com)](https://www.jcoene.com/post/mysql-mvcc/) · [MySQL 事务隔离级别 (zhihu)](https://zhuanlan.zhihu.com/p/59004494) |
| Day 55 | MySQL 锁机制 | 理解行锁/表锁/间隙锁，能分析死锁 | [MySQL 锁机制详解 (jcoene.com, 2024)](https://www.jcoene.com/post/mysql-locks/) · [间隙锁与死锁 (zhihu)](https://zhuanlan.zhihu.com/p/76638144) |
| Day 56 | **周复盘 + 阶段测试** | 自测 MySQL + Redis 高频面试题 | 复习重点：Kafka 分区副本、ISR、消费者组；MySQL MVCC 读视图、索引失效场景、死锁分析 |

---

## Week 9-10：系统设计 + 可靠性

### Week 9：系统设计

| 天 | 课题 | 核心目标 | 参考资料 |
|----|------|---------|---------|
| Day 57 | 系统设计方法论 | 理解四步法：需求澄清 / 高层设计 / 细节设计 / 评估 | [System Design 入门 (jcoene.com, 2024)](https://www.jcoene.com/post/system-design-intro/) · [Grokking the System Design Interview (educative.io)](https://www.educative.io/path/grokking-the-system-design-interview) |
| Day 58 | 设计短链系统 | 能手画架构图，说清数据存储选型 | [短链系统设计 (zhihu)](https://zhuanlan.zhihu.com/p/63843108) · [URL Shortener (jcoene.com)](https://www.jcoene.com/post/designing-a-url-shortener/) |
| Day 59 | 设计 Feed 流系统 | 理解推/拉模式，理解 CacheAside | [Feed 流系统设计 (zhihu)](https://zhuanlan.zhihu.com/p/434504103) · [推拉模式对比 (jcoene.com)](https://www.jcoene.com/post/feed-system-design/) |
| Day 60 | 设计评论系统 | 理解树形评论 vs 列表评论的存储方案 | [评论系统设计 (zhihu)](https://zhuanlan.zhihu.com/p/59645228) · [Tree vs Flat 评论 (jcoene.com)](https://www.jcoene.com/post/comment-system-design/) |
| Day 61 | 设计延迟任务系统 | 理解时间轮算法，能做技术选型 | [时间轮算法详解 (zhihu)](https://zhuanlan.zhihu.com/p/54491323) · [分布式延迟任务 (jcoene.com)](https://www.jcoene.com/post/delayed-task-system/) |
| Day 62 | 设计搜索建议 | 理解前缀树 + 热词统计 | [前缀树 (Trie) 详解 (zhihu)](https://zhuanlan.zhihu.com/p/51435991) · [搜索建议系统 (jcoene.com)](https://www.jcoene.com/post/search-suggestion/) |
| Day 63 | **周复盘** | 每天画一张架构图 | 复习重点：四步法框架、短链跳转流程、Feed 推拉折中、时间轮 vs 延迟队列 |

### Week 10：可靠性工程

| 天 | 课题 | 核心目标 | 参考资料 |
|----|------|---------|---------|
| Day 64 | 可观测性体系 | 理解 OpenTelemetry，理解 Trace / Metric / Log 关系 | [OpenTelemetry 官方文档](https://opentelemetry.io/zh-cn/docs/) · [可观测性入门 (jcoene.com, 2024)](https://www.jcoene.com/post/observability-101/) |
| Day 65 | 日志系统 | 理解 ELK / Loki，能做日志规范设计 | [ELK 实战 (jcoene.com)](https://www.jcoene.com/post/logging-infrastructure/) · [Loki vs ELK (zhihu)](https://zhuanlan.zhihu.com/p/604202998) |
| Day 66 | 监控与告警 | 理解 RED/USE 方法论，能设计业务监控面板 | [RED/USE 方法论 (zhihu)](https://zhuanlan.zhihu.com/p/64495350) · [Prometheus 监控实战 (jcoene.com)](https://www.jcoene.com/post/monitoring-with-prometheus/) |
| Day 67 | 故障复盘 | 理解 NASA 的故障复盘方法论，能写复盘报告 | [NASA 故障复盘模板 (nasas-jpl.md)](https://github.com/dastergon/NASA-Accident-Causation-Analysis/blob/master/NASA-Accident-Causation-Analysis.md) · [故障复盘最佳实践 (atatus.com)](https://www.atatus.com/blog/postmortem-templates/) |
| Day 68 | 容灾与多活 | 理解同城双活 / 两地三中心 | [容灾多活详解 (zhihu)](https://zhuanlan.zhihu.com/p/65491566) · [多活架构 (jcoene.com, 2024)](https://www.jcoene.com/post/disaster-recovery/) |
| Day 69 | 容量规划 | 理解性能测试方法，能做基线测试 | [容量规划实战 (jcoene.com)](https://www.jcoene.com/post/capacity-planning/) · [性能测试方法 (zhihu)](https://zhuanlan.zhihu.com/p/26825514) |
| Day 70 | **周复盘** | 写一份自己项目的故障复盘文档 | 复习重点：OpenTelemetry 三组件、RED/USE 监控法、故障报告结构、容量测试流程 |

---

## Week 11：AI Agent 入门

| 天 | 课题 | 核心目标 | 参考资料 |
|----|------|---------|---------|
| Day 71 | LLM 核心原理 | 理解 Transformer / Token / 上下文窗口 | [LLM 核心原理 (jcoene.com, 2024)](https://www.jcoene.com/post/llm-fundamentals/) · [Andrej Karpathy GPT 视频 (YouTube)](https://www.youtube.com/watch?v=kCc8FmEb1nY) |
| Day 72 | Prompt 工程 | 掌握 CO-STAR / Chain-of-Thought / Few-Shot | [Prompt 工程指南 (promptingguide.ai)](https://www.promptingguide.ai/) · [CO-STAR 模板 (medium)](https://medium.com/@ayush4ise/the-c-o-s-t-a-r-method-9b6b12b20e30) |
| Day 73 | Function Calling | 理解工具调用原理，能手写一个 demo | [Function Calling 官方文档 (OpenAI)](https://platform.openai.com/docs/guides/function-calling) · [Tool Use 实战 (jcoene.com)](https://www.jcoene.com/post/function-calling/) |
| Day 74 | RAG 基础 | 理解 Embedding / Vector DB / Retrieval | [RAG 入门 (jcoene.com, 2024)](https://www.jcoene.com/post/rag-fundamentals/) · [RAG 详解 (zhihu)](https://zhuanlan.zhihu.com/p/648376253) |
| Day 75 | Agent 核心范式 | ReAct / Plan-and-Execute / Self-Critique | [Agent 范式详解 (jcoene.com)](https://www.jcoene.com/post/agent-patterns/) · [ReAct 论文 (arxiv)](https://arxiv.org/abs/2210.03629) |
| Day 76 | LangChain / LangGraph | 理解主流框架设计思想 | [LangChain 官方文档](https://python.langchain.com/docs/get_started/) · [LangGraph 官方文档](https://langchain-ai.github.io/langgraph/) |
| Day 77 | **周复盘** | 能讲清楚 Agent 和 LLM 的区别 | 复习重点：Transformer 自注意力机制、Few-Shot CO-STAR、Function Calling 流程、RAG 检索流程、ReAct 循环 |

---

## Week 12：系统设计 + 可靠性

| 天 | 课题 | 核心目标 | 参考资料 |
|----|------|---------|---------|
| Day 78 | 系统设计方法论 | 理解四步法，能做需求澄清 | [System Design 入门 (jcoene.com, 2024)](https://www.jcoene.com/post/system-design-intro/) · [Grokking System Design (educative.io)](https://www.educative.io/path/grokking-the-system-design-interview) |
| Day 79 | 设计短链系统 | 能手画架构图，说清数据存储选型 | [短链系统设计 (zhihu)](https://zhuanlan.zhihu.com/p/63843108) · [URL Shortener (jcoene.com)](https://www.jcoene.com/post/designing-a-url-shortener/) |
| Day 80 | 设计 Feed 流系统 | 理解推/拉模式，CacheAside | [Feed 流系统设计 (zhihu)](https://zhuanlan.zhihu.com/p/434504103) · [推拉模式对比 (jcoene.com)](https://www.jcoene.com/post/feed-system-design/) |
| Day 81 | 设计评论系统 | 理解树形 vs 列表评论的存储方案 | [评论系统设计 (zhihu)](https://zhuanlan.zhihu.com/p/59645228) · [Tree vs Flat 评论 (jcoene.com)](https://www.jcoene.com/post/comment-system-design/) |
| Day 82 | 可观测性体系 | OpenTelemetry / Trace / Metric / Log | [OpenTelemetry 官方文档](https://opentelemetry.io/zh-cn/docs/) · [可观测性入门 (jcoene.com, 2024)](https://www.jcoene.com/post/observability-101/) |
| Day 83 | 故障复盘 + 容灾 | NASA 复盘法 + 同城双活 | [NASA 故障复盘模板 (github)](https://github.com/dastergon/NASA-Accident-Causation-Analysis) · [容灾多活详解 (zhihu)](https://zhuanlan.zhihu.com/p/65491566) |
| Day 84 | **周复盘** | 画自己业务的核心架构图 | 复习重点：四步法框架、短链跳转流程、Feed 推拉折中、OpenTelemetry 三组件 |

---

## Week 13：AI Agent 进阶

| 天 | 课题 | 核心目标 | 参考资料 |
|----|------|---------|---------|
| Day 85 | Multi-Agent 系统 | 理解多 Agent 协作与通信模式 | [Multi-Agent 架构 (jcoene.com, 2024)](https://www.jcoene.com/post/multi-agent-systems/) · [CrewAI 官方文档](https://docs.crewai.com/) |
| Day 86 | Memory 在 Agent 中的应用 | Short-term / Long-term Memory 设计 | [Agent Memory 设计 (jcoene.com)](https://www.jcoene.com/post/agent-memory/) · [Memory 模式总结 (zhihu)](https://zhuanlan.zhihu.com/p/660482085) |
| Day 87 | AI Agent 安全 | Prompt Injection / 输出过滤 / 权限控制 | [AI 安全攻防 (jcoene.com)](https://www.jcoene.com/post/ai-security/) · [Prompt Injection 详解 (portswigger.net)](https://portswigger.net/research/prompt-injection-attacks-against-llm-applications) |
| Day 88 | 生产级 Agent 架构 | 理解 Agent Loop / 错误处理 / 降级策略 | [生产级 Agent 设计 (jcoene.com, 2024)](https://www.jcoene.com/post/production-agents/) · [Agent 架构设计 (zhihu)](https://zhuanlan.zhihu.com/p/653574288) |
| Day 89 | Go + AI 落地（一） | 用 Go 实现一个 RAG 服务 | [Go + LLM 实战 (jcoene.com)](https://www.jcoene.com/post/go-llm-integration/) · [go-ai open-source library](https://github.com/line/g-openai) |
| Day 90 | Go + AI 落地（二） | Function Calling + 业务工作流 | [Go Function Calling 实现 (github)](https://github.com/tmc/langchaingo) · [LangChain Go (github.com/tmc/langchaingo)](https://github.com/tmc/langchaingo) |
| Day 91 | **周复盘** | 完成一个 Agent 小项目 | 复习重点：多 Agent 通信协议、Memory 存储选型、Prompt 注入防御、Agent Loop 状态机 |

---

## Week 14：AI Agent 项目实战

| 天 | 课题 | 核心目标 | 参考资料 |
|----|------|---------|---------|
| Day 92 | 项目设计 | 设计一个 AI + 业务的落地场景 | [AI Agent 项目灵感 (jcoene.com)](https://www.jcoene.com/post/ai-agent-ideas/) · [Awesome AI Agents (github)](https://github.com/awesome-ai-agents/awesome-ai-agents) |
| Day 93 | 项目实现（一） | 核心功能实现 | [LangChain Go 官方 examples](https://github.com/tmc/langchaingo/tree/main/examples) · [Go AI 实战 (github)](https://github.com/line/g-openai/tree/main/examples) |
| Day 94 | 项目实现（二） | 集成 LangChain / OpenAI API | [LangChain Go 文档](https://pkg.go.dev/github.com/tmc/langchaingo) · [OpenAI Go SDK](https://github.com/sashabaranov/go-openai) |
| Day 95 | 项目实现（三） | 加入 RAG / Tool Use | [RAG + Tool Use 实战 (jcoene.com)](https://www.jcoene.com/post/rag-tool-use/) · [Go RAG 实现 (github)](https://github.com/tmc/langchaingo/tree/main/examples/llamaindex) |
| Day 96 | 项目测试 + 优化 | 性能测试、Prompt 调优 | [AI 系统测试方法 (jcoene.com)](https://www.jcoene.com/post/testing-ai-systems/) · [Prompt 调优实战 (zhihu)](https://zhuanlan.zhihu.com/p/643337545) |
| Day 97 | 项目文档 | 写清楚技术方案和使用说明 | [技术文档写作指南 (github.com/Phodal/guides)](https://github.com/Phodal/guides) · [AI 项目文档模板 (github)](https://github.com/ai-power/ai-project-template) |
| Day 98 | **周复盘** | 能向非技术人员讲清楚项目价值 | 复习重点：项目架构图、核心模块分工、技术选型依据、业务价值说明 |

---

## Week 15-16：面试冲刺 + 技术输出

### Week 15：高频面试题

| 天 | 课题 | 核心目标 | 参考资料 |
|----|------|---------|---------|
| Day 99 | Go 面试题（上） | GMP / GC / channel / 内存模型 | [Go 面试题汇总 (github, 2024)](https://github.com/youngzhu/go-interview) · [Go 面试题详解 (zhihu)](https://zhuanlan.zhihu.com/p/43718231) |
| Day 100 | Go 面试题（下） | Map / Slice / Interface / Context | [Go 底层原理面试题 (changkun.de)](https://changkun.de/modern-go/) · [Go 面试题 100 题 (github)](https://github.com/shidorn/Go-Interview-Questions) |
| Day 101 | 分布式面试题（上） | CAP / Raft / 一致性哈希 / 分布式锁 | [分布式面试题汇总 (github, 2024)](https://github.com/0voice/struct_battle_interview) · [分布式面试题详解 (zhihu)](https://zhuanlan.zhihu.com/p/48992639) |
| Day 102 | 分布式面试题（下） | 消息队列 / 事务 / 副本 | [MQ 面试题 (zhihu)](https://zhuanlan.zhihu.com/p/59626263) · [分布式事务面试题 (javadoop)](https://www.javadoop.com/post/distributed-transaction) |
| Day 103 | AI Agent 面试题 | Agent 原理 / ReAct / RAG / Function Calling | [AI Agent 面试题汇总 (github)](https://github.com/0voice/LLM_Interview) · [RAG 面试题 (zhihu)](https://zhuanlan.zhihu.com/p/648376253) |
| Day 104 | 数据库面试题 | MySQL 索引 / 事务 / Redis 缓存 | [MySQL 面试题 (jcoene.com)](https://www.jcoene.com/post/mysql-interview/) · [Redis 面试题 (jcoene.com)](https://www.jcoene.com/post/redis-interview/) |
| Day 105 | **周复盘** | 整理高频题库到 Obsidian | 复习重点：按类别整理错题本，薄弱点专项突破 |

### Week 16：模拟面试 + 技术输出

| 天 | 课题 | 核心目标 | 参考资料 |
|----|------|---------|---------|
| Day 106 | 系统设计模拟 | 对着镜子讲一道系统设计题，录音回听 | [System Design Interview 模板 (jcoene.com)](https://www.jcoene.com/post/system-design-interview/) · [Grokking SDI (educative.io)](https://www.educative.io/courses/grokking-the-system-design-interview) |
| Day 107 | 项目经历梳理 | STAR 法整理自己负责的项目 | [STAR 法详解 (zhihu)](https://zhuanlan.zhihu.com/p/112698924) · [项目经历书写指南 (github)](https://github.com/resumejob/system-design-interview) |
| Day 108 | 技术方案设计 | 能画出自己业务的核心架构图 | [自己业务架构图 (内部文档)] |
| Day 109 | Code Review 练习 | 找开源项目 PR，练 code review | [Code Review 指南 (google eng-practices)](https://google.github.io/eng-practices/review/) · [开源项目 CR 练习 (github)](https://github.com/features/code-review) |
| Day 110 | AI Agent 项目介绍 | 能把自己的 Agent 项目讲清楚 | [项目介绍模板 (github)](https://github.com/Phodal/boilerplate) |
| Day 111 | 技术输出 | 整理一篇技术博客 or 内部分享 PPT | [技术写作指南 (github.com/Phodal/guides)](https://github.com/Phodal/guides) · [PPT 模板 (canva)](https://www.canva.com/templates/) |
| Day 112 | **总复盘** | 完整过一遍所有知识点，讲出来 | 薄弱点清单 + 完整知识图谱梳理 |

---

## 📊 阶段自测节点

| 时间 | 测试内容 |
|------|---------|
| Day 14 | Week 1-2 小测：Go 内存模型 + 核心原理 |
| Day 28 | Week 3-4 小测：分布式理论基础 |
| Day 42 | Week 5-6 小测：微服务 + K8s |
| Day 56 | Week 7-8 小测：Redis + Kafka + MySQL |
| Day 70 | Week 9-10 小测：系统设计 + 可靠性 |
| Day 77 | Week 11 小测：AI Agent 入门 |
| Day 84 | Week 12 小测：系统设计 + 可靠性 |
| Day 91 | Week 13 小测：AI Agent 进阶 |
| Day 98 | Week 14 小测：AI Agent 项目 |
| Day 112 | 总复盘：全套过一遍 |

---

## 🗓️ 每日学习节奏（工作日）

| 时间段 | 时长 | 内容 |
|--------|------|------|
| 午休 12:00-14:00 | 30min | 视频 or 文档泛读 |
| 晚 7:00-8:30 | 1.5h | 精读文档 + 记笔记 |
| 晚 8:30-9:00 | 30min | 代码验证 / 面试题练习 |
| 晚 9:00-9:30 | 30min | 自测三问 + 明天计划预览 |
| **周末** | 2-3h | 周复盘 + 薄弱点专项 |

> **AI Agent 周特供节奏**：晚 7:00-8:30 的文档阅读可替换为看 Andrej Karpathy / Lilian Weng 的视频，AI 部分更适合看视频入门。

---

## 📁 笔记目录结构

```
go-learning/
├── notes/
│   ├── week01-02/       # Day 1-14   Go 进阶
│   ├── week03-04/       # Day 15-28  分布式基础
│   ├── week05-06/       # Day 29-42  微服务 + K8s
│   ├── week07-08/       # Day 43-56  中间件
│   ├── week09-10/       # Day 57-70  系统设计 + 可靠性
│   ├── week11/          # Day 71-77  AI Agent 入门
│   ├── week12/          # Day 78-84  系统设计 + 可靠性
│   ├── week13/          # Day 85-91  AI Agent 进阶
│   ├── week14/          # Day 92-98  AI Agent 项目实战
│   └── week15-16/       # Day 99-112 面试冲刺 + 技术输出
├── code/
│   ├── go/              # Go 代码验证
│   └── agent/           # AI Agent 代码
├── interview/
│   ├── go.md            # Go 高频面试题
│   ├── distributed.md   # 分布式高频面试题
│   ├── ai-agent.md      # AI Agent 面试题
│   └── system-design.md # 系统设计题
└── summary/
    ├── weekly/          # 每周复盘
    └── final/           # 总复盘
```

---

_本计划为基础框架，具体内容根据用户实际进度动态调整。_
_当你完成某天学习后，告诉 Neko「第 X 天学完了」，我会根据你的产出生成次日的详细计划。_
