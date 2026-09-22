[← 上一章：理论与经济学](16-theory.md) · [返回目录](../README.md) · [下一章：具身与物理自改进 →](18-embodied.md)

---

# 17 · 安全、对齐与治理

> 一旦系统开始持久地修改自身，「改进」与「漂移」就不再可区分——安全因此不是 RSI 的外围，而是其核心约束。

---

## 1. 为什么安全是 RSI 的内生问题

在 [GAI 形式框架](16-theory.md)中，当评价基准 ρ 可被 Agent 改写时，系统进入 **Goal Drift** 极性；当无外部信号时，退化为 **Self-Referential**。二者正是 RSI 风险的形式化表述。

2026 年出现的一个关键概念是 **Misevolution（错误演化）**：自演化 Agent 在 model、memory、tool、workflow 各条演化路径上都可能出现有害漂移。([arXiv 2509.26354](https://arxiv.org/abs/2509.26354))

---

## 2. 主要失效模式

| 失效模式 | 说明 |
|---|---|
| **Self-confirming loop** | 生成与评估同源，互相确认 |
| **Reward hacking** | 优化评测代理指标而非真实目标 |
| **Goal drift** | 长程中逐渐偏离既定目标 |
| **Model collapse** | 在自生成数据上迭代导致分布坍缩 |
| **Diversity collapse** | 搜索多样性丧失，陷入局部 |
| **Frame lock-in** | 目标过时却无法重新框定 |
| **Sandbagging** | 模型在评测中策略性隐藏能力 |
| **Sleeper agents** | 欺骗性策略穿过安全训练仍保留 |

安全基础工作还包括：reward tampering、mesa-optimization、可中断性、可扩展监督等经典问题。

---

## 3. 防御与护栏

| 机制 | 代表工作 | 作用 |
|---|---|---|
| **对齐漂移监控** | [SAHOO](https://arxiv.org/abs/2603.06333) | goal-drift 检测、约束保持检查、回归风险分析 |
| **确定性护栏** | [LLM-as-a-Judge Is Not an Oracle](https://arxiv.org/abs/2609.02246) | 针对 judge 偏差、指标错误、reward hacking 的确定性门控 |
| **篡改压力测试** | [TamperBench](https://arxiv.org/abs/2602.06911) | 微调 / 权重修改 / 表示篡改下的安全保持 |
| **Harness 篡改审计** | [Auditing Harness Tampering](https://arxiv.org/abs/2609.00069) | 两轴分类：harness 功能角色 × 被违反的义务 |
| **确定性验证门** | Recuris validation gate | 用确定性验证替代模型投票 |
| **Verifier-gated 应用** | SIA、RSIHub | 改进只有在通过验证后才被采纳 |

> 工程原则与 [04 · Evaluator](04-architecture.md) 一致：**Generate 与 Evaluate 必须独立**，并配合 versioning、rollback、regression testing。

---

## 4. 治理与前沿实验室评测框架

治理第一次有了可对齐的评测对象——「AI R&D 能力阈值」。

| 机构 | 框架 | 要点 |
|---|---|---|
| **Anthropic** | Responsible Scaling Policy · AI R&D-4 | 把「完全自动化一名入门级远程研究员的工作」设为能力阈值，并据此评测与防护 |
| **Google DeepMind** | Frontier Safety Framework · ML R&D | 用 CCL / TCL 与专门评测协议衡量显著加速或自动化 AI R&D 的能力 |
| **OpenAI** | Preparedness Framework · AI Self-Improvement | 用 Internal Research Debugging、KernelGen 1P、NanoGPT、PostTrainBench Lite、MLE-Bench Revised 等聚合成 **RSI Index** |

> 这些框架把 [14 · 瓶颈与路线图](14-outlook.md) 中的 **AI R&D Automation Rate** 从研究指标变成了治理对象。Frontier Lab 的内部测量见 [13 · 产业与组织](13-industry.md)。

---

## 5. 开放挑战

- **可审计性**：如何独立证明某个循环「确实在改进」，而非在自我确认。
- **持久修改的信任**：skill / memory / experience graph 一旦写入便长期生效，需要类似软件供应链的完整性机制。
- **方向评价**：验证「哪个方向值得做」比验证「做得对不对」更难，也更缺方法。
- **评测本身的完整性**：sandbagging 与 sleeper agents 说明，评测结果的可信度本身就是一个安全问题。

---

[← 上一章：理论与经济学](16-theory.md) · [返回目录](../README.md) · [下一章：具身与物理自改进 →](18-embodied.md)
