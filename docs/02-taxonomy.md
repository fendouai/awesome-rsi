[← 上一章：理论基础](01-foundations.md) · [返回目录](../README.md) · [下一章：技术发展史 →](03-history.md)

---

# 02 · 分类与技术栈

> 真正需要关注的不是名字中有没有 RSI，而是：改了什么、是否持久、改进后的系统是否参与下一轮改进。

本章提供三套互补的组织工具：**术语界定** → **多轴分类矩阵** → **L1–L8 技术栈**。前两者回答「它算不算 RSI」，后者回答「它改的是哪一层」。

---

## 1. 术语界定

不同论文对「自我改进」的用法差异极大。本仓库采用以下操作性区分：

| 术语 | 定义 | 是否持久 |
|---|---|---|
| **Self-Refinement** | 改进当前输出，系统本身不变 | 否 |
| **Persistent Self-Improvement** | 对 weights / memory / skills / prompts / harness / code 的修改会带入下一轮 | 是 |
| **Recursive Self-Improvement (RSI)** | 产生改进的**机制本身**也成为被改进的对象 | 是，且机制递归 |
| **RSI Substrate** | 把 Agent 自身结构暴露为可修改对象，但默认不自动形成改进闭环 | 视配置 |

> 一个系统可以是 RSI 的**底座（substrate）**，却尚未构成 RSI。例如可扩展的 Agent Runtime 暴露了 prompt / tool / skill / memory 的修改接口，但要真正闭环，还需要 proposer、evaluator、selection 与 persistence。

---

## 2. 多轴分类矩阵

单一维度无法刻画 RSI。本仓库综合 2026 年三项关键工作，采用**三轴**定位：

### 轴 A · 改什么（What is improved）

来自 1,250 篇论文的大规模 Survey（[arXiv 2607.07663][3]）：

| 类别 | 对象 | 典型 |
|---|---|---|
| **Deployment-time self-evolution** | 输出 / 上下文 / harness / skill / memory（权重冻结） | Reflexion、ACE、ModularRSI |
| **Training-time self-iteration** | 自生成数据 / 奖励 / 教师信号更新权重 | STaR、SEAL、NeoHorse-1 |
| **Self-evaluation** | Evaluator 本身（judge / verifier / rubric / PRM） | Self-Rewarding、Meta-Rewarding |
| **Auto Research** | 研究过程本身（假设、实验、算法发现） | AI Scientist、AI4AI-Bench |

> Survey 的独特之处是为**自评估**单列一类：每一个改进循环，本质都是一个「某信号可以替代人类判断」的断言。

### 轴 B · 闭环程度（Loop closure）

谁来做最终验证：

```text
human-in-the-loop  →  human-on-the-loop  →  closed loop
（人类参与）           （自动信号+人类审计）    （无人类复核）
```

这条轴区分了**bounded self-refinement**（外部 evaluator 固定、收敛）与**open-ended RSI**（修改自身判据、原理上发散）。

### 轴 C · 接地极性（Grounding polarity）

来自 Generalized Agent Iteration（GAI，[arXiv 2609.13406][17]）。把系统建模为 `χ = (π, V, m, U, ρ)`：策略 π、动作 critic V、修改器 m、修改 critic U、评价基准 ρ。两个「旋钮」决定性质：

- **旋钮一**：改进机制 `m` 是否属于 Agent 本身？外部 ⇒ GPI（经典策略迭代）；内部 ⇒ RSI。
- **旋钮二**：评价基准 `ρ` 是否外接接地？

由此得到三种极性：

| 极性 | 特征 | 例子 |
|---|---|---|
| **Anchored（锚定）** | ρ 外接且不可被改，朝固定外部标准改进 | Gödel Machine、STOP、Gödel Agent、DGM、SICA |
| **Goal Drift（目标漂移）** | 外接目标存在，但 ρ 可被 Agent 改写 | Red Queen Gödel Machine（evaluator 共进化） |
| **Self-Referential（自指）** | 无外部信号，critic 退化为内部自洽 | Socratic learning 类设计 |

> 轴 C 的价值：它把 RSI 的**风险**（目标漂移、自证循环）变成可陈述的坐标，而不是笼统的担忧。

---

## 3. 验证层级（Verification Hierarchy）

Evaluator 是 RSI 最核心的基础设施。2026 Survey 把验证信号从强到弱排序：

```text
1. Formal Verifiers        形式证明、类型系统（构造上可靠）
        ↓
2. Execution Feedback      测试、编译器、benchmark（可靠但不完备）
        ↓
3. Learned Judges          reward model、LLM-as-judge（受 judge 能力限制，且自身可被优化）
        ↓
4. Intrinsic Signals       confidence、self-consistency、likelihood（最廉价、最易被 hack）
```

两条经验规律：

1. **已观察到的自我改进强度，与验证信号在层级中的位置正相关。** FunSearch / AlphaEvolve 位于第 1–2 层；AI Scientist 的差距则是「用第 3 层工具解决第 4 层问题」。
2. **层级排序的是「给定目标后如何验证」；而「哪个方向值得验证」在逻辑上更靠前，且不由层级决定**——这正是 research taste 的难点。

Evaluator 设计空间（judge、PRM、verifier、rubric、meta-evaluation）与工程实践详见 [04 · 统一架构与 Evaluator](04-architecture.md)。

---

## 4. RSI 的七层技术栈

从「被修改对象」看，可以建立一个工程化的 RSI Stack。

| Level | 层 | 被修改对象 | 典型技术 |
|---|---|---|---|
| **L1** | Output | 答案 / Code | Self-Refine |
| **L2** | Prompt | Instruction | Prompt Optimization |
| **L3** | Memory | Skills / Experience | Recuris |
| **L4** | Harness | Loop / Tool / Context | ModularRSI |
| **L5** | Data | Training Data | RSIBench-Data |
| **L6** | Model | Model Weight | SEAL、NeoHorse-1 |
| **L7** | Research | Search / Algorithm / Evaluator | Dream-RSI / AI4AI |
| **L8** | Meta | 「下一轮改哪一层」 | MetaRSI |

各层的展开阅读：

- [06 · Harness 与 Memory RSI](06-harness-rsi.md)
- [07 · Data RSI](07-data-rsi.md)
- [08 · Model RSI](08-model-rsi.md)
- [09 · Algorithm RSI](09-algorithm-rsi.md)
- [10 · Meta-RSI 与 Search RSI](10-meta-rsi.md)

---

## 5. 技术成熟度

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

## 6. 2026 RSI Landscape

| 方向 | 代表工作 | 成熟度 |
|---|---|---|
| Self-Refinement | Reflexion 等 | 高 |
| Memory RSI | Recuris、RSIAgent | 中高 |
| Harness RSI | ModularRSI / OpenRSI / RRSI / SoL-Pi | 中高 |
| Data RSI | RSIBench-Data | 中 |
| Model RSI | NeoHorse-1、ScienceBuddy | 中低 |
| Algorithm RSI | AI4AI-Bench | 早期 |
| AI Research | RSI-Exam / OpenAI RSI | 中早期 |
| Search RSI | Dream-RSI / SIFT | 早期 |
| Meta-RSI | MetaRSI | 早期 |
| Open-ended RSI | — | 未实现 |

---

[← 上一章：理论基础](01-foundations.md) · [返回目录](../README.md) · [下一章：技术发展史 →](03-history.md)

[3]: https://arxiv.org/abs/2607.07663
[17]: https://arxiv.org/abs/2609.13406
