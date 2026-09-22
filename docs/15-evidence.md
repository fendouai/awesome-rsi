[← 上一章：瓶颈与路线图](14-outlook.md) · [返回目录](../README.md)

---

# 15 · 证据等级与核实

> RSI 领域混杂着 Marketing Claim、Demo、Benchmark、Internal Eval、Research Paper。因此跟踪 RSI 必须建立统一的证据等级。

---

## 1. Evidence Level

| 等级 | 名称 | 含义 |
|---|---|---|
| **E0** | Concept | 只有理论或观点 |
| **E1** | Demo | 有 Demo，但无严格评价 |
| **E2** | Public Benchmark | 存在可测试 Benchmark |
| **E3** | Hidden Evaluation | Agent 无法直接看到最终 evaluator |
| **E4** | Reproducible | Code / Environment / Evaluation 全部公开 |
| **E5** | Independent Replication | 其他团队独立复现 |

因此：

```text
Project Claim ≠ Benchmark Result ≠ Independent Verification
```

在高速发展的 RSI 领域，这一区分尤其重要。

---

## 2. 数据核实说明

1. **DGM 官方代码是 `jennyzzt/dgm`**（arXiv 摘要原文），不是 `kew-lab/darwin-godel-machine`（疑似 fork）。
2. **NatureBench Surpass-SOTA = 17.8%**（arXiv v2 已更新 GLM-5.2 / MiniMax-M3），不是 15.6%。
3. **Gödel Agent 主干是 GPT-3.5**。
4. **OpenRSI 论文 = arXiv 2607.28568（2026-07）**，Frontis-MA1-35B 基于 Qwen3.6-35B-A3B（30B 版基于 Qwen3-30B-A3B-Thinking-2507）。
5. STOP / ADAS / SEAL / Agent0 / RE-Bench 的仓库创建日期均已通过 GitHub 元数据核实。

---

## 3. 待独立复核项

- Agent0 的「math +18%、general reasoning +24%」。
- SEAL 的「2×A100/H100 可跑」。

> 引用前建议核对原始仓库。

---

## 4. 引用来源

| # | 来源 | 链接 |
|---|---|---|
| [1] | Anthropic — Measuring the pace of AI development | https://www.anthropic.com/institute/measuring-pace-of-ai-development |
| [2] | OpenAI — RSI 岗位 | https://openai.com/careers/research-engineer-research-scientist-ai-systems-engineer-rsi-san-francisco/ |
| [3] | RSI Survey（arXiv 2607.07663） | https://arxiv.org/abs/2607.07663 |
| [4] | RSI-Exam | https://github.com/aiming-lab/RSI-Exam |
| [5] | AI4AI-Bench（arXiv 2608.20318） | https://arxiv.org/abs/2608.20318 |
| [6] | Evolvent AI | https://evolvent.co/en/research |
| [7] | Recuris | https://github.com/Gen-Verse/Recuris |
| [8] | OpenRSI | https://github.com/FrontisAI/OpenRSI |
| [9] | ScienceBuddy（arXiv 2609.17523） | https://arxiv.org/abs/2609.17523 |
| [10] | MetaRSI-v1 | https://cosmosmind.ai/research/metarsi-v1 |
| [11] | Dream-RSI | https://www.dream-rsi.com/ |
| [12] | The Last AI Built by Humans（arXiv 2609.11873） | https://arxiv.org/abs/2609.11873 |
| [13] | OpenAI — Research acceleration | https://openai.com/index/research-acceleration-view-inside-openai/ |
| [14] | TechCrunch — Recursive Superintelligence | https://techcrunch.com/2026/07/28/recursive-superintelligence-signs-400-compute-deal-with-amazon/ |
| [15] | Nasdaq — Deep Cogito | https://www.nasdaq.com/press-release/deep-cogito-raises-43m-series-advance-post-training-engine-frontier-intelligence-2026 |
| [16] | Ineffable Intelligence | https://www.ineffable.ai/ |

---

[← 上一章：瓶颈与路线图](14-outlook.md) · [返回目录](../README.md)
