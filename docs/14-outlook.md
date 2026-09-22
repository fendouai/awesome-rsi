[← 上一章：产业与组织](13-industry.md) · [返回目录](../README.md) · [下一章：证据等级与核实 →](15-evidence.md)

---

# 14 · 瓶颈与路线图

> 决定 AI 能力增长速度的，可能不再只是我们还能训练多大的模型，而是 AI 本身能够以多快的速度发现如何制造更好的 AI。

---

## 1. RSI 最大的六个技术瓶颈

### 14.1 Evaluation

AI 怎么知道「自己真的变好了」？这是第一问题。见 [04 · 统一架构与 Evaluator](04-architecture.md)。

### 14.2 Generalization

Benchmark 提升不等于 General Intelligence 提升。因此越来越需要 hidden split、sealed evaluator、benchmark-disjoint evolution、cross-domain transfer。

### 14.3 Regression

一个改动可能造成：

```text
Coding +15%
Math -10%
Tool Use -20%
```

因此 RSI 必须拥有 **Regression Suite**。

### 14.4 Credit Assignment

一个现代 Agent 可能包含 Model、Prompt、Memory、Tools、Skills、Harness、Data、Evaluator。能力提升到底来自哪里？Modular RSI 正是在解决这个问题。

### 14.5 Exploration Cost

AI Research 的最大瓶颈之一：Experiment 很贵。Harness 修改可能几美元，训练 Model 可能数千、数万甚至数百万美元。因此 Dream-RSI 这样的 Replay / Simulation / World Model 可能成为降低 **Research Search Cost** 的重要技术。

### 14.6 Research Taste

今天 Agent 很擅长：

```text
Execute Experiment
```

但优秀研究者真正稀缺的能力是：

```text
Choose Experiment
```

也就是：什么值得试？哪个失败值得研究？哪个方向应该放弃？哪个结果可能形成新的 Paradigm？

2026 RSI Survey 同样把 **research direction-setting** 视为人类仍然处在 Improvement Loop 中的重要原因。([arXiv][3])

---

## 2. 一个非常重要的新指标：AI R&D Automation Rate

未来衡量 RSI 进度，最值得长期追踪的指标不是 Benchmark Score，而是：

$$
AI\ R\&D\ Automation\ Rate
$$

即：制造下一代 AI 所需工作中，有多少已经由 AI 完成？

| AI Research 环节 | 2026 大致成熟度 |
|---|---|
| Coding | 高 |
| Debugging | 高 |
| Experiment Execution | 高 |
| Data Generation | 中高 |
| Evaluation | 中高 |
| Experiment Design | 中 |
| Hypothesis Generation | 中 |
| Research Taste | 低 |
| Research Direction | 低 |
| Paradigm Discovery | 极低 |

Anthropic 已经开始尝试公开测量类似指标，见 [13 · 产业与组织](13-industry.md)。([Anthropic][1])

---

## 3. 从 Agent Loop 到 Research Loop

过去几年 Agent 主要解决 `User Task`，下一代 Agent 开始解决 `Research Task`。两者最大的差异是：

- 用户任务通常存在比较明确的 Goal + Success Criterion。
- Research Task 则包含 Unknown Goal + Unknown Path + Unknown Evaluation。

因此真正的 AI Researcher 必须自己完成：

```text
Observe → Find Problem → Form Hypothesis → Design Experiment
       → Run → Evaluate → Interpret → Decide Next Experiment
```

传统 Agent：

```text
Observe → Think → Act
```

Research Agent：

```text
Observe Failure → Hypothesis → Design Experiment → Execute
                → Measure → Interpret → Update Belief
                → Choose Next Experiment
```

> **Research Loop 本身正在成为新的 Agent Loop。**
> 未来 RSI 最核心的软件可能不再只是 Agent Framework，而是 **Research Operating System**。

---

## 4. 未来 1–2 年最值得关注的五条路线

1. **Harness Evolution** — 最成熟、最低成本、最容易商业化。关注 Agent Loop、Context Management、Tool Use、Skills、Memory。
2. **Evaluator Infrastructure** — RSI 最核心的基础设施。包括 verifier、benchmark、hidden eval、regression testing、judge ensemble、adversarial evaluator。
3. **Trajectory Intelligence** — Trajectory 将变成新的 Agent Debug Data，系统自动回答「Agent 为什么失败」「哪一步最值得改」。
4. **Data Research Agent** — 从 Synthetic Data Generation 升级到 Data Research，Agent 自己寻找 Capability Gap 并设计 Curriculum。
5. **AI Research Agent** — Agent 从 Software Engineer 向 AI Researcher 迁移。这也是 RSI 真正进入 Model / Algorithm Layer 的前提。

