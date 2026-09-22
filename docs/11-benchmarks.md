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
| Scale RSI Bench | AI Research | ✓ | Frontier R&D |
| MLE-Bench | ML Engineering | 部分 | MLE |
| NatureBench | Scientific ML | ✓ | SOTA Replication |
| PaperBench | Research Replication | ✓ | Paper Reproduction |
| SWE-Bench Verified | Software | ✓ | Software Engineering |
| Terminal-Bench | Agent Harness | ✓ | Computer Use |

### 能力阶梯

按能力分组：

- **Software Engineering** — [SWE-bench](https://github.com/SWE-bench/SWE-bench)（含 Verified / Lite / Multilingual / Multimodal 变体）、Polyglot（多语言 coding，DGM 使用）。
- **ML Engineering / AI4AI** — [MLE-bench](https://github.com/openai/mle-bench)（75 个 Kaggle 竞赛）、[RE-Bench](https://github.com/METR/RE-Bench)（AI R&D 能力）。
- **Scientific Discovery** — [NatureBench](https://github.com/FrontisAI/NatureBench)（90 个 Nature 系论文任务）。
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

---

## 3. 基准测试成绩

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

## 4. Benchmark 追踪优先级

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
