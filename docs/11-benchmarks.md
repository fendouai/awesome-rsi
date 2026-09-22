[← 上一章：Meta-RSI 与 Search RSI](10-meta-rsi.md) · [返回目录](../README.md) · [下一章：系统与项目地图 →](12-systems.md)

---

# 11 · Benchmark 生态

> RSI Benchmark 的核心设计目标是区分「真自我改进」与「Benchmark Overfitting」。

---

## 1. 值得长期跟踪的 RSI / AI Research Benchmark

截至 2026 年 9 月：

| Benchmark | 测量对象 | 是否 Hidden Eval | 主要能力 |
|---|---|:---:|---|
| RSI-Exam | Research Agent | ✓ | 长程研究与泛化 |
| AI4AI-Bench | Training Algorithm | ✓ | Algorithm Discovery |
| RSIBench-Data | Data Strategy | ✓ / Controlled | Data Research |
| PostTrainBench | LLM Post-Training | ✓ | 自主后训练 |
| MLS-Bench | ML Method Invention | ✓ | 发明可泛化 ML 方法 |
| AutoLab | Auto Research & Eng | ✓ | 长程闭环优化 |
| RSI-Bench | Self-Modification | ✓ | 六轴自修改 |
| Scale RSI Bench | AI Research | ✓ | Frontier R&D |
| MLE-Bench | ML Engineering | 部分 | MLE |
| MLAgentBench | ML Experiments | 部分 | 自主实验 |
| NatureBench | Scientific ML | ✓ | SOTA Replication |
| SAEScientist-Bench | Interpretability Research | ✓ | 机制可解释性研究 |
| PaperBench | Research Replication | ✓ | Paper Reproduction |
| SWE-Bench Verified / Pro | Software | ✓ | Software Engineering |
| Terminal-Bench / LH-Terminal-Bench | Agent Harness | ✓ | Computer Use |
| OSWorld 2.0 | Computer Use | ✓ | 真实工作流 |
| TheAgentCompany | Workplace Agents | ✓ | 跨应用办公任务 |
| MCPMark | MCP Workflows | ✓ | 有状态工具工作流 |

> 部分 benchmark（如 RSI-Bench、PAST-Bench）社区实现星数很低，属**早期信号**，引用需谨慎。

### 能力阶梯

按能力分组：

