[← 上一章：证据等级与核实](15-evidence.md) · [返回目录](../README.md) · [下一章：安全、对齐与治理 →](17-safety.md)

---

# 16 · 理论与经济学

> RSI 是「现象、机制，还是前景」？2026 年的形式化工作开始把这个问题拆成可陈述的条件。

---

## 1. 形式化框架：Generalized Agent Iteration

Generalized Agent Iteration（GAI，[arXiv 2609.13406][17]）把迭代策略改进（GPI）与 RSI 统一为同一学习范式的两个特例。

**系统建模**：`χ = (π, V, m, U, ρ)`

| 符号 | 含义 |
|---|---|
| π | 策略（policy） |
| V | 动作 critic |
| m | 修改器（proposes system changes） |
| U | 修改 critic（scores proposed changes） |
| ρ | 评价基准（the standard） |

**Agent** 是可修改子集 `Ag ⊆ {π, V, m, U, ρ}`。学习循环 = agent evaluation（critic 依 ρ 打分）+ agent improvement（m 提议 ξ，采纳为 χ←χ[ξ]）。

**两个旋钮**：

- 旋钮一：改进机制 `m` 是否属于 Agent？外部 ⇒ **GPI**；内部 ⇒ **RSI**（递归在 m 处闭合，无外部 meta 层）。
- 旋钮二：评价基准 `ρ` 是否外接接地？决定**极性**（anchored / goal drift / self-referential），见 [02 · 分类与技术栈](02-taxonomy.md)。

**意义**：它让不同系统第一次可以放在同一坐标系上比较，并把 RSI 的缺陷「一次只陈述一个条件」（候选自搜索无界、非单调改进、对象与工具重合时的自评估、基准不接地、目标漂移）。

---

## 2. RSI 的经济学

[The Economics of Recursive Self-Improvement](https://arxiv.org/abs/2609.15802)（Cunningham 等，2026-09）把 RSI 建模为**弹性网络**。

**反馈环即有向图**：节点是生产函数的产出，边权是产出对投入的**弹性**。核心环：

```text
AI 能力 → 算法效率 → AI 能力
                （含训练算力）
```

扩展图加入瓶颈（人类、算力、数据）与经济环（产出 → 算力/数据投资）。

**自维持加速条件**：净加速取决于**每个反馈环弹性的乘积**。即使 R&D 完全自动化，若「想法越来越难」导致边际收益递减，或存在瓶颈，也可能不会出现智能爆炸。

**Narrow vs Broad**：

- **Narrow**：优化 AI R&D benchmark（算法效率）。
- **Broad**：有经济价值的广泛任务。

核心环可能在 narrow 上很强，而 broad 实际影响停滞——这是对 RSI 叙事的**关键限定**。

**标定结果**：若 1 单位能力提升带来 ≥15% 的 AI R&D 生产率提升，条件成立；粗略估计当前约 **9%**（编码 Agent 驱动）。结论：**反馈环尚不足以产生自维持加速，但正在增强。**

---

## 3. 极限与负结果

RSI 的理论边界同样重要：

| 结果 | 含义 |
|---|---|
| **Sharpening Mechanism**（[arXiv 2412.01951](https://arxiv.org/abs/2412.01951)） | 自我改进可被理解为把「验证器引导的搜索」摊销进更锐利的策略，因此受验证器质量限制 |
| **LLM 尚不能自我纠正推理**（[arXiv 2310.01798](https://arxiv.org/abs/2310.01798)） | 无可靠外部反馈时，内在自纠正会**降低**推理表现 |
| **Model / Diversity Collapse**（[arXiv 2510.16657](https://arxiv.org/abs/2510.16657)） | 在自生成数据上迭代训练会坍缩；外部验证可稳定短期，但暴露长期极限 |
| **Headroom-Closed Index（HCI）**（[arXiv 2609.11873][12]） | 用 HCI 揭示现有 LLM 的问题，给出五级自主性路线 |

---

## 4. 经典理论与历史锚点

- **Gödel Machine**（Schmidhuber，2003/2006）——可证明最优自我改进。见 [01 · 理论基础](01-foundations.md)。
- **Optimal Ordered Problem Solver**（2004）——复用解以加速后续问题求解。
- **From Seed AI to Technological Singularity**（[arXiv 1502.06512](https://arxiv.org/abs/1502.06512)，2015）——RSI 软件定义与收敛理论。
- **Intelligence Explosion Microeconomics**（MIRI，2013）——决定加速、平台期或爆炸的回报与瓶颈。
- **The Singularity: A Philosophical Analysis**（Chalmers，2010）——智能爆炸的哲学论证。

---

## 5. 开放问题

2026 Survey 列出六个公开问题：

1. **Exchange rate of grounding**：维持改进所需的最低外部信号比例。
2. **Verifying the non-verifiable**：research taste、创造性质量、方向设定的评价。
3. **Stability engineering as a discipline**：把循环动力学（收敛 / 振荡 / 坍缩）统一处理。
4. **Trustworthy accumulation**：持久自修改（skill、memory、experience graph）的验证。
5. **Governance-grade measurement**：可审计地证明某个训练循环「改进了什么、没改进什么」。
6. **Recognizing frame revision**：识别并更换过时目标。

失败模式：self-confirming loop、model collapse、diversity collapse、frame lock-in。

---

[← 上一章：证据等级与核实](15-evidence.md) · [返回目录](../README.md) · [下一章：安全、对齐与治理 →](17-safety.md)

[12]: https://arxiv.org/abs/2609.11873
[17]: https://arxiv.org/abs/2609.13406
