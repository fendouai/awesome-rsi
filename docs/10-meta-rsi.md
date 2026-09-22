[← 上一章：Algorithm RSI](09-algorithm-rsi.md) · [返回目录](../README.md) · [下一章：Benchmark 生态 →](11-benchmarks.md)

---

# 10 · Meta-RSI 与 Search RSI

> 真正的临界点不是 AI 能优化自己的 Prompt，甚至也不是能训练自己的 Model，而是：**AI 能够改进 Improvement Operator 本身。**

---

## 1. 从单层优化到组合优化

[MetaRSI-v1](https://cosmosmind.ai/research/metarsi-v1)（CosmosMind）把 RSI 拆为三类 Operator：

- **Data-RSI** — 修改训练数据。
- **Harness-RSI** — 修改系统 Scaffold。
- **Model-RSI** — 修改参数。

然后由更高层 Policy 决定：

> 什么时候应该调用哪个 Operator？

这意味着 RSI 开始从：

```text
Optimize X
```

转变成：

```text
Decide
  WHAT to optimize
  WHEN to optimize
  HOW to optimize
```

MetaRSI-v1 明确提出统一 Loop Kernel，并将三类 Operator 进行组合。这对应技术栈中的 **L8 · Meta-RSI**（见 [02 · 分类与技术栈](02-taxonomy.md)）。

---

## 2. Dream-RSI：改进「搜索方法」

[Dream-RSI](https://www.dream-rsi.com/) 是当前 Meta-RSI 中非常值得关注的工作。

传统 Agent：

```text
Search → Solution
```

Dream-RSI：

```text
Search
↓
Discovery Tree
↓
Replay Simulator
↓
Improve Search Policy
↓
Better Search
```

系统把历史探索过程中形成的 **Discovery Tree** 作为一种 Replay World，然后：

> 在已经产生的历史搜索空间中模拟大量新的探索策略，而无需重新执行所有真实实验。

最后只有表现最好的 Policy 被重新部署。于是形成：

```text
Real Exploration
↓
History
↓
Dream
↓
Better Exploration Policy
↓
New Exploration
↓
More History
```

真正被进化的是：

> **How to explore。**

这是 RSI 从 **Solution Optimization** 迈向 **Search Optimization** 的重要一步。

---

## 3. Meta-RSI 的层级

```text
第一层：Optimize Solution
第二层：Optimize Solver
第三层：Optimize Search Strategy
第四层：Optimize Improvement Strategy
最终：  Improve How to Improve
```

这才是真正意义上的 **Recursive Self-Improvement**。

---

## 4. 理论标尺：The Last AI Built by Humans

[The Last AI Built by Humans](https://arxiv.org/abs/2609.11873) 提出 **Headroom-Closed Index（HCI）**，并给出 RSI 路线：

```text
Improvement Execution Autonomy
↓
Improvement Strategy Autonomy
↓
Experience Acquisition Autonomy
↓
Environment Adaptation Autonomy
↓
Recursive Meta-Improvement
```

这条路线为 Meta-RSI 提供了可比较的自主性刻度。

---

## 5. RSI 的增长飞轮

最终 RSI 可以表示为：

```text
        ┌───────────────────┐
        │    Better AI      │
        └────────┬──────────┘
                 ↓
        Better AI Research
                 ↓
        Better Experiments
                 ↓
        Better Training
                 ↓
        ┌───────────────────┐
        │    Better AI      │
        └────────┬──────────┘
                 ↓
              ...
```

数学上：

$$
AI_t \rightarrow R_t \rightarrow AI_{t+1}
$$

如果同时满足：

$$
AI_{t+1} > AI_t \quad \text{且} \quad R_{t+1} > R_t
$$

那么：

> AI 能力增长机制本身也在增长。

这是 RSI 最核心的意义。

---

[← 上一章：Algorithm RSI](09-algorithm-rsi.md) · [返回目录](../README.md) · [下一章：Benchmark 生态 →](11-benchmarks.md)
