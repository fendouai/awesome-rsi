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

这些非权重部分统称 **Harness / Scaffold**。Harness RSI 直接修改其中的 Agent Loop、Tool Strategy、Context Strategy、Skill、Prompt、Memory、Observation Processing。

对应 [技术栈](02-taxonomy.md) 的 **L2–L4**。

---

## 2. 早期 Scaffold 层自改进（2023–2025）

这一代系统验证了「AI 修改自己的脚手架」的可行性：

- [STOP](https://github.com/microsoft/stop) — Self-Taught Optimizer：让优化程序递归优化自己。底层 LLM 未变，作者自述非 full RSI。（Microsoft，2023）
- [ADAS](https://github.com/ShengranHu/ADAS) — Automated Design of Agentic Systems：Meta Agent 自动搜索并设计 agent 架构；Gödel Agent 中 **Meta Agent Search（MAS）基线**的来源。（ICLR 2025）
- [Gödel Agent](https://github.com/Arvid-pku/Godel_Agent) — Self-Referential Agent：运行时用 monkey patch 读写自身源码；Game of 24 从 4% → 78%。（ACL 2025，arXiv 2410.04444）
- [SICA](https://github.com/MaximeRobeyns/self_improving_coding_agent) — Self-Improving Coding Agent：评估 → 存档 → 改自身 codebase → 下一轮。（2025，[workshop paper](https://openreview.net/pdf?id=rShJCyLsOr)）
- [Darwin Gödel Machine (DGM)](https://github.com/jennyzzt/dgm) — 开放进化：archive + selection + mutation + evaluation；SWE-bench 20% → 50%、Polyglot 14.2% → 30.7%。（arXiv 2505.22954）

成绩明细见 [11 · Benchmark 生态](11-benchmarks.md)。

---

## 3. ModularRSI：模块化 Harness 进化

Harness RSI 的困难之一是：如果整个 Agent 一次性变化，很难确定提升来自哪里。ModularRSI 把 Harness 拆成五个功能模块：

```text
Agent Loop · Tool Use · Observation Management
· Context Management · Task Completion Detection
```

核心思路不是「Rewrite everything」，而是：

```text
Compare Successful vs Failed Trajectory
        ↓
Find recurring behavioral deficiency
        ↓
Modify only affected module
```

它采用 **benchmark-disjoint** 设计：从外部来源整理 2,000 个可执行演化任务，与下游评测 benchmark 不相交；在 TB2.0 与 SWE-Bench Verified 上对未见域和跨域任务均有稳定提升，且可跨基础模型迁移。（[arXiv 2609.14857](https://arxiv.org/abs/2609.14857)）

这实际上解决的是 **Credit Assignment**，也标志着 RSI 从 **Monolithic Evolution** 向 **Modular Evolution** 转变。

---

## 4. 2026 年 Harness RSI 新进展

| 系统 | 机构 | 核心机制 |
|---|---|---|
| **RRSI**（[arXiv 2609.24972](https://arxiv.org/abs/2609.24972)，[google-research/rrsi](https://github.com/google-research/rrsi)） | Google Research | 把**正则化**引入 harness 自改进：proposer 用时间退火预算限制单次编辑数并鼓励未探索轨迹；selector 配 critic（筛掉 benchmark 专属提议）与 pruner（删除过小 / 过贵 / 失效改动）。8 个 benchmark 上 in-distribution +14.1，5 个 OOD +4.7，且 token 少 30% |
| **SoL-Pi**（[arXiv 2609.20519](https://arxiv.org/abs/2609.20519)，[NVlabs/SoL-Pi](https://github.com/NVlabs/SoL-Pi)） | NVIDIA | 在 harness 层 scaling auto-research loop；四个机制（action execution、context compaction、observation handling、delegated reading）存活选择。EdgeBench 51 任务上性能相当，token 流量 −44.7~49.0%，API 成本约 −1/3 |
| **SIFT**（[arXiv 2609.19526](https://arxiv.org/abs/2609.19526)） | — | 用 LLM-as-judge 成对比较候选 patch，经正则化 Bradley-Terry 聚合后驱动轻量树搜索，把昂贵的下游评测留给最有希望的节点 |
| **AutoHarness**（[arXiv 2603.03329](https://arxiv.org/abs/2603.03329)） | — | 从环境反馈合成并迭代精炼可执行 harness，在 145 个 TextArena 游戏中消除非法动作 |
| **Continual Harness**（[arXiv 2605.09998](https://arxiv.org/abs/2605.09998)） | — | 单条连续轨迹内在线精炼 prompt、sub-agent、skill、memory，并扩展到与模型权重共学习 |
| **MetaSkill-Evolve**（[arXiv 2607.05297](https://arxiv.org/abs/2607.05297)） | — | 双时间尺度：快环演化 task skill，慢环演化治理 Analyzer / Retriever / Allocator / Proposer / Evolver 的 meta-skill |
| **SkillOpt**（[arXiv 2605.23904](https://arxiv.org/abs/2605.23904)） | — | 把单个 skill 文档当作冻结 Agent 的外部状态，独立 optimizer 提议有界编辑，仅在严格 held-out 提升时接受 |
| **Agentic Harness Engineering**（[arXiv 2604.25850](https://arxiv.org/abs/2604.25850)） | — | 以可观测编辑自动演化 tools、middleware、memory、prompts，并在后续任务验证预测 |
| **SIA**（[arXiv 2605.27276](https://arxiv.org/abs/2605.27276)，[hexo-ai/sia](https://github.com/hexo-ai/sia)） | Hexo AI | 在同一个自我改进循环中同时更新 harness 与模型权重 |
| **AI4AI at Test-Time**（[arXiv 2608.12307](https://arxiv.org/abs/2608.12307)） | — | 用更强的 builder model 迭代构造推理期 harness，把能力迁移到更弱的目标模型（不更新参数） |

---

## 5. Memory RSI

### Recuris

[Recuris](https://github.com/Gen-Verse/Recuris) 路线是：**模型不变，Prompt 不变，进化 Memory**。它把 Skill Memory 建模为多个结构化组件，让 Meta-Agent 根据 execution trace 定位失败属于哪个 memory component。

修改完成后，通过 **deterministic validation gate** 判断是否保留，而不是让模型自己投票。其 evolved memory 还可**跨模型迁移**——意味着 **Experience 可能成为独立于 Model 的资产**。

### RSIAgent

[RSIAgent](https://github.com/AetherLabsAI/RSIAgent)（[arXiv 2609.15364](https://arxiv.org/abs/2609.15364)）是 training-free 的多 Agent 框架，通过 **broad-then-deep** 自主探索构建可复用记忆（含 action / condition / consequence 的因果关系），记忆冻结后可直接复用，无需更新参数。

### 其他记忆演化

- [ACE · Agentic Context Engineering](https://arxiv.org/abs/2510.04618) — 把 context 当作结构化 playbook，经生成 / 反思 / 策展演化，避免 context collapse。
- [EvolveR](https://arxiv.org/abs/2510.16079) — 把交互轨迹蒸馏为可复用策略原则，形成经验闭环。
- [ExpeL](https://arxiv.org/abs/2308.10144) — 从成功 / 失败轨迹抽取可迁移洞见。

---

## 6. 为什么 Harness RSI 会先爆发

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

## 7. 关键挑战：泛化与过拟合

2026 年 harness RSI 的核心争议是**泛化**：在评测集或其子集上演化，难以区分「可复用改进」与「benchmark 专属适配」。应对手段包括：

- **benchmark-disjoint 演化**（ModularRSI）
- **正则化约束**（RRSI）
- **严格 held-out 接受门**（SkillOpt）
- **确定性验证门**（Recuris）

这与 [14 · 瓶颈与路线图](14-outlook.md) 中 Generalization 瓶颈直接对应。

---

[← 上一章：数据生态](05-data.md) · [返回目录](../README.md) · [下一章：Data RSI →](07-data-rsi.md)
