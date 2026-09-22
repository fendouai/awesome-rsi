[← 上一章：数据生态](05-data.md) · [返回目录](../README.md) · [下一章：Data RSI →](07-data-rsi.md)

---

# 06 · Harness 与 Memory RSI

> 不重新训练几百亿甚至几千亿参数，而是直接修改 Agent 的脚手架与记忆。这是目前最现实、成本最低的 RSI 路径。

---

## 1. 什么是 Harness RSI

Agent 系统由以下部分共同构成：

```text
Model + System Prompt + Memory + Skills + Tools
+ Context Management + Agent Loop + Subagents + Completion Logic
```

这些非权重部分统称 **Harness / Scaffold**。Harness RSI 直接修改其中的：

- Agent Loop
- Tool Strategy
- Context Strategy
- Skill
- Prompt
- Memory
- Observation Processing

---

## 2. 早期 Scaffold 层自改进（2023–2025）

这一代系统验证了「AI 修改自己的脚手架」的可行性：

- [STOP](https://github.com/microsoft/stop) — Self-Taught Optimizer：让优化程序递归优化自己。底层 LLM 未变，作者自述非 full RSI。（Microsoft，2023）
- [ADAS](https://github.com/ShengranHu/ADAS) — Automated Design of Agentic Systems：Meta Agent 自动搜索并设计 agent 架构；Gödel Agent 中 **Meta Agent Search（MAS）基线**的来源。（ICLR 2025）
- [Gödel Agent](https://github.com/Arvid-pku/Godel_Agent) — Self-Referential Agent：运行时用 monkey patch 读写自身源码；Game of 24 从 4% → 78%。（ACL 2025，arXiv 2410.04444）
- [SICA](https://github.com/MaximeRobeyns/self_improving_coding_agent) — Self-Improving Coding Agent：评估 → 存档 → 改自身 codebase → 下一轮，适合 trajectory 研究。（2025，[workshop paper](https://openreview.net/pdf?id=rShJCyLsOr)）
- [Darwin Gödel Machine (DGM)](https://github.com/jennyzzt/dgm) — 开放进化：archive + selection + mutation + evaluation；SWE-bench 20% → 50%、Polyglot 14.2% → 30.7%。（arXiv 2505.22954）

成绩明细见 [11 · Benchmark 生态](11-benchmarks.md)。

---

## 3. ModularRSI：模块化 Harness 进化

Harness RSI 的困难之一是：如果整个 Agent 一次性发生变化，很难确定提升来自哪里。

因此 ModularRSI 把 Harness 拆成多个模块：

```text
Agent Loop
Tool Use
Observation Management
Context Management
Task Completion Detection
```

核心思路不是「Rewrite everything」，而是：

```text
Compare
  Successful Trajectory
vs
  Failed Trajectory
        ↓
Find systematic defect
        ↓
Modify only affected module
```

这实际上解决的是 **Credit Assignment**，也标志着 RSI 从 **Monolithic Evolution** 向 **Modular Evolution** 转变。

---

## 4. Memory RSI：Recuris

[Recuris](https://github.com/Gen-Verse/Recuris) 采取了另一条路线：

> 模型不变，Prompt 不变，进化 Memory。

其公开实现把 Skill Memory 建模为多个结构化组件，并让 Meta-Agent 根据 execution trace 定位失败属于哪个 memory component。

修改完成后，通过 **deterministic validation gate** 判断修改是否保留，而不是让模型自己投票决定。

另一个重要特点是：

> evolved memory 可以跨模型迁移。

这意味着 **Experience 可能成为独立于 Model 的资产**。

---

## 5. 为什么 Harness RSI 会先爆发

原因主要有四个：

### 1. 成本低

改 Prompt / Skill / Loop 几乎不需要 GPU Training。

### 2. Feedback 快

```text
Edit → Run → Evaluate
```

几分钟完成一次实验。

### 3. Verifier 丰富

Software / Agent Task 很容易获得 unit test、benchmark、compiler、execution result。

### 4. 容易 Rollback

Harness 本质上是 Software，天然支持 git diff、versioning、branch、rollback。

> **Harness 很可能成为 RSI 的第一个大规模产业落地点。**

---

## 6. 相关基础设施

- [OpenRSI / OpenMLE](https://github.com/FrontisAI/OpenRSI) 提供完整 AI4AI 技术栈，详见 [09 · Algorithm RSI](09-algorithm-rsi.md)。
- RSI-Harness 等长期跟踪项目见 [12 · 系统与项目地图](12-systems.md)。

---

[← 上一章：数据生态](05-data.md) · [返回目录](../README.md) · [下一章：Data RSI →](07-data-rsi.md)
