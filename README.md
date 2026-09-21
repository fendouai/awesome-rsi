<div align="center">

# Awesome RSI

**Recursive Self-Improvement（递归自我改进）精选清单**

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)
![Updated](https://img.shields.io/badge/updated-2026--09-blue)
![Status](https://img.shields.io/badge/status-actively%20maintained-green)

*系统梳理 RSI 开源生态：发展顺序 · 技术变迁 · 基准测试成绩。*
*关键数据均已对照论文 / 官方仓库逐项核实。*

</div>

---

## Contents

- [Systems](#systems)
- [Benchmarks](#benchmarks)
- [Datasets & Task Sources](#datasets--task-sources)
- [Foundations & Early Work](#foundations--early-work)
- [发展顺序](#发展顺序)
- [技术变迁脉络](#技术变迁脉络)
- [基准测试成绩](#基准测试成绩)
- [数据核实说明](#数据核实说明)
- [Contributing](#contributing)

---

## 边界定义

| 概念 | 是什么 | 举例 |
|---|---|---|
| **Dataset / Task** | 数据与任务源 | GitHub Issues、Kaggle 竞赛、Nature 论文 |
| **Benchmark** | 数据 + 评测协议 + 阈值包装成的评价体系 | SWE-bench、MLE-bench、NatureBench |
| **RSI System** | 会修改自身、再被 benchmark 检验的系统 | DGM、Gödel Agent、OpenRSI |

> SWE-bench / MLE-bench 本身**不是** RSI；DGM、OpenRSI 这类系统才是。
> **「强 RSI」**：系统能修改构成自身能力的关键部分，并经执行反馈反复产生后继版本。单纯的 Self-Reflection / Self-Critique 不算。

---

## Systems

按世代分组，不按成绩排名。

### ① Scaffold 层自改进（2023–2025）

- [STOP](https://github.com/microsoft/stop) — Self-Taught Optimizer：让优化程序递归优化自己。底层 LLM 未变，作者自述非 full RSI。（Microsoft，2023）
- [ADAS](https://github.com/ShengranHu/ADAS) — Automated Design of Agentic Systems：Meta Agent 自动搜索并设计 agent 架构；Gödel Agent 中 **Meta Agent Search（MAS）基线**的来源。（ICLR 2025）
- [Gödel Agent](https://github.com/Arvid-pku/Godel_Agent) — Self-Referential Agent：运行时用 monkey patch 读写自身源码；Game of 24 从 4% → 78%。（ACL 2025，arXiv 2410.04444）
- [SICA](https://github.com/MaximeRobeyns/self_improving_coding_agent) — Self-Improving Coding Agent：评估 → 存档 → 改自身 codebase → 下一轮，适合 trajectory 研究。（2025，[workshop paper](https://openreview.net/pdf?id=rShJCyLsOr)）
- [Darwin Gödel Machine (DGM)](https://github.com/jennyzzt/dgm) — 开放进化：archive + selection + mutation + evaluation；SWE-bench 20% → 50%、Polyglot 14.2% → 30.7%。（arXiv 2505.22954）

### ② 权重层自改进（2025）

- [SEAL](https://github.com/Continual-Intelligence/SEAL) — Self-Adapting Language Models：生成 self-edit + 训练指令再 fine-tune，触碰 weight-level self-improvement。
- [Agent0](https://github.com/aiming-lab/Agent0) — Self-Evolving Agents from Zero Data：curriculum agent 与 executor agent 共进化，不依赖人工 curated 数据。（ICML'26 & COLM'26）

### ③ AI4AI（2026）

- [OpenRSI / OpenMLE / Frontis-MA1](https://github.com/FrontisAI/OpenRSI) — 训练一个专门改进 ML 系统的 meta-evolution model；四算子 **Draft / Improve / Debug / Crossover**；MLE-Bench Lite 39.39% → 71.21%。（arXiv 2607.28568）

---

## Benchmarks

按能力阶梯分组。

### Software Engineering

- [SWE-bench](https://github.com/SWE-bench/SWE-bench) — 真实 GitHub Issue + repo + tests，RSI 最成熟的实验场。含 Verified / Lite / Multilingual / Multimodal 变体。
- Polyglot — 多语言 coding benchmark，用于检验 self-improvement 的跨语言泛化（DGM 使用）。

### ML Engineering / AI4AI

- [MLE-bench](https://github.com/openai/mle-bench) — 75 个 Kaggle ML 竞赛，测「AI 当 ML 工程师」。（OpenAI，2024）
- [RE-Bench](https://github.com/METR/RE-Bench) — 测 AI 自主完成 **AI R&D** 的能力（METR，2024）。

### Scientific Discovery

- [NatureBench](https://github.com/FrontisAI/NatureBench) — 90 个 Nature 系论文科学任务，测能否达到 / 超过论文 SOTA。（arXiv 2606.24530）

### Reasoning

- DROP · MGSM · GPQA · MMLU · Game of 24 — 早期 self-improving agent 常用（Gödel Agent 等）。
- MATH / MATH500 · GSM8K · ARC · HumanEval · MBPP — 通用能力与 coding。

---

## Datasets & Task Sources

- **GitHub Issues / Repositories** — 软件工程（SWE-bench 数据源）。
- **Kaggle Competitions** — ML 工程（MLE-bench 数据源）。
- **Nature-family Papers + Datasets** — 科学发现（NatureBench 数据源）。
- **Reasoning / Math / QA 数据** — DROP、MGSM、GPQA、MMLU 等。

> 能力升级路径：`SWE-bench（AI 改进软件）→ MLE-bench（AI 构建 ML）→ NatureBench（AI 改进科学 ML）→ 未来（AI 改进 AI 研究）`。

---

## Foundations & Early Work

- [Gödel Machine](https://people.idsia.ch/~juergen/goedelmachine.html) — Schmidhuber（2003/2007），可证明自我改进的理论起源。
- [STaR](https://arxiv.org/abs/2203.14465) — Self-Taught Reasoner：用自身推理链 bootstrap 训练（2022）。
- [Reflexion](https://arxiv.org/abs/2303.11366) — 语言化反思，口头 RL（2023）。
- [Voyager](https://arxiv.org/abs/2305.16291) — 开放式 embodied skill 库（2023）。
- [Self-Rewarding Language Models](https://arxiv.org/abs/2401.10020) — 自评分自训练（Meta，2024）。

---

## 发展顺序

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
> **顺序修正**：ADAS（2024-08）早于 Gödel Agent（2024-10）；Gödel Agent 对比的 MAS 基线正来自 ADAS。

---

## 技术变迁脉络

核心主线是 **「改什么」的跃迁**：

```
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

## 基准测试成绩

全部来自论文 / 官方 README 一手来源。

### Level 1 — Reasoning（Gödel Agent，GPT-3.5 主干）

| Benchmark | Meta Agent Search | Gödel Agent |
|---|---:|---:|
| DROP (F1) | 79.4 | **80.9** |
| MGSM (%) | 53.4 | **64.2** |
| MMLU (%) | 69.6 | **70.9** |
| GPQA (%) | 34.6 | **34.9** |

- Game of 24：4% → 78%；无限制版 DROP 90.5 / MGSM 90.6%。
- 价值在于「同底座下 self-improvement 的增益」，非绝对 SOTA。

### Level 2 — Software Engineering（DGM）

| Benchmark | Initial | DGM |
|---|---:|---:|
| SWE-bench | 20.0% | **50.0%** |
| Polyglot (full) | 14.2% | **30.7%** |

### Level 3 — ML Engineering（OpenRSI / Frontis-MA1 · MLE-Bench Lite 22 题 / 12h / 1×RTX 4090 / 12GB VRAM）

| 配置 | Medal Average |
|---|---:|
| Qwen3.6-35B-A3B + OpenMLE-Evo（base） | 39.39% |
| Frontis-MA1-35B + OpenMLE-Evo（post-train） | **60.61%** |
| Frontis-MA1-35B + OpenMLE-Evo-Max | **71.21%** |

- 对照：GPT-5.5 + Codex = 68.18%，GPT-5.6 Sol / Kimi K3 = 72.73%。即**超过 GPT-5.5+Codex，逼近 GPT-5.6 Sol**。
- 30B 版复现：34.85% → 53.03% → 66.67%（+18.18pp post-training 增益）。

### Level 4 — Scientific Discovery（NatureBench）

| 评测 | 成绩 |
|---|---|
| 全量 90 题：最强 coding-agent 配置 Surpass-SOTA（g>0.1） | **17.8%** |
| NatureBench Lite（10 题）：Frontis-MA1-35B + OpenMLE-Evo adapter | 30% Surpass / **70% Match-SOTA** |
| Model 迁移（framework 固定） | Match-SOTA 50% → **70%** |
| Framework 迁移（model 固定） | Match-SOTA 20% → **50%** |

- 核心结论：agent 成功主要靠**方法论翻译**，而非真正发明；失败主因 = 方法选错 + 算力不足。

### Benchmark 基线

- MLE-bench（OpenAI 2024）：o1-preview + AIDE 达 bronze 及以上 = **16.9%**。

> ⚠️ **待独立复核**：Agent0 的「math +18%、general reasoning +24%」、SEAL 的「2×A100/H100 可跑」——引用前建议核对原始仓库。

---

## 数据核实说明

1. **DGM 官方代码是 `jennyzzt/dgm`**（arXiv 摘要原文），不是 `kew-lab/darwin-godel-machine`（疑似 fork）。
2. **NatureBench Surpass-SOTA = 17.8%**（arXiv v2 已更新 GLM-5.2 / MiniMax-M3），不是 15.6%。
3. **Gödel Agent 主干是 GPT-3.5**。
4. **OpenRSI 论文 = arXiv 2607.28568（2026-07）**，Frontis-MA1-35B 基于 Qwen3.6-35B-A3B（30B 版基于 Qwen3-30B-A3B-Thinking-2507）。
5. STOP / ADAS / SEAL / Agent0 / RE-Bench 的仓库创建日期均已通过 GitHub 元数据核实。

---

## Contributing

欢迎 PR。新增条目请遵循：

- 提供**论文 / 官方仓库一手来源**，并标注可验证的 benchmark 分数。
- 区分 Dataset / Benchmark / RSI System，勿混用。
- 分数如来自二手资料，请标注「待独立复核」。

---

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/80x15.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, maintainers have waived all copyright on this list.
