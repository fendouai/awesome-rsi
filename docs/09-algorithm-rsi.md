[← 上一章：Model RSI](08-model-rsi.md) · [返回目录](../README.md) · [下一章：Meta-RSI 与 Search RSI →](10-meta-rsi.md)

---

# 09 · Algorithm RSI

> AI 是否能够发明更好的 AI 学习算法？这是「改进模型」与「改进学习方法」之间的分界线。

---

## 1. 问题定位

普通 Agent 可以修改：

```text
Hyperparameter
```

甚至：

```text
Training Script
```

但真正的 Algorithm RSI 要修改的是：

```text
How the model learns
```

AI4AI-Bench 正是围绕这一分界线设计的。

---

## 2. AI4AI-Bench：Algorithm RSI Benchmark

[AI4AI-Bench](https://arxiv.org/abs/2608.20318) 把所有任务映射到统一尺度：

$$
0 = Uninformative\ Model
$$

$$
0.1 = Repository\ Original\ Algorithm
$$

$$
1 = Task\ Optimum
$$

论文共测试 **6 个系统、29 种配置、10 个任务**：

| 指标 | 数值 |
|---|---|
| 平均 | **0.166** |
| 最好系统 | **0.250** |
| 真正改变算法的 Submission（平均） | 约 **0.226** |
| 其余 Submission（平均） | 约 **0.126** |

更值得注意的是：大部分 Agent 提交甚至没有真正改变 Model Learning Algorithm。

> 这揭示了当前 AI 的一个重要能力边界：**Agent 已经非常擅长 Coding，但距离真正进行 Algorithm Research 仍然很远。**

Benchmark 细节（冻结 Repository、4 小时研究预算、单张 B300、评估端最长 12 小时）见 [11 · Benchmark 生态](11-benchmarks.md)。

---

## 3. OpenRSI：走向完整 AI4AI Stack

FrontisAI 发布的 [OpenRSI](https://github.com/FrontisAI/OpenRSI) 是 2026 年比较完整的开放 AI4AI 技术栈之一。其核心组件包括：

- **OpenMLE-Gym** — Executable ML Research Environment。
- **OpenMLE-RL** — 利用 execution-grounded experience 训练 Agent。
- **OpenMLE-Evo** — 长程 Program Evolution / Search。
- **OpenMLE Sandbox** — 负责 CPU/GPU job、execution、automatic evaluation、distributed experiment。
- **Frontis-MA1** — 面向 Machine Learning Engineering 的 Meta-Evolution Agent。

项目强调：

> Make AI improving AI executable, measurable and reproducible.

这非常重要，因为 RSI 正开始形成完整软件栈：

```text
Agent + Environment + Training + Evolution + Evaluator + Sandbox
```

---

## 4. AI4AI 的成绩信号

OpenRSI / Frontis-MA1 在 MLE-Bench Lite 上展示了完整的训练 + 搜索闭环效果：

| 配置 | Medal Average |
|---|---:|
| Qwen3.6-35B-A3B + OpenMLE-Evo（base） | 39.39% |
| Frontis-MA1-35B + OpenMLE-Evo（post-train） | **60.61%** |
| Frontis-MA1-35B + OpenMLE-Evo-Max | **71.21%** |

对照：GPT-5.5 + Codex = 68.18%，GPT-5.6 Sol / Kimi K3 = 72.73%。即 **超过 GPT-5.5+Codex，逼近 GPT-5.6 Sol**。

完整评测口径与基线见 [11 · Benchmark 生态](11-benchmarks.md)。

---

## 5. 四算子：OpenRSI 的进化机制

OpenRSI 的 meta-evolution 使用四个算子：

```text
Draft → Improve → Debug → Crossover
```

这使「训练」与「搜索」统一到同一循环中：既训练一个专门的改进器，又用它持续搜索更好的 ML 方案。

---

[← 上一章：Model RSI](08-model-rsi.md) · [返回目录](../README.md) · [下一章：Meta-RSI 与 Search RSI →](10-meta-rsi.md)