- **Software Engineering** — [SWE-bench](https://github.com/SWE-bench/SWE-bench)（含 Verified / Lite / Multilingual / Multimodal 变体）、[SWE-Bench Pro](https://arxiv.org/abs/2509.16941)（1,865 个抗污染企业任务）、Polyglot（多语言 coding，DGM 使用）。
- **ML Engineering / AI4AI** — [MLE-bench](https://github.com/openai/mle-bench)（75 个 Kaggle 竞赛）、[RE-Bench](https://github.com/METR/RE-Bench)、[MLS-Bench](https://arxiv.org/abs/2605.08678)（140 任务 / 12 域）、[AutoLab](https://arxiv.org/abs/2606.05080)（36 个长程闭环任务）、[MLAgentBench](https://github.com/snap-stanford/MLAgentBench)。
- **Scientific Discovery** — [NatureBench](https://github.com/FrontisAI/NatureBench)（90 个 Nature 系论文任务）、[SAEScientist-Bench](https://arxiv.org/abs/2609.09113)。
- **Computer / Workplace Use** — [OSWorld 2.0](https://arxiv.org/abs/2606.29537)、[TheAgentCompany](https://arxiv.org/abs/2412.14161)、[MCPMark](https://arxiv.org/abs/2509.24002)、[Long-Horizon-Terminal-Bench](https://arxiv.org/abs/2607.08964)。
- **Reasoning** — DROP、MGSM、GPQA、MMLU、Game of 24；MATH / MATH500、GSM8K、ARC、HumanEval、MBPP。

---

## 2. 重点 Benchmark 详解

### RSI-Exam

公开仓库显示，完整 Benchmark 包含 **88 个任务**（Public 35 / Private 53）。每个任务给 Agent 一个可以运行但表现较弱的方法，最长可实验约 12 小时，最终提交 Artifact。随后：

> 在 Agent 从未访问过的密封数据上重新从头执行。如果改进无法迁移：**不得分。**

这使 RSI-Exam 测试的是 **Generalizable Research Improvement**，而不是 **Visible-set Optimization**。([GitHub][4])

### AI4AI-Bench

不再是 `Task`，而是 **Research Repository**。提供 **10 个冻结 Research Repository**，覆盖 10 类 Training Algorithm。Agent 可以修改 objective、loss、training rule、update mechanism、algorithm implementation。

- Agent 获得 **4 小时研究预算 + 单张 B300**。
- 提交之后，评估端从头运行最长 12 小时。([arXiv][5])

评分尺度与结果见 [09 · Algorithm RSI](09-algorithm-rsi.md)。

### RSIBench-Data

固定 Base Model、Post-training Stack、Evaluator、Training Backend、Compute Budget，仅让 Agent 负责 **Data Strategy**。详见 [07 · Data RSI](07-data-rsi.md)。([Evolvent AI][6])

### PostTrainBench

给自主 Agent 一个 base model、一张 H100、十小时，让它研究并执行能找到的最强 post-training 策略，直接度量「AI 能否自动化 LLM 后训练」。（[arXiv 2603.08640](https://arxiv.org/abs/2603.08640)，[aisa-group/PostTrainBench](https://github.com/aisa-group/PostTrainBench)）

### MLS-Bench / AutoLab

- **MLS-Bench**（[arXiv 2605.08678](https://arxiv.org/abs/2605.08678)）— 140 个任务、12 个 ML 研究域，测「AI 能否发明可泛化、可扩展的 ML 方法」。
- **AutoLab**（[arXiv 2606.05080](https://arxiv.org/abs/2606.05080)）— 36 个专家设计的真实长程闭环优化任务，评测前沿 Agent 的自动研究与工程能力。

### RSI-Bench

社区实现的多轴框架，评测六个维度：self-modification depth、improvement trajectories、operator discovery、meta-adaptation、safety、autonomous goal generation。（[sunghunkwag/rsi-bench](https://github.com/sunghunkwag/rsi-bench)）

> ⚠️ 社区早期项目，星数低，仅作方向参考。

---

## 3. 前沿实验室评测框架

除学术 benchmark 外，Frontier Lab 已把「AI R&D / 自我改进能力」纳入正式评测与治理框架：

| 机构 | 框架 / 指标 | 评测对象 |
|---|---|---|
| **Anthropic** | Responsible Scaling Policy · AI R&D-4 | 以「完全自动化一名入门级远程研究员」为阈值 |
| **Google DeepMind** | Frontier Safety Framework · ML R&D | 用 CCL / TCL 衡量显著加速或自动化 AI R&D 的能力 |
| **OpenAI** | Preparedness Framework · AI Self-Improvement | Internal Research Debugging、KernelGen 1P、NanoGPT、PostTrainBench Lite、MLE-Bench Revised 等聚合为 **RSI Index** |

> 这些框架把学术评测推向**治理级测量**——不仅问「分数多少」，还问「改进的是什么、是否可信」。见 [17 · 安全、对齐与治理](17-safety.md)。

---

## 4. 基准测试成绩

全部来自论文 / 官方 README 一手来源。

### Level 1 — Reasoning（Gödel Agent，GPT-3.5 主干）

| Benchmark | Meta Agent Search | Gödel Agent |
|---|---:|---:|
| DROP (F1) | 79.4 | **80.9** |
| MGSM (%) | 53.4 | **64.2** |
| MMLU (%) | 69.6 | **70.9** |
| GPQA (%) | 34.6 | **34.9** |

- Game of 24：4% → 78%；无限制版 DROP 90.5 / MGSM 90.6%。
- 价值在于「同底座下 self-improvement 的增益」，非绝对 SOTA。

### Level 2 — Software Engineering（DGM）

| Benchmark | Initial | DGM |
|---|---:|---:|
| SWE-bench | 20.0% | **50.0%** |
| Polyglot (full) | 14.2% | **30.7%** |

### Level 3 — ML Engineering（OpenRSI / Frontis-MA1 · MLE-Bench Lite 22 题 / 12h / 1×RTX 4090 / 12GB VRAM）

| 配置 | Medal Average |
|---|---:|
| Qwen3.6-35B-A3B + OpenMLE-Evo（base） | 39.39% |
| Frontis-MA1-35B + OpenMLE-Evo（post-train） | **60.61%** |
| Frontis-MA1-35B + OpenMLE-Evo-Max | **71.21%** |

- 对照：GPT-5.5 + Codex = 68.18%，GPT-5.6 Sol / Kimi K3 = 72.73%。即**超过 GPT-5.5+Codex，逼近 GPT-5.6 Sol**。
- 30B 版复现：34.85% → 53.03% → 66.67%（+18.18pp post-training 增益）。

### Level 4 — Scientific Discovery（NatureBench）

| 评测 | 成绩 |
|---|---|
| 全量 90 题：最强 coding-agent 配置 Surpass-SOTA（g>0.1） | **17.8%** |
| NatureBench Lite（10 题）：Frontis-MA1-35B + OpenMLE-Evo adapter | 30% Surpass / **70% Match-SOTA** |
| Model 迁移（framework 固定） | Match-SOTA 50% → **70%** |
| Framework 迁移（model 固定） | Match-SOTA 20% → **50%** |

- 核心结论：agent 成功主要靠**方法论翻译**，而非真正发明；失败主因 = 方法选错 + 算力不足。

### Benchmark 基线

- MLE-bench（OpenAI 2024）：o1-preview + AIDE 达 bronze 及以上 = **16.9%**。

> ⚠️ **待独立复核**：Agent0 的「math +18%、general reasoning +24%」、SEAL 的「2×A100/H100 可跑」——引用前建议核对原始仓库。

---

## 5. Benchmark 追踪优先级

**一级（RSI 核心）**

- **RSI-Exam** — AI Research Generalization。
- **AI4AI-Bench** — Training Algorithm Discovery。
- **RSIBench-Data** — Data Research。

**二级（能力底座）**

- **NatureBench** — 科学机器学习复现。
- **MLE-Bench** — ML Engineering。
- **PaperBench** — Paper Reproduction。
- **Terminal-Bench** — Harness 与 Computer Use。
- **SWE-Bench Verified** — Software Agent。

---

[← 上一章：Meta-RSI 与 Search RSI](10-meta-rsi.md) · [返回目录](../README.md) · [下一章：系统与项目地图 →](12-systems.md)

[4]: https://github.com/aiming-lab/RSI-Exam
[5]: https://arxiv.org/abs/2608.20318
[6]: https://evolvent.co/en/research