---

## 5. 未来 3–5 年（推演）

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

> 这不是确定时间预测，而是一条值得跟踪的 **Capability Dependency Graph**，每一层都依赖前一层成熟。

---

## 6. 商业机会

从创业角度，RSI 不应该只理解为「做一个会自己进化的大模型」，更现实的机会出现在基础设施层。

### Opportunity 1 · Agent Evaluator

输入 `Agent + Task + Trajectory`，输出 `Score + Failure Analysis + Regression Report`。

### Opportunity 2 · Harness Optimizer

输入 `Agent + Historical Trajectories`，自动修改 prompt、tools、skill、context、loop，并通过 Benchmark 自动选择版本。可以理解为 **Compiler / AutoML for Agents**。

### Opportunity 3 · Trajectory Intelligence Platform

类似传统 Datadog，但监控的是 Agent Reasoning & Execution。核心功能：trajectory clustering、failure taxonomy、bottleneck detection、skill extraction、improvement suggestion。

### Opportunity 4 · RSI Benchmark Platform

未来可能需要类似 `MLPerf + SWE-Bench + Weights & Biases` 的组合产品，统一测试 Model、Agent、Skill、Harness 能否持续、自主、可泛化地改进。

### Opportunity 5 · AI Research Infrastructure

更长期、更大的市场：

```text
Research Agent + Experiment Sandbox + GPU Scheduler
+ Evaluator + Knowledge Base + Research Memory + Evolution Engine
```

可以理解为 **Operating System for Machine Research**。

---

## 7. 从 Scaling Law 到 Improvement Law

过去十年 AI 最重要的能力增长模式是 Scaling：

```text
More Compute + More Data + Larger Model = Better AI
```

RSI 带来的潜在变化是：

```text
Better AI + Better AI Research = Even Better AI
```

也就是说，能力增长来源可能从 **Scaling Law** 进一步扩展到 **Improvement Loop**。未来真正值得研究的问题可能是：

$$
\Delta Capability = f(Compute,\ Data,\ Model,\ Research\ Efficiency)
$$

其中 **Research Efficiency** 过去主要来自人类研究者，未来越来越可能来自 **AI Researcher**。

---

## 8. 最终结论

2026 年是 RSI 从 **哲学与理论问题** 进入 **可执行工程问题** 的重要节点。当前公开研究已经开始分别解决：

```text
How to improve outputs
↓
How to improve prompts
↓
How to improve memory
↓
How to improve harnesses
↓
How to improve training data
↓
How to improve models
↓
How to improve training algorithms
↓
How to improve AI research
```

而真正的最终问题是：

```text
How to improve the process that improves AI?
```

- 目前最成熟：Self-Refinement、Memory 与 Harness Evolution。
- 正在突破：Data RSI 与 Automated AI Research。
- 仍处早期：Algorithm RSI 与 Meta-RSI。
- 尚未有公开证据证明实现：Open-ended Recursive Self-Improvement。

因此，2026 年 RSI 最重要的变化并不是「AI 已经能够无限地改进自己」，而是：

> **AI 已经开始成为 AI Research Pipeline 中越来越重要的执行者，并开始参与修改产生下一代 AI 的 Data、Harness、Model 与 Research Process。**

Anthropic 已开始量化 AI R&D Automation Rate；OpenAI 已建立专门的 RSI 团队；RSI-Exam、AI4AI-Bench、RSIBench-Data 等 Benchmark 开始把「AI 改善 AI」转化成可测量问题；OpenRSI、ScienceBuddy、Dream-RSI、MetaRSI 等工作则开始探索不同 Improvement Loop 如何组合。

如果这条路线继续发展，AI 下一阶段最重要的 Scaling Factor 可能不再只是 Parameter、Data 和 GPU，而会增加第四个变量：

# Research.

最终决定 AI 能力增长速度的，可能不是「我们还能训练多大的模型」，而是：

> **AI 本身能够以多快的速度发现如何制造更好的 AI。**

这才是 Recursive Self-Improvement 真正值得长期跟踪的原因。

---

[← 上一章：产业与组织](13-industry.md) · [返回目录](../README.md) · [下一章：证据等级与核实 →](15-evidence.md)

[1]: https://www.anthropic.com/institute/measuring-pace-of-ai-development
[3]: https://arxiv.org/abs/2607.07663
