[← 上一章：Benchmark 生态](11-benchmarks.md) · [返回目录](../README.md) · [下一章：产业与组织 →](13-industry.md)

---

# 12 · 系统与项目地图

> 把 RSI 前沿工作按「研究方向」和「成熟梯队」两轴组织。

---

## 1. 前沿论文地图（六条线）

### ① Survey / Theory

- **Recursive Self-Improvement in AI** — 1,250 篇论文的大规模 Survey，建立 `What is improved × Loop closure` 框架。([arXiv][3])
- **The Last AI Built by Humans** — 提出 Headroom-Closed Index（HCI）与五级自主性路线。([arXiv][12])

### ② Harness RSI

代表：ModularRSI、Recuris、OpenRSI。
核心问题：AI 能否改进自己的 Agent Architecture？→ [06](06-harness-rsi.md)

### ③ Data RSI

代表：RSIBench-Data。
核心问题：AI 能否自己研究什么数据最值得训练？→ [07](07-data-rsi.md)

### ④ Model + Harness RSI

代表：ScienceBuddy。
核心问题：Model 与 Harness 能否相互推动？→ [08](08-model-rsi.md)

### ⑤ Algorithm RSI

代表：AI4AI-Bench。
核心问题：AI 能否发明 AI Training Algorithm？→ [09](09-algorithm-rsi.md)

### ⑥ Meta-RSI

代表：Dream-RSI、MetaRSI。
核心问题：AI 能否改善「改善 AI 的过程」？→ [10](10-meta-rsi.md)

---

## 2. 项目地图

### Harness Evolution

- ModularRSI（[arXiv 2609.14857](https://arxiv.org/abs/2609.14857)）
- OpenRSI
- Recuris
- RRSI（[google-research/rrsi](https://github.com/google-research/rrsi)）
- SoL-Pi（[NVlabs/SoL-Pi](https://github.com/NVlabs/SoL-Pi)）
- AutoHarness、Continual Harness、MetaSkill-Evolve、SkillOpt、Agentic Harness Engineering
- RSI-Harness

### Model RSI

- SEAL
- NeoHorse-1（[TokenRhythm/NeoHorse](https://github.com/TokenRhythm/NeoHorse)）
- HyperAgents（[facebookresearch/HyperAgents](https://github.com/facebookresearch/HyperAgents)）
- SIA（[hexo-ai/sia](https://github.com/hexo-ai/sia)）

### Memory RSI

- Recuris
- RSIAgent（[AetherLabsAI/RSIAgent](https://github.com/AetherLabsAI/RSIAgent)）
- ACE、EvolveR、ExpeL

### AI4AI / Automated Research

- OpenMLE / Frontis-MA1
- ScienceBuddy（[Gen-Verse/ScienceBuddy](https://github.com/Gen-Verse/ScienceBuddy)）
- The AI Scientist-v2、MLEvolve、AutoResearch、RD-Agent、RSIHub

### Data RSI

- RSIBench-Data
- PostTrainBench、DataChef、FT-Dojo

### Meta-RSI / Search RSI

- Dream-RSI（[zhengkid/Dream-RSI](https://github.com/zhengkid/Dream-RSI)）
- MetaRSI（[arXiv 2609.06396](https://arxiv.org/abs/2609.06396)）
- SIFT（[arXiv 2609.19526](https://arxiv.org/abs/2609.19526)）

### Benchmark

- RSI-Exam、AI4AI-Bench、RSIBench-Data、Scale RSI Bench
- MLS-Bench、AutoLab、PostTrainBench、MLAgentBench、SAEScientist-Bench
- NatureBench、PaperBench、MLE-Bench、SWE-Bench、Terminal-Bench、OSWorld 2.0

### 相关清单

- lobehub/awesome-rsi、KaiWU5/Awesome-AI4AI、ANative-Lab/Awesome-Self-Evolving-Agents 等，对比见 [19 · Survey 与相关清单](19-surveys.md)。

---

## 3. 2026 值得关注的新项目

| 项目 | 类别 | 为何值得关注 |
|---|---|---|
| **RRSI** | Harness RSI | 首个把**正则化**系统引入 harness 自改进，显式对抗 benchmark 过拟合 |
| **SoL-Pi** | Harness RSI | 把 auto-research loop 推向 **token 效率**，接近生产可用 |
| **NeoHorse-1** | Model RSI | routing harness 驱动的 agentic post-training，闭合评测–选择–更新环 |
| **HyperAgents** | Model/Meta RSI | 自我修改过程本身可演化并跨域迁移 |
| **SIA** | Harness+Model | 同一循环内同时更新 harness 与权重 |
| **ModularRSI** | Harness RSI | benchmark-disjoint + 模块化，直指 credit assignment |
| **SIFT** | Search RSI | 用 judge 信号缓解自修改评测瓶颈 |
| **RSIAgent** | Memory RSI | broad-then-deep 探索，记忆冻结后可复用 |

---

## 4. 项目梯队

**第一梯队（核心研究项目）**

```text
OpenRSI        ModularRSI     Recuris
Dream-RSI      MetaRSI        ScienceBuddy
RSIBench-Data  RSI-Exam       AI4AI-Bench
```

**长期观察**

```text
OpenMLE   Frontis-MA1   RSI-Harness   NatureBench
```

---

## 5. Systems 清单（按世代）

按世代分组，不按成绩排名。

### ① Scaffold 层自改进（2023–2025）

- [STOP](https://github.com/microsoft/stop) — Self-Taught Optimizer（Microsoft，2023）
- [ADAS](https://github.com/ShengranHu/ADAS) — Automated Design of Agentic Systems（ICLR 2025）
- [Gödel Agent](https://github.com/Arvid-pku/Godel_Agent) — Self-Referential Agent（ACL 2025）
- [SICA](https://github.com/MaximeRobeyns/self_improving_coding_agent) — Self-Improving Coding Agent（2025）
- [Darwin Gödel Machine (DGM)](https://github.com/jennyzzt/dgm) — 开放进化（2025）

### ② 权重层自改进（2025）

- [SEAL](https://github.com/Continual-Intelligence/SEAL) — Self-Adapting Language Models
- [Agent0](https://github.com/aiming-lab/Agent0) — Self-Evolving Agents from Zero Data

### ③ AI4AI（2026）

- [OpenRSI / OpenMLE / Frontis-MA1](https://github.com/FrontisAI/OpenRSI) — meta-evolution model

各系统机制与成绩详见 [06](06-harness-rsi.md) / [08](08-model-rsi.md) / [09](09-algorithm-rsi.md) 与 [11 · Benchmark 生态](11-benchmarks.md)。

---

[← 上一章：Benchmark 生态](11-benchmarks.md) · [返回目录](../README.md) · [下一章：产业与组织 →](13-industry.md)

[3]: https://arxiv.org/abs/2607.07663
[12]: https://arxiv.org/abs/2609.11873
