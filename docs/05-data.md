[← 上一章：统一架构与 Evaluator](04-architecture.md) · [返回目录](../README.md) · [下一章：Harness 与 Memory RSI →](06-harness-rsi.md)

---

# 05 · 数据生态

> RSI 的 Data 并不只是传统 NLP Dataset。目前正在出现四种新的数据形式。

---

## 1. 四类数据

| 类型 | 基本单位 | 典型代表 | 用途 |
|---|---|---|---|
| **Executable Task Dataset** | 可运行的研究任务 | RSI-Exam | 长程研究与泛化 |
| **Research Repository** | 冻结的代码仓库 | AI4AI-Bench | Algorithm Discovery |
| **Trajectory** | 完整执行轨迹 | Agent 运行日志 | Debug / Train / Harness 改进 |
| **Experience** | 抽象经验 | Memory RSI | 跨任务迁移 |

---

## 2. Executable Task Dataset

传统 Benchmark 是：

```text
Input → Output
```

RSI Benchmark 越来越像：

```text
Weak System + Environment + Dataset + Evaluator + Compute Budget
```

Agent 得到一个**完整研究问题**，而不是一道题。代表是 [RSI-Exam](11-benchmarks.md)：每个任务给 Agent 一个可运行但表现较弱的方法，允许最长约 12 小时实验，最终提交 Artifact，并在 Agent 从未访问过的密封数据上从头重跑。

---

## 3. Research Repository

[AI4AI-Bench](09-algorithm-rsi.md) 进一步改变了 Benchmark 的基本单位。不再是 `Task`，而是 `Research Repository`。它提供冻结的研究仓库，Agent 可以修改 objective、loss、training rule、update mechanism、algorithm implementation。

这使 Benchmark 更接近真实的 **ML Research**。

---

## 4. Trajectory

Agent RSI 中越来越重要的数据形式不是 Text，而是 **Trajectory**：

```text
Task → State → Reasoning → Tool Call → Observation
     → Mistake → Recovery → Outcome
```

Trajectory 可以同时用于：

1. Debug Agent
2. Train Agent
3. Discover Failure Pattern
4. Improve Harness
5. Generate Skills
6. Build Evaluator

> **Trajectory 很可能成为 Agent 时代新的核心训练资产。**

---

## 5. Experience

比 Trajectory 更进一步的是 **Experience**。经验并不是保存完整历史，而是抽象成：

```text
State + Failure + Lesson + Skill + Applicability
```

这正是 Memory RSI 的重要方向，代表工作是 [Recuris](06-harness-rsi.md)。

---

## 6. Datasets & Task Sources

现有主要数据与任务源：

- **GitHub Issues / Repositories** — 软件工程（SWE-bench 数据源）。
- **Kaggle Competitions** — ML 工程（MLE-bench 数据源）。
- **Nature-family Papers + Datasets** — 科学发现（NatureBench 数据源）。
- **Reasoning / Math / QA 数据** — DROP、MGSM、GPQA、MMLU 等。

> 能力升级路径：`SWE-bench（AI 改进软件）→ MLE-bench（AI 构建 ML）→ NatureBench（AI 改进科学 ML）→ 未来（AI 改进 AI 研究）`。

---

[← 上一章：统一架构与 Evaluator](04-architecture.md) · [返回目录](../README.md) · [下一章：Harness 与 Memory RSI →](06-harness-rsi.md)
