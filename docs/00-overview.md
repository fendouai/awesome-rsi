[← 返回目录](../README.md) · [下一章：理论基础 →](01-foundations.md)

---

# 00 · 执行摘要与边界

> 2026 年，Recursive Self-Improvement（RSI，递归自我改进）正在经历一次重要的范式变化。

---

## 1. 从理论概念到工程问题

过去，RSI 更多是一个理论概念：

```text
AI 修改自身 → 获得更强能力 → 更强的 AI 再次修改自身
```

而截至 2026 年 9 月，公开研究已经开始把这一概念拆解成一系列**能够独立实验、执行、测量和 Benchmark 的工程问题**：

- AI 能否修改自己的 Prompt？
- 能否修改 Memory？
- 能否改进自己的 Agent Harness？
- 能否根据自身失败生成更好的训练数据？
- 能否训练出更强的下一代模型？
- 能否发明新的训练算法？
- 能否自动设计并执行 AI Research？
- 能否最终改进「改进 AI 的方法」本身？

这意味着 RSI 正在从：

> **一个关于 Superintelligence 的理论问题**

转变成：

> **一套关于 Automated AI R&D 的工程技术栈。**

---

## 2. 2026 年最值得关注的五点变化

**第一，Harness RSI 成为最容易工程化的 RSI 路线。** Agent 开始自动修改 Prompt、Skills、Tool Usage、Context Management、Memory、Agent Loop 等非权重组件。

**第二，RSI Benchmark 开始成熟。** RSI-Exam、AI4AI-Bench、RSIBench-Data 等工作开始使用 Hidden Evaluation、冻结 Repository、Held-out Task 等设计，判断所谓「自我改进」究竟是不是 Benchmark Overfitting。

**第三，RSI 从 Harness 向 Data、Model 和 Training Algorithm 扩展。** MetaRSI、ScienceBuddy、OpenRSI 等系统正在尝试建立跨层优化闭环。

**第四，Frontier Labs 开始公开测量 AI 自动化 AI Research 的比例。** Anthropic 2026 年 8 月的内部指标显示，Claude 已能够「主导」约 26% 的 AI R&D 工作，90% 以上的工作至少达到人机协作级别，但尚没有任何被测研究类别达到完全无人监督自动化。([Anthropic][1])

**第五，AI Research Automation 已经成为 Frontier Lab 的显式研究方向。** OpenAI 已设立专门的 Recursive Self-Improvement 团队，其公开岗位说明明确提出：构建能够加速并最终执行高质量研究的 AI 系统，包括 research judgment、hypothesis generation、experiment execution、feedback loop 等。([OpenAI][2])

---

## 3. 核心判断

2026 年 RSI 最重要的判断并不是：

> AI 是否已经实现无限递归自我进化？

目前公开证据并不支持这一结论。真正正在发生的是：

> **AI 开始进入「制造下一代 AI」的反馈循环。**

因此本报告的核心立场是：**RSI 正从概念阶段进入 Infrastructure Stage。** 今天真正成熟起来的是 Benchmark、Evaluator、Trajectory、Harness、Sandbox、Research Agent、Evolution Loop 这些组件；它们进一步支撑 Data RSI → Model RSI → Algorithm RSI → Meta-RSI 的递进。

详见 [14 · 瓶颈与路线图](14-outlook.md)。

---

## 4. 边界定义

本仓库严格区分三类对象，避免概念混用。

| 概念 | 是什么 | 举例 |
|---|---|---|
| **Dataset / Task** | 数据与任务源 | GitHub Issues、Kaggle 竞赛、Nature 论文 |
| **Benchmark** | 数据 + 评测协议 + 阈值包装成的评价体系 | SWE-bench、MLE-bench、NatureBench |
| **RSI System** | 会修改自身、再被 benchmark 检验的系统 | DGM、Gödel Agent、OpenRSI |

> SWE-bench / MLE-bench 本身**不是** RSI；DGM、OpenRSI 这类系统才是。
>
> **「强 RSI」**：系统能修改构成自身能力的关键部分，并经执行反馈反复产生后继版本。单纯的 Self-Reflection / Self-Critique 不算。

进一步的概念辨析见 [02 · 分类与技术栈](02-taxonomy.md)。

---

[← 返回目录](../README.md) · [下一章：理论基础 →](01-foundations.md)

[1]: https://www.anthropic.com/institute/measuring-pace-of-ai-development
[2]: https://openai.com/careers/research-engineer-research-scientist-ai-systems-engineer-rsi-san-francisco/
