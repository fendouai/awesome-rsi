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

## 6. 相关 AI4AI / Automated Research 工作

| 系统 | 机制 |
|---|---|
| **The AI Scientist-v2**（[Nature 2026](https://doi.org/10.1038/s41586-026-10265-5)） | 模板无关的 agentic tree search：提假设、跑实验、分析结果并写完整论文 |
| **MLEvolve**（[arXiv 2606.06473](https://arxiv.org/abs/2606.06473)） | 渐进图搜索 + 回溯记忆 + 分层代码生成，做长程端到端 ML 算法发现 |
| **AutoResearch**（[arXiv 2608.17906](https://arxiv.org/abs/2608.17906)） | 把 grounded idea generation 与执行 Agent 连接，实验经独立复核后才接受结论 |
| **Towards Execution-Grounded Automated AI Research**（[arXiv 2601.14525](https://arxiv.org/abs/2601.14525)） | 把预训练 / 后训练变成可执行研究环境，进化搜索从实验产出中学习 |
| **AlphaEvolve**（[arXiv 2506.13131](https://arxiv.org/abs/2506.13131)） | LLM 代码生成 + 自动评测 + 进化搜索，改进算法（含 AI 训练组件） |
| **FunSearch**（[Nature 2024](https://www.nature.com/articles/s41586-023-06924-6)） | 冻结代码模型 + evaluator 的进化环，发现新程序与数学结果 |
| **RD-Agent**（[microsoft/RD-Agent](https://github.com/microsoft/RD-Agent)） | 自动化高价值 R&D 流程，「AI drive data-driven AI」 |
| **RSIHub**（[simple-agent-lab/RSIHub](https://github.com/simple-agent-lab/RSIHub)） | 在冻结 evaluator 下做有原则的自我改进，并保留可验证 lineage |
| **AutoML-Zero**（[arXiv 2003.03384](https://arxiv.org/abs/2003.03384)） | 从基础数学操作进化出完整学习算法，最小化人类设计偏置 |
| **AI-GAs**（[arXiv 1905.10985](https://arxiv.org/abs/1905.10985)） | 自动生成环境、架构与学习算法的开放系统 |

> 从 **AutoML-Zero → AlphaEvolve → AI4AI-Bench** 构成一条清晰的「算法发现」脉络：早期进化学习算法，中期用 LLM 进化程序，2026 年开始用冻结仓库与统一尺度**度量 AI 发明算法的能力**。

---

[← 上一章：Model RSI](08-model-rsi.md) · [返回目录](../README.md) · [下一章：Meta-RSI 与 Search RSI →](10-meta-rsi.md)
