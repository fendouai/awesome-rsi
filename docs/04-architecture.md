[← 上一章：技术发展史](03-history.md) · [返回目录](../README.md) · [下一章：数据生态 →](05-data.md)

---

# 04 · 统一架构与 Evaluator

> RSI 不是一个算法，而是一套 Feedback Architecture。其中最核心的问题不是「如何生成更多 Candidate」，而是「如何知道 Candidate 真的更好」。

---

## 1. RSI 的统一技术架构

从当前论文来看，一个完整 RSI 系统可以拆成八个核心模块：

```text
                 Objective
                     │
                     ↓
              Research Agent
                     │
        ┌────────────┼────────────┐
        ↓            ↓            ↓
      Data        Harness        Model
        ↓            ↓            ↓
    Training      Execution      Update
        └────────────┼────────────┘
                     ↓
                 Candidate
                     ↓
                 Evaluator
                     ↓
          ┌──────────┴──────────┐
          ↓                     ↓
        KEEP                  REVERT
          ↓
     Experience Memory
          ↓
   Improve Search Strategy
          ↓
       Next Cycle
```

> **RSI 不是一个算法，而是一套 Feedback Architecture。**

---

## 2. Evaluator：RSI 最核心的基础设施

如果只选 RSI 中最重要的一个技术问题，并不是「AI 如何生成更多 Candidate」，而是：

> **AI 如何知道 Candidate 真的更好？**

2026 RSI Survey 将验证信号大致形成一条可靠性等级：

```text
Formal Proof
     ↓
Executable Verifier
     ↓
Hidden Evaluation
     ↓
External Reward
     ↓
Model Judge
     ↓
Self Evaluation
```

其核心观察之一是：

> 已观察到的 Self-Improvement 强度与 Verification Signal 的可靠程度密切相关。([arXiv][3])

---

## 3. 为什么 Evaluator 必须独立

如果系统同时负责 Generate 与 Evaluate，就非常容易产生：

- self-confirmation
- reward hacking
- benchmark gaming
- regression
- evaluator hacking
- model collapse
- diversity collapse

因此真正能够规模化的 RSI，必须具备：

```text
Generate
+
Independent Evaluation
+
Versioning
+
Rollback
+
Regression Testing
```

从工程上看，这非常像：

> **CI/CD for AI Evolution。**

---

## 4. Evaluator 的设计要点

| 要点 | 目的 | 对应实践 |
|---|---|---|
| Hidden Evaluation | 防止对可见集过拟合 | RSI-Exam、AI4AI-Bench |
| Sealed / Held-out | 检验改进是否可迁移 | RSI-Exam 密封数据重跑 |
| Regression Suite | 防止「一处提升、多处退化」 | 多 benchmark 联合评测 |
| Deterministic Gate | 用确定性验证替代模型投票 | Recuris validation gate |
| Judge Ensemble | 降低单一 model judge 偏差 | 多评审聚合 |
| Adversarial Evaluator | 主动寻找评测漏洞 | reward hacking 对抗 |

Evaluator 同时也是产业机会的核心，详见 [14 · 瓶颈与路线图](14-outlook.md)。

---

## 5. 评测信号如何塑造能力

不同能力层级依赖不同的验证信号，这也是 RSI 逐层递进的原因之一：

```text
L1–L2  Output / Prompt   → 可自动评测，迭代最快
L3–L4  Memory / Harness  → unit test / benchmark 反馈
L5     Data              → 端到端训练评测，成本上升
L6–L7  Model / Algorithm → 需要 GPU 与长周期实验
L8     Meta-RSI          → 需要跨层信用分配
```

各层的具体实现见 [06–10 章](06-harness-rsi.md)。

---

[← 上一章：技术发展史](03-history.md) · [返回目录](../README.md) · [下一章：数据生态 →](05-data.md)

[3]: https://arxiv.org/abs/2607.07663
