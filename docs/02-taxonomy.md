[← 上一章：理论基础](01-foundations.md) · [返回目录](../README.md) · [下一章：技术发展史 →](03-history.md)

---

# 02 · 分类与技术栈

> 真正需要关注的不是名字中有没有 RSI，而是：改了什么、是否持久、改进后的系统是否参与下一轮改进。

---

## 1. RSI 与相邻概念的边界

今天很多项目都使用 Self-Refine、Self-Evolve、Self-Improve、Self-Train、Self-Play、AutoResearch 等概念，但它们并不完全等价。

2026 年发布的大型 RSI Survey 调查了 2024–2026 年约 1,250 篇相关 arXiv 论文，将这些工作按两个维度整理：

1. **系统修改什么**
2. **Improvement Loop 闭合到什么程度**

并明确区分了已经非常成熟的 bounded self-refinement 与真正开放式 RSI。([arXiv][3])

| 技术 | 是否持久改变系统 | 是否形成递归闭环 | RSI 程度 |
|---|---:|:---:|---|
| Self-Critique | 否 | 否 | 很低 |
| Self-Refine | 否 | 否 | 很低 |
| Prompt Optimization | 是 | 部分 | 低 |
| Memory Evolution | 是 | 是 | 中 |
| Harness Evolution | 是 | 是 | 中高 |
| Synthetic Data Training | 是 | 部分 | 中 |
| Data RSI | 是 | 是 | 高 |
| Model RSI | 是 | 是 | 高 |
| Training Algorithm Discovery | 是 | 是 | 很高 |
| Meta-RSI | 是 | Improvement Operator 也改变 | 最高 |

判断一个系统是否属于 RSI，只需回答三个问题：

> **What changes？**
>
> **Does it persist？**
>
> **Does the improved system participate in the next improvement cycle？**

---

## 2. RSI 的七层技术栈

从「被修改对象」看，可以建立一个更加工程化的 RSI Stack。

| Level | 层 | 被修改对象 | 典型技术 |
|---|---|---|---|
| **L1** | Output | 答案 / Code | Self-Refine |
| **L2** | Prompt | Instruction | Prompt Optimization |
| **L3** | Memory | Skills / Experience | Recuris |
| **L4** | Harness | Loop / Tool / Context | ModularRSI |
| **L5** | Data | Training Data | RSIBench-Data |
| **L6** | Model | Model Weight | RL / SFT（SEAL、Agent0） |
| **L7** | Research | Search / Algorithm / Evaluator | Dream-RSI / AI4AI |

再往上一层：

### L8 · Meta-RSI

系统开始决定：

> 下一轮究竟应该修改哪一层？

这一层对应 MetaRSI 的组合优化与 Dream-RSI 的搜索策略改进，详见 [10 · Meta-RSI 与 Search RSI](10-meta-rsi.md)。

---

## 3. 技术成熟度

截至目前，各层成熟度大致如下（条形越长越成熟）：

```text
Self-Refinement          ██████████
Prompt Optimization      █████████
Memory Evolution         ████████
Harness Evolution        ███████
Data RSI                 ██████
AI Research Automation   █████
Model RSI                ████
Algorithm RSI            ███
Meta-RSI                 ██
Open-ended RSI           █
```

> 最大的误区是：把所有 Self-Improvement 都理解为「模型重新训练自己」。
> 实际上目前发展最快的是 **Harness + Memory + Data + Research Automation**。

---

## 4. 2026 RSI Landscape

把目前主要研究放入统一地图：

| 方向 | 代表工作 | 成熟度 |
|---|---|---|
| Self-Refinement | Reflexion 等 | 高 |
| Memory RSI | Recuris | 中高 |
| Harness RSI | ModularRSI / OpenRSI | 中高 |
| Data RSI | RSIBench-Data | 中 |
| Model RSI | ScienceBuddy | 中低 |
| Algorithm RSI | AI4AI-Bench | 早期 |
| AI Research | RSI-Exam / OpenAI RSI | 中早期 |
| Search RSI | Dream-RSI | 早期 |
| Meta-RSI | MetaRSI | 早期 |
| Open-ended RSI | — | 未实现 |

各层的展开阅读：

- [06 · Harness 与 Memory RSI](06-harness-rsi.md)
- [07 · Data RSI](07-data-rsi.md)
- [08 · Model RSI](08-model-rsi.md)
- [09 · Algorithm RSI](09-algorithm-rsi.md)
- [10 · Meta-RSI 与 Search RSI](10-meta-rsi.md)

---

[← 上一章：理论基础](01-foundations.md) · [返回目录](../README.md) · [下一章：技术发展史 →](03-history.md)

[3]: https://arxiv.org/abs/2607.07663
