<div align="center">

# Awesome RSI

**Recursive Self-Improvement（递归自我改进）技术地图与精选清单**

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)
![Updated](https://img.shields.io/badge/updated-2026--09-blue)
![Status](https://img.shields.io/badge/status-actively%20maintained-green)

*从 Self-Refinement、Harness Evolution 到 Autonomous AI Research。*

*关键数据均对照论文 / 官方仓库逐项核实；未核实项显式标注。*

</div>

---

## 这份仓库是什么

本仓库不是项目名堆砌，而是一套 **RSI 技术地图**：把 Data / Model / Harness / Evaluator / Research Process 放进统一框架，区分「已经验证的技术进展」与「未来推演」，并持续跟踪基准测试、综述与产业信号。

组织方法：**分层（L1–L8）× 多轴分类（改什么 × 闭环程度 × 接地极性）× 证据等级**。

- 想看**结论**：从 [执行摘要](docs/00-overview.md) 开始。
- 想理解**怎么分类**：看 [分类与技术栈](docs/02-taxonomy.md)。
- 想查**某个项目**：看 [系统与项目地图](docs/12-systems.md)。
- 想查**某个 Benchmark**：看 [Benchmark 生态](docs/11-benchmarks.md)。
- 想看**综述与同类清单**：看 [Survey 与相关清单](docs/19-surveys.md)。
- 想知道**证据可信度**：看 [证据等级与数据核实](docs/15-evidence.md)。

---

## 目录导航

### 第一部分 · 基础与框架

| 文档 | 回答的问题 |
|---|---|
| [00 · 执行摘要与边界](docs/00-overview.md) | 2026 年 RSI 到底走到了哪一步？ |
| [01 · 理论基础](docs/01-foundations.md) | Gödel Machine 与理论 RSI 从何而来？ |
| [02 · 分类与技术栈](docs/02-taxonomy.md) | 术语界定；多轴分类（what × closure × polarity）；L1–L8 技术栈 |
| [03 · 技术发展史](docs/03-history.md) | 五个阶段与关键里程碑时间轴 |
| [04 · 统一架构与 Evaluator](docs/04-architecture.md) | 一个 RSI 系统由哪些模块构成？如何验证改进？ |

### 第二部分 · 技术栈各层

| 文档 | 被改进对象 | 代表工作 |
|---|---|---|
| [05 · 数据生态](docs/05-data.md) | 数据形态 | Executable Task / Research Repo / Trajectory / Experience |
| [06 · Harness 与 Memory RSI](docs/06-harness-rsi.md) | 脚手架 / 记忆 | STOP、DGM、ModularRSI、RRSI、SoL-Pi、Recuris、RSIAgent |
| [07 · Data RSI](docs/07-data-rsi.md) | 训练数据 | RSIBench-Data、PostTrainBench |
| [08 · Model RSI](docs/08-model-rsi.md) | 模型权重 | SEAL、NeoHorse-1、HyperAgents、ScienceBuddy |
| [09 · Algorithm RSI](docs/09-algorithm-rsi.md) | 学习算法 | AI4AI-Bench、OpenRSI / OpenMLE / Frontis-MA1 |
| [10 · Meta-RSI 与 Search RSI](docs/10-meta-rsi.md) | 搜索 / 改进策略 | Dream-RSI、MetaRSI、SIFT |

### 第三部分 · 生态

| 文档 | 内容 |
|---|---|
| [11 · Benchmark 生态](docs/11-benchmarks.md) | 横向对比、前沿实验室评测框架、基线成绩 |
| [12 · 系统与项目地图](docs/12-systems.md) | 前沿论文地图、2026 新项目与项目梯队 |
| [13 · 产业与组织](docs/13-industry.md) | Frontier Labs、创业公司、产业链分层 |

### 第四部分 · 展望与可信度

| 文档 | 内容 |
|---|---|
| [14 · 瓶颈与路线图](docs/14-outlook.md) | 六大瓶颈、1–2 年 / 3–5 年路线、商业机会 |
| [15 · 证据等级与核实](docs/15-evidence.md) | E0–E5 证据等级、数据核实说明、引用来源 |

### 第五部分 · 专题与索引

| 文档 | 内容 |
|---|---|
| [16 · 理论与经济学](docs/16-theory.md) | GAI 形式框架、RSI 经济学、极限与开放问题 |
| [17 · 安全、对齐与治理](docs/17-safety.md) | misevolution、防御护栏、前沿实验室治理框架 |
| [18 · 具身与物理自改进](docs/18-embodied.md) | 具身 RSI 范式、代表系统、与软件 RSI 的差异 |
| [19 · Survey 与相关清单](docs/19-surveys.md) | 综述索引、相关 awesome 清单对比、组织方法 |

---

## 核心结论速览

2026 年 RSI 最重要的判断，不是「AI 是否已实现无限递归自我进化」——公开证据并不支持这一结论——而是：

> **AI 开始进入「制造下一代 AI」的反馈循环。**

1. **Harness RSI 是最容易工程化的路线**：自动修改 Prompt、Skills、Tool Usage、Context、Memory、Agent Loop 等非权重组件。
2. **RSI Benchmark 开始成熟**：Hidden Evaluation、冻结 Repository、Held-out Task 被用来区分「真自我改进」与 Benchmark Overfitting。
3. **RSI 从 Harness 向 Data / Model / Training Algorithm 扩展**：MetaRSI、ScienceBuddy、OpenRSI 尝试建立跨层闭环。
4. **Frontier Labs 开始量化 AI 自动化 AI Research 的比例**：Anthropic 2026-08 内部指标显示 Claude「主导」约 26% 的 AI R&D 工作，90%+ 至少达到人机协作，但尚无类别达到完全无人监督。
5. **Automated AI Research 成为 Frontier Lab 的显式方向**：OpenAI 已设立专门的 Recursive Self-Improvement 团队。

> 一句话：**RSI 正从概念阶段进入 Infrastructure Stage。**

---

## 边界定义

| 概念 | 是什么 | 举例 |
|---|---|---|
| **Dataset / Task** | 数据与任务源 | GitHub Issues、Kaggle 竞赛、Nature 论文 |
| **Benchmark** | 数据 + 评测协议 + 阈值包装成的评价体系 | SWE-bench、MLE-bench、NatureBench |
| **RSI System** | 会修改自身、再被 benchmark 检验的系统 | DGM、Gödel Agent、OpenRSI |

> SWE-bench / MLE-bench 本身**不是** RSI；DGM、OpenRSI 这类系统才是。
> **「强 RSI」**：系统能修改构成自身能力的关键部分，并经执行反馈反复产生后继版本。单纯的 Self-Reflection / Self-Critique 不算。

详见 [02 · 分类与技术栈](docs/02-taxonomy.md)。

---

## Contributing

欢迎 PR。新增条目请遵循：

- 提供**论文 / 官方仓库一手来源**，并标注可验证的 benchmark 分数。
- 区分 Dataset / Benchmark / RSI System，勿混用。
- 分数如来自二手资料，请标注「待独立复核」。
- 新内容请归入 `docs/` 对应章节，并在本 README 导航中登记。

---

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/80x15.png)](https://creativecommons.org/publicdomain/zero/1.0/)

To the extent possible under law, maintainers have waived all copyright on this list.
