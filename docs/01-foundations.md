[← 上一章：执行摘要](00-overview.md) · [返回目录](../README.md) · [下一章：分类与技术栈 →](02-taxonomy.md)

---

# 01 · 理论基础

> 真正的 RSI 研究，始于一个形式化问题：一个程序能否安全地修改自身？

---

## 1. RSI 的形式化定义

Recursive Self-Improvement 可以抽象为：

$$
S_{t+1}=I(S_t,E_t,V)
$$

其中：

- \(S_t\)：当前 AI System
- \(E_t\)：系统运行产生的 Experience / Trajectory
- \(I\)：Improvement Operator
- \(V\)：Evaluator / Verifier

其循环结构为：

```text
System₀
   ↓
Execution
   ↓
Experience / Failure
   ↓
Improvement Operator
   ↓
System₁
   ↓
Execution
   ↓
Experience
   ↓
Improvement
   ↓
System₂
```

在普通 Self-Improvement 中，改进方法本身由人类预先规定：

$$
I = fixed
$$

更强意义上的 RSI 则允许系统改进「如何改进自己」：

$$
I_{t+1}=M(I_t,E_t)
$$

> **系统不仅能够改善自己，还能够改善「如何改善自己」。**

后者通常被视为 **Meta-RSI**。

---

## 2. 理论 RSI（1980s–2000s）

RSI 的思想根源早于大模型时代。第一阶段的探索主要围绕：

- Meta-Learning
- Self-Modifying Program
- Learning to Learn
- Gödel Machine

这一阶段回答的核心问题是：

> 一个程序在理论上能否安全地修改自身？

---

## 3. Gödel Machine：形式化 RSI 的起点

Jürgen Schmidhuber 提出的 [Gödel Machine](https://people.idsia.ch/~juergen/goedelmachine.html) 是 RSI 理论的重要基础之一。

其核心思想是：系统可以改写自己的程序，**但只有在能够证明修改可以提升预期 Utility 时才允许进行修改。**

```text
Current Program
      ↓
Search for Rewrite
      ↓
Prove Improvement
      ↓
Rewrite
      ↓
New Program
```

今天 Agent RSI 中常见的：

```text
Candidate
↓
Evaluation
↓
KEEP / REVERT
```

事实上可以视为 Gödel Machine 中「证明改进」思想的工程化弱版本——用经验评测替代形式化证明。

---

## 4. 从理论到工程的三次松动

从 Gödel Machine 到 2026 年的 Agent RSI，有三个关键松动：

| 维度 | 理论 RSI | 工程 RSI |
|---|---|---|
| **改进判据** | 形式化证明 | Evaluator / Benchmark |
| **修改对象** | 任意程序 | Prompt / Memory / Harness / Data / Weights |
| **回滚机制** | 证明保证 | Versioning + Rollback + Regression |

这三次松动使 RSI 从不可计算的理想，变成了可以实验、可以度量、可以迭代的工程问题——这正是 [03 · 技术发展史](03-history.md) 的主线。

---

## 5. 早期奠基工作

在大模型 RSI 系统出现之前，以下工作奠定了「自我改进」的方法论基础：

- [STaR](https://arxiv.org/abs/2203.14465) — Self-Taught Reasoner：用自身推理链 bootstrap 训练（2022）。
- [Reflexion](https://arxiv.org/abs/2303.11366) — 语言化反思，口头 RL（2023）。
- [Voyager](https://arxiv.org/abs/2305.16291) — 开放式 embodied skill 库（2023）。
- [Self-Rewarding Language Models](https://arxiv.org/abs/2401.10020) — 自评分自训练（Meta，2024）。

> 这些工作大多只修改 Output 或短期上下文，属于 **bounded self-refinement**，尚未构成持久化 RSI。边界辨析见 [02 · 分类与技术栈](02-taxonomy.md)。

---

[← 上一章：执行摘要](00-overview.md) · [返回目录](../README.md) · [下一章：分类与技术栈 →](02-taxonomy.md)
