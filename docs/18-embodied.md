[← 上一章：安全、对齐与治理](17-safety.md) · [返回目录](../README.md) · [下一章：Survey 与相关清单 →](19-surveys.md)

---

# 18 · 具身与物理自改进

> 当环境是物理世界，反馈更慢、更贵，但经验也更真实。具身 RSI 把「从执行中学习」推到机器人与交互环境。

---

## 1. 自演化具身 AI 范式

[Self-evolving Embodied AI](https://arxiv.org/abs/2602.04411) 把该范式拆成五个可独立演化的部分：

```text
Memory Self-Updating
Task Self-Switching
Environment Self-Prediction
Embodiment Self-Adaptation
Model Self-Evolution
```

与纯软件 RSI 相比，具身 RSI 多了**embodiment**这一维：身体、传感器、动力学本身也可成为被改进对象。

---

## 2. 代表系统

| 系统 | 机构 | 机制 |
|---|---|---|
| **ASPIRE**（[arXiv 2607.00272](https://arxiv.org/abs/2607.00272)） | NVIDIA GEAR | 从机器人执行轨迹诊断失败，编辑 code-as-policy，把验证过的修复存入 skill library，跨任务与跨本体复用 |
| **ENPIRE**（[arXiv 2606.19980](https://arxiv.org/abs/2606.19980)） | NVIDIA GEAR / CMU / Berkeley | 真机 autoresearch 循环：reset → rollout → verify → 编辑 policy / 训练基础设施 / 算法代码 → 重跑，并可扩展到机器人集群 |
| **MineEvolve**（[arXiv 2603.13131](https://arxiv.org/abs/2603.13131)） | — | 成功经验转 reusable skills，失败转 executable guardrails，无需更新模型参数即可持续指导 planner |
| **RISE**（[arXiv 2602.11075](https://arxiv.org/abs/2602.11075)） | — | 用组合式 world model 生成想象 rollout、估计 advantage 并更新机器人策略（RSS 2026） |
| **Skill-Harness Evolution**（[arXiv 2608.11350](https://arxiv.org/abs/2608.11350)） | — | 权重冻结，同一模型兼任 planner 与 optimizer，持续演化 skill 与 context-code harness |
| **VLA + Residual RL**（[ICLR 2026](https://iclr.cc/virtual/2026/poster/10008318)） | — | 用 residual RL 定位 VLA 失败区域，生成恢复轨迹并蒸馏回通用策略，形成 data→policy 飞轮 |

---

## 3. 与软件 RSI 的差异

| 维度 | 软件 / Agent RSI | 具身 RSI |
|---|---|---|
| 反馈速度 | 快（分钟级） | 慢（真机 rollout） |
| 单次成本 | 低 | 高 |
| Verifier | 测试 / benchmark | 传感器 + 物理成功判据 |
| 可回滚性 | 强（git） | 弱（物理后果） |
| 被修改对象 | code / prompt / memory | 还包括 embodiment 与动力学 |
| 数据来源 | trajectory | trajectory + 真实交互 |

因此具身 RSI 更依赖 **world model / replay** 来降低探索成本，这与 [Dream-RSI](10-meta-rsi.md) 的思路一致。

---

## 4. 相关 Benchmark

- [OSWorld 2.0](https://arxiv.org/abs/2606.29537) — 108 个真实端到端计算机工作流（中位人类耗时约 1.6 小时）。
- [ARC-AGI-3](https://arxiv.org/abs/2603.24621) — 陌生交互环境中探索、推断目标、建模动力学。
- [Long-Horizon-Terminal-Bench](https://arxiv.org/abs/2607.08964) — 46 个需数百 episode 持续执行的终端任务。

完整清单见 [11 · Benchmark 生态](11-benchmarks.md)。

---

[← 上一章：安全、对齐与治理](17-safety.md) · [返回目录](../README.md) · [下一章：Survey 与相关清单 →](19-surveys.md)
