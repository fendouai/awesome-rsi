[← 上一章：具身与物理自改进](18-embodied.md) · [返回目录](../README.md)

---

# 19 · Survey 与相关清单

> 2026 年 RSI 相关综述密集出现。它们各自的分类轴，正是本仓库组织方法的来源与对照。

---

## 1. Survey 索引

### 核心 RSI / 自我改进

| arXiv | 标题 | 分类框架 |
|---|---|---|
| [2607.07663][3] | Recursive Self-Improvement in AI: From Bounded Self-Refinement to Autonomous Research Loops | 改什么（deployment / training / evaluator / research）× 闭环程度；自评估单列一类；验证层级 |
| [2607.13104](https://arxiv.org/abs/2607.13104) | Self-Improvements in Modern Agentic Systems: A Survey | Agent = 基础模型 + 操作脚手架；按更新目标 × 驱动信号 |
| [2609.01679](https://arxiv.org/abs/2609.01679) | A Survey on Self-Improving Test-Time Intelligence | 统一 test-time adaptation / learning / scaling |
| [2601.12538](https://arxiv.org/abs/2601.12538) | A Survey of Agentic Reasoning for LLMs: Towards Recursively Self-Improving and Collective Agents | 三层（基础 / 自演化 / 集体）× in-context vs post-training |
| [2412.14352](https://arxiv.org/abs/2412.14352) | A Survey on LLM Inference-Time Self-Improvement | Independent / Context-Aware / Model-Aided |
| [2404.14387](https://arxiv.org/abs/2404.14387) | A Survey on Self-Evolution of Large Language Models | 四阶段：经验获取 / 精炼 / 更新 / 评估 |

### 自演化 Agent

| arXiv | 标题 | 分类框架 |
|---|---|---|
| [2507.21046](https://arxiv.org/abs/2507.21046) | A Survey of Self-Evolving Agents: What, When, How, and Where to Evolve | what / when / how 三维（TMLR 2026） |
| [2508.07407](https://arxiv.org/abs/2508.07407) | A Comprehensive Survey of Self-Evolving AI Agents | 统一反馈环：System Inputs、Agent System、Environment、Optimisers |
| [2608.18104](https://arxiv.org/abs/2608.18104) | Self-Evolving Agents as Dynamic Graph Transformation | 图变换四类：node / edge / subgraph / cross-component |
| [2608.03392](https://arxiv.org/abs/2608.03392) | Self-Evolving Coding Agents | 演化目标 ×（何时演化 × 代码信号） |
| [2602.06052](https://arxiv.org/abs/2602.06052) | A Survey of Agent Memory | memory substrate × cognitive mechanism × subject |

### 自动化研究 / AI Scientist

| arXiv | 标题 | 分类框架 |
|---|---|---|
| [2608.05179](https://arxiv.org/abs/2608.05179) | Autonomous Research Agents: A Survey of AI Scientists and the Verification Gap | 7 审计维度；lifecycle × autonomy 图 |
| [2608.14407](https://arxiv.org/abs/2608.14407) | The Past and Future of AI Scientists | 把 AI Scientist 视为集成问题；Nobel Turing Challenge |
| [2606.23175](https://arxiv.org/abs/2606.23175) | Position: Correct Answer, Wrong Mechanism | 分离 outcome / mechanism fidelity / epistemic honesty |

### 验证、安全与理论

| arXiv | 标题 | 分类框架 |
|---|---|---|
| [2609.00069](https://arxiv.org/abs/2609.00069) | Auditing Harness Tampering in Self-Improving Agents | harness 功能角色 × 被违反义务 |
| [2609.02246](https://arxiv.org/abs/2609.02246) | LLM-as-a-Judge Is Not an Oracle | 四类失败：judge 偏差、harness/指标、ground-truth、reward hacking |
| [2609.13406][17] | Generalized Agent Iteration | 形式框架；两旋钮；极性分类 |
| [2609.15802](https://arxiv.org/abs/2609.15802) | The Economics of Recursive Self-Improvement | 弹性网络；narrow vs broad |
| [2608.27505](https://arxiv.org/abs/2608.27505) | A Survey on Rubric-Guided RL | prior–posterior 轴 |

> 检索方式：`http://export.arxiv.org/api/query?search_query=all:"recursive self-improvement"`（截至 2026-09 约 88 条）。

---

## 2. 相关清单对比

同类精选清单的组织方法差异，值得对照。星数为 GitHub API 于 2026-09 读取，会随时间变化。

| 清单 | 星数 | 组织方法 |
|---|---|---|
| [ANative-Lab/Awesome-Self-Evolving-Agents](https://github.com/ANative-Lab/Awesome-Self-Evolving-Agents) | ~2.5k | 以综述为纲，覆盖自演化 Agent 全景 |
| [selfimproving-agent/Awesome-Self-Improving-Agents](https://github.com/selfimproving-agent/Awesome-Self-Improving-Agents) | ~500 | 面向基础模型 Agentic 系统的自我改进 |
| [XMUDeepLIT/Awesome-Self-Evolving-Agents](https://github.com/XMUDeepLIT/Awesome-Self-Evolving-Agents) | ~449 | 综述 + 资源 |
| [ResearAI/Awesome-AI-Scientist](https://github.com/ResearAI/Awesome-AI-Scientist) | ~314 | AI Scientist / Researcher / Engineer 综述 |
| [lobehub/awesome-rsi](https://github.com/lobehub/awesome-rsi) | ~303 | **按层分类**：model / harness / multi-agent / coding / automated R&D / embodied / evolutionary / safety / introspection / benchmarks；含 Scope & Terminology |
| [FrontisAI/Awesome-Self-Improving-Agents](https://github.com/FrontisAI/Awesome-Self-Improving-Agents) | ~266 | 清单 + 综述站点 |
| [EvoMap/awesome-agent-evolution](https://github.com/EvoMap/awesome-agent-evolution) | ~229 | agent evolution / memory / multi-agent |
| [KaiWU5/Awesome-AI4AI](https://github.com/KaiWU5/Awesome-AI4AI) | ~171 | AI4AI 综述（223 篇）：长程 Agent、benchmark、harness 设计、RSI |
| [cocacola-lab/awesome-embodied-rsi](https://github.com/cocacola-lab/awesome-embodied-rsi) | ~119 | 具身 RSI：系统 / benchmark |
| [leezythu/Awesome-Harness-Self-Improvement](https://github.com/leezythu/Awesome-Harness-Self-Improvement) | ~99 | Harness 工程视角 |
| [theseus-labs-rsi/awesome-rsi](https://github.com/theseus-labs-rsi/awesome-rsi) | ~107 | RSI 论文 / 资源 |
| [Persdre/awesome-recursive-self-improvement](https://github.com/Persdre/awesome-recursive-self-improvement) | ~5 | **定义优先**：what is modified × loop closure |

> 组织方法大致分三派：**平铺论文列表**、**按被修改组件分层**、**按证据/闭环分级的 map**。本仓库采用「分层（L1–L8）+ 多轴（what × closure × polarity）+ 证据等级」的混合结构。

---

## 3. 本仓库的组织方法

```text
第一部分 基础与框架   定义 → 理论 → 分类 → 历史 → 架构
第二部分 技术栈各层   L1–L8 逐层展开
第三部分 生态         Benchmark → 项目地图 → 产业
第四部分 展望与可信度 瓶颈路线 → 证据等级
第五部分 专题         理论 → 安全 → 具身 → Survey 索引
```

选择这一结构的原因：

1. **分层**回答「改哪一层」，与工程直觉一致。
2. **多轴**回答「算不算 RSI、有多闭环、是否接地」，避免名词混用。
3. **证据等级**回答「能不能信」，应对营销与论文混杂。
4. **专题**承接横切议题（安全、具身、理论），避免在主线上打断叙事。

---

[← 上一章：具身与物理自改进](18-embodied.md) · [返回目录](../README.md)

[3]: https://arxiv.org/abs/2607.07663
[17]: https://arxiv.org/abs/2609.13406
