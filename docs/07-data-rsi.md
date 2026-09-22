[← 上一章：Harness 与 Memory RSI](06-harness-rsi.md) · [返回目录](../README.md) · [下一章：Model RSI →](08-model-rsi.md)

---

# 07 · Data RSI

> AI 是否能够根据自己的失败，判断下一轮应该训练什么数据？

---

## 1. 问题定位

Data RSI 位于 RSI 技术栈的 **L5**。它不修改模型结构，也不修改脚手架，而是修改 **Training Data**。

从 Data RSI 开始，Improvement Loop 第一次把「数据」当作可搜索、可迭代的对象，而不是一次性准备的前置资源。

---

## 2. RSIBench-Data：Data Research

RSIBench-Data（[arXiv 2607.25886](https://arxiv.org/abs/2607.25886)）的研究问题正是：

> AI 是否能够根据自己的失败，判断下一轮应该训练什么数据？

系统固定：

- Base Model
- Post-training Stack
- Evaluator
- Training Backend
- Compute Budget

Agent 主要负责 **Data Strategy**。循环为：

```text
Evaluate Model
↓
Discover Capability Gap
↓
Form Hypothesis
↓
Generate Data
↓
Train
↓
Evaluate
↓
Analyze
↓
New Data Strategy
```

官方研究总结显示，Agent 已经能够在多个设置中改进初始方案，但持续搜索经常出现：

> 找到一个强 Candidate 后继续「改进」，反而让结果下降。

这说明 **Stopping、Rollback、Best-State Preservation** 正在成为 RSI 的核心问题。([Evolvent AI][6])

---

## 3. 从 Synthetic Data Generation 到 Data Research

Data RSI 的升级路径是：

```text
Synthetic Data Generation
        ↓
Data Research
```

在 Data Research 中，Agent 自己寻找 Capability Gap 并设计 Curriculum，而不是被动地按人类给定的分布生成数据。

---

## 4. 数据侧的关键工程约束

| 约束 | 说明 |
|---|---|
| **Capability Gap 定位** | 必须先诊断「弱在哪里」，再决定「训练什么」 |
| **Stopping Rule** | 何时停止继续改进，避免负向迭代 |
| **Best-State Preservation** | 保留历史最优，而非接受最后一次结果 |
| **去重与去泄漏** | 训练数据需对 eval benchmark 去重（OpenRSI 已采用） |
| **端到端评测成本** | 每次数据策略变更都需重新训练，成本远高于 Harness RSI |

---

## 5. 相关数据研究工作

- **PostTrainBench**（[arXiv 2603.08640](https://arxiv.org/abs/2603.08640)，[aisa-group/PostTrainBench](https://github.com/aisa-group/PostTrainBench)）— 给 Agent 一个 base model、一张 H100、十小时，自主研究并执行最强 post-training 策略。
- **DataChef**（[yichengchen24/DataChef](https://github.com/yichengchen24/DataChef)）— 用 RL 为 LLM 适配寻找最优 data recipe。
- **FT-Dojo**（[arXiv 2603.01712](https://arxiv.org/abs/2603.01712)）— 把数据收集、训练、评测、诊断、策略修订变成可执行环境。
- **Data-Efficient Language Modeling / Research RSI**（[arXiv 2609.10702](https://arxiv.org/abs/2609.10702)）— 把研究过程本身作为 RSI 对象，在 BabyLM Strict-Small 上做长期自主研究。

---

[← 上一章：Harness 与 Memory RSI](06-harness-rsi.md) · [返回目录](../README.md) · [下一章：Model RSI →](08-model-rsi.md)

[6]: https://evolvent.co/en/research
