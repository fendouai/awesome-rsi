[← 上一章：系统与项目地图](12-systems.md) · [返回目录](../README.md) · [下一章：瓶颈与路线图 →](14-outlook.md)

---

# 13 · 产业与组织

> RSI 不仅存在于论文里。真正值得关注的指标是：Frontier Lab 内部，AI 已经自动化了多少 AI Research？

---

## 1. Frontier Labs 正在成为 RSI 最大实验场

这可能比 Parameter Count、Context Length、Benchmark Score 更接近 RSI 的真实进度。

### Anthropic：AI R&D Automation Index

Anthropic 2026 年公开了一套 **R&D Automation Index**，使用 Epoch AI 的 Automation Level：

```text
AL0   No AI
AL1
AL2
AL3   AI Collaborates
AL4   AI Leads
AL5   Fully Autonomous
```

截至 2026 年 8 月：

- Claude **主导约 26% 的 Anthropic AI R&D 工作**。
- 达到至少 AI Collaborates 的：**超过 90%**。
- 但：**目前没有任何测量类别达到 AL5 完全自主研究**。([Anthropic][1])

> 这个指标极其重要：RSI 第一次开始拥有类似 **AI R&D Automation Rate** 的现实世界进度指标。

### OpenAI：RSI 已成为正式研究团队

OpenAI 当前公开招聘 Research Engineer / Research Scientist / AI Systems Engineer, RSI。其 RSI Team 的公开目标包括：

- automate real research workflows
- research judgment
- hypothesis generation
- hypothesis testing
- long-horizon experiment execution
- model failure → data/evaluation flywheel

([OpenAI][2])

OpenAI 2026 年 9 月还公开表示，其目标是构建能够在人类监督下推进 Deep Learning 与 Alignment 的 automated AI researcher。([OpenAI][13])

> 这说明 **Automated AI Research 已不再只是外围研究，而成为 Frontier Lab 的核心能力建设。**

---

## 2. RSI 公司生态

2026 年出现了一批更加直接围绕 Self-Improvement 建立的公司。

### Recursive Superintelligence

Richard Socher 创立，是目前最明确押注 **Open-ended Self-Improving AI** 的公司之一。2026 年 5 月走出 stealth 时获得约 **6.5 亿美元融资**，随后与 AWS 签署约 **4.1 亿美元多年 Compute Deal**。([TechCrunch][14])

### Deep Cogito

路线偏 **Post-Training + Reinforcement Learning + Self-Improvement**。2026 年 8 月宣布 **4300 万美元 Series A**，累计融资超过 **5600 万美元**。定位为「Post-Training Engine for Frontier Intelligence」。([Nasdaq][15])

```text
Foundation Model
↓
Self-Improvement Engine
↓
Better Model
```

未来 AI Infra 很可能出现一个新的层级：**Continuous Intelligence Improvement Layer。**

### Ineffable Intelligence

David Silver 创建，代表 **Experience-driven Self-Improvement**。公司强调 Experiential、Continual、General、Self-improving，核心观点是：超级智能最终更多依赖从 Environment 中获得 Experience，而不是完全依赖人类已经生成的数据。([Ineffable AI][16])

```text
Experience
↓
Continual RL
↓
Superlearner
```

---

## 3. RSI 产业链正在出现

```text
┌─────────────────────────┐
│ Meta-RSI                │  Research Strategy
├─────────────────────────┤
│ AI Researcher           │
├─────────────────────────┤
│ Evaluator / Verifier    │
├─────────────────────────┤
│ Harness Evolution       │
├─────────────────────────┤
│ Memory / Skills         │
├─────────────────────────┤
│ Data Evolution          │
├─────────────────────────┤
│ Model Post-Training     │
├─────────────────────────┤
│ Experiment Sandbox      │
├─────────────────────────┤
│ Compute Infrastructure  │
└─────────────────────────┘
```

几乎每一层未来都有机会形成独立产品甚至公司。具体机会分析见 [14 · 瓶颈与路线图](14-outlook.md)。

---

## 4. 值得持续跟踪的组织

**研究与 Frontier Labs**

```text
OpenAI RSI    Anthropic    Google DeepMind
FrontisAI     CosmosMind   Evolvent AI
```

**创业公司**

```text
Recursive Superintelligence   Deep Cogito   Ineffable Intelligence
```

---

[← 上一章：系统与项目地图](12-systems.md) · [返回目录](../README.md) · [下一章：瓶颈与路线图 →](14-outlook.md)

[1]: https://www.anthropic.com/institute/measuring-pace-of-ai-development
[2]: https://openai.com/careers/research-engineer-research-scientist-ai-systems-engineer-rsi-san-francisco/
[13]: https://openai.com/index/research-acceleration-view-inside-openai/
[14]: https://techcrunch.com/2026/07/28/recursive-superintelligence-signs-400-compute-deal-with-amazon/
[15]: https://www.nasdaq.com/press-release/deep-cogito-raises-43m-series-advance-post-training-engine-frontier-intelligence-2026
[16]: https://www.ineffable.ai/
