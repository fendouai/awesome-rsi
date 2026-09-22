[← 上一章：分类与技术栈](02-taxonomy.md) · [返回目录](../README.md) · [下一章：统一架构与 Evaluator →](04-architecture.md)

---

# 03 · 技术发展史

> RSI 的发展可以粗略划分为五个阶段，每一步都在扩大「被改进的对象」。

---

## 阶段总览

```text
① 理论 RSI（1980s–2000s）
     改：程序（形式化证明）
        ↓
② Self-Refinement（2022–2023）
     改：Output
        ↓
③ Prompt / Memory Self-Improvement（2023–2024）
     改：Solver（持久化经验）
        ↓
④ Harness RSI（2025–2026）
     改：Agent 脚手架
        ↓
⑤ AI4AI / Automated AI Research（2026–）
     改：制造 Agent 与 Model 的整个过程
```

---

## 第一阶段 · 理论 RSI（1980s–2000s）

核心思想：Meta-Learning、Self-Modifying Program、Learning to Learn、Gödel Machine。主要回答「程序能否安全修改自身」。详见 [01 · 理论基础](01-foundations.md)。

---

## 第二阶段 · Self-Refinement（2022–2023）

LLM 出现后，最早大规模成熟的是：

```text
Generate → Critique → Rewrite
```

典型技术：Self-Refine、Reflexion、Self-Critique、Debate。

这一阶段修改的是 **Output**，而不是 **System**，因此更准确地说属于 **Bounded Self-Refinement**。

---

## 第三阶段 · Prompt / Memory Self-Improvement（2023–2024）

系统开始把经验沉淀为 Prompt、Rules、Skills、Memory、Experience。系统从：

```text
Improve Answer
```

变成：

```text
Improve Solver
```

这一步非常重要：Improvement 开始成为 **Persistent**。

---

## 第四阶段 · Harness RSI（2025–2026）

一个明显的趋势出现：**AI System 的能力并不仅仅由 Model 决定。** Agent 系统由以下部分共同构成：

```text
Model + System Prompt + Memory + Skills + Tools
+ Context Management + Agent Loop + Subagents + Completion Logic
```

这些非权重部分通常被统称为 **Harness / Scaffold**。系统不再重训参数，而是直接修改 Agent Loop、Tool Strategy、Context Strategy、Skill、Prompt、Memory、Observation Processing。这是目前最现实、成本最低的 RSI 路径之一。

详见 [06 · Harness 与 Memory RSI](06-harness-rsi.md)。

---

## 第五阶段 · AI4AI 与 Automated AI Research（2026–）

```text
AI solves tasks
↓
AI improves agents
↓
AI improves training data
↓
AI improves models
↓
AI designs training algorithms
↓
AI conducts AI research
```

RSI 的研究对象从 **Agent** 扩展到 **制造 Agent 和 Model 的整个过程**，即 **AI4AI**。

---

## 关键里程碑时间轴

从理论到可跑系统，四个阶段、八个里程碑：

| 时间 | 事件 | 类型 | 自我改进对象 |
|---|---|---|---|
| 2003 / 2007 | Gödel Machine（Schmidhuber） | 理论 | 可证明的自我改进 |
| 2023-09 | STOP（Microsoft） | RSI 系统 | Improver 改进 Improver |
| 2024-06 | RE-Bench（METR） | Benchmark | AI R&D 能力 |
| 2024-07 | ADAS（ICLR 2025） | RSI 系统 | Meta Agent Search：自动设计 agent 架构 |
| 2024-10 | Gödel Agent（ACL 2025） | RSI 系统 | 自身逻辑（monkey patch） |
| 2024-10 | MLE-bench（OpenAI） | Benchmark | ML 工程能力 |
| 2025 | SICA | RSI 系统 | coding agent 自身 codebase |
| 2025-05 | Darwin Gödel Machine | RSI 系统 | agent code + open-ended 进化 |
| 2025-06 | SEAL | RSI 系统 | 模型权重（self-edit + fine-tune） |
| 2025-10 | Agent0（ICML'26 & COLM'26） | RSI 系统 | curriculum ↔ solver 共进化 |
| 2026-06 | NatureBench | Benchmark | 科学发现能力 |
| 2026-07 | OpenRSI / OpenMLE / Frontis-MA1 | RSI 系统 | AI4AI：改进「改进 ML」的过程 |

> **关键观察**：Benchmark 每升一级（软件工程 → ML 工程 → 科学发现），就催生一代更强的 RSI 系统——「环境定义能力」。
>
> **顺序修正**：ADAS（2024-08）早于 Gödel Agent（2024-10）；Gödel Agent 对比的 MAS 基线正来自 ADAS。

---

## 技术变迁脉络

核心主线是 **「改什么」的跃迁**：

```text
改 prompt / workflow（脚手架层）
   → 改 agent 架构（元搜索）
   → 改自身代码（运行时 / codebase）
   → 进化式改自身代码（archive + selection）
   → 改模型权重（self-edit → fine-tune）
   → 训练一个专门的「改进器」（AI4AI）
```

| 阶段 | 代表 | 改什么 | 质变点 |
|---|---|---|---|
| **① Scaffold 层** | STOP → ADAS → Gödel Agent → SICA → DGM | prompt / 架构 / 代码 | 从「改答案」到「改系统」，再到开放式进化 |
| **② 权重层** | SEAL → Agent0 | 模型权重 / curriculum | 首次触碰 weight-level；curriculum 开始进化（防 overfitting） |
| **③ AI4AI** | OpenRSI / Frontis-MA1 | 「改进 ML」这个过程 | 学习与进化合一：训练 + 搜索同一循环 |

三个转折点：

1. **STOP → ADAS**：被优化对象从「解决方案」变成「agent 架构 / 优化器本身」。
2. **Gödel Agent → DGM**：从「单链自我修订」变成「archive + selection + mutation」的群体进化。
3. **SEAL → OpenRSI**：从「改脚手架」→「改权重」→「训练 meta-evolution model」；OpenRSI 训练数据对 eval benchmark 去重。

---

## 未来阶段（推演）

以下不是确定时间预测，而是一条值得跟踪的 **Capability Dependency Graph**——每一层都依赖前一层成熟：

```text
2024  Self-Refinement
   ↓
2025  Agent / Prompt / Skill Evolution
   ↓
2026  Harness + Data RSI
   ↓
2027  AI Research Automation
   ↓
2028  Model + Harness Co-Evolution
   ↓
2029+ Algorithm Discovery → Meta-RSI
```

详见 [14 · 瓶颈与路线图](14-outlook.md)。

---

[← 上一章：分类与技术栈](02-taxonomy.md) · [返回目录](../README.md) · [下一章：统一架构与 Evaluator →](04-architecture.md)
