[← 上一章：Data RSI](07-data-rsi.md) · [返回目录](../README.md) · [下一章：Algorithm RSI →](09-algorithm-rsi.md)

---

# 08 · Model RSI

> 模型能否修改自己的权重？更现实的形态，或许是 Model 与 Harness 互为对方的改进环境。

---

## 1. 权重层自改进（2025）

这一代系统首次触碰 **weight-level self-improvement**：

- [SEAL](https://github.com/Continual-Intelligence/SEAL) — Self-Adapting Language Models：生成 self-edit + 训练指令再 fine-tune，触碰 weight-level self-improvement。
- [Agent0](https://github.com/aiming-lab/Agent0) — Self-Evolving Agents from Zero Data：curriculum agent 与 executor agent 共进化，不依赖人工 curated 数据。（ICML'26 & COLM'26）

> ⚠️ **待独立复核**：Agent0 的「math +18%、general reasoning +24%」、SEAL 的「2×A100/H100 可跑」——引用前建议核对原始仓库。

---

## 2. 2026 年 Model RSI 新进展

| 系统 | 机构 | 核心机制 |
|---|---|---|
| **NeoHorse-1**（[arXiv 2609.08183](https://arxiv.org/abs/2609.08183)，[TokenRhythm/NeoHorse](https://github.com/TokenRhythm/NeoHorse)） | TokenRhythm | 异构模型池 + 智能路由，把路由信号组织成三段课程 SFT 与 routing-guided on-policy distillation；能力导向分配把评测反馈转成下一轮训练配比，闭合 evaluation–selection–update 环。11 个 benchmark 上 4B 由 58.94→64.87、9B 由 65.60→69.04 |
| **HyperAgents**（[arXiv 2603.19461](https://arxiv.org/abs/2603.19461)，[facebookresearch/HyperAgents](https://github.com/facebookresearch/HyperAgents)） | Meta | 把 task agent 与可编辑 meta-agent 结合，其自我修改过程本身也可演化，并能跨域迁移改进 |
| **SIA**（[arXiv 2605.27276](https://arxiv.org/abs/2605.27276)，[hexo-ai/sia](https://github.com/hexo-ai/sia)） | Hexo AI | 在同一个自我改进循环中同时更新 harness 与模型权重 |
| **Meta-Rewarding**（[arXiv 2407.19594](https://arxiv.org/abs/2407.19594)） | — | 让模型评判自己的评判，迭代提升评估与指令跟随能力 |

---

## 3. ScienceBuddy：Harness 与 Model Co-Evolution

[ScienceBuddy](https://github.com/Gen-Verse/ScienceBuddy)（[arXiv 2609.17523][9]）提出了 **Recursive-in-Recursive Self-Improvement**。它包含两个循环。

Inner Loop（固定模型，改 Harness）：

```text
Fixed Model
↓
Improve Harness
↓
Better Harness
```

Outer Loop（用更好的 Harness 生成数据，反哺模型）：

```text
Improved Harness
↓
Generate Better Training Experience
↓
Reinforcement Learning
↓
Better Model
```

于是形成：

```text
Harness improves Model
         ↑       ↓
Model improves Harness
```

这类系统可能比「模型直接修改自己的权重」更加现实，因为：

> Model 与 Harness 可以互相成为对方的 Improvement Environment。([arXiv][9])

---

## 4. 为什么 Co-Evolution 更现实

| 维度 | 直接改权重 | Model ↔ Harness 共进化 |
|---|---|---|
| 单次迭代成本 | 高（需训练） | 低（Harness 可快速迭代） |
| 反馈速度 | 慢 | 快 |
| 可回滚性 | 弱 | 强（Harness 是软件） |
| 风险 | 灾难性遗忘 / collapse | 可分层控制 |
| 数据来源 | 需重新采集 | Harness 运行自动产生 |

这也是为什么 2026 年的完整闭环更倾向于 **Data + Harness + Model 的组合优化**，见 [09 · Algorithm RSI](09-algorithm-rsi.md) 与 [10 · Meta-RSI](10-meta-rsi.md)。

---

[← 上一章：Data RSI](07-data-rsi.md) · [返回目录](../README.md) · [下一章：Algorithm RSI →](09-algorithm-rsi.md)

[9]: https://arxiv.org/abs/2609.17523
