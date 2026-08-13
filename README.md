# Seth Zapata

**Software engineer building production AI systems — retrieval, LLM evaluation, and agentic workflows.**

Three years building backend services at AWS scale, currently finishing an MS in Artificial Intelligence at UT Austin. Most of what I build sits at the boundary between machine learning and production engineering: the pipelines, evaluation harnesses, and observability that determine whether a model still works after it ships.

I try to measure things rather than assert them — and to publish the results that didn't work alongside the ones that did.

---

## Projects

| Project | What it is | What it demonstrates |
|---|---|---|
| **[glassbox](https://github.com/seth-zapata/glassbox)** | Glass-box RAG agent on Cloudflare Workers, [live here](https://glassbox.glassbox.workers.dev) | Runs entirely on Cloudflare — Workers AI for generation, embeddings and judging, Durable Objects for session state, Vectorize for retrieval, D1 for eval history. Every answer ships with its evidence: retrieved chunks and scores stream *before* the answer, then a second model's verdict on whether the answer is supported, then per-stage latency. **28 eval cases are committed and replay with `npm run eval:replay` — no credentials, no model calls** — so every number below is reproducible: 100% refusal out-of-corpus, 1.000 faithfulness and 0.861 MRR in-corpus, τ = 0.62. The most useful finding was negative: similarity scores alone can't separate answerable from unanswerable questions, because a threshold would admit six of eight out-of-corpus cases. **It also speaks [MCP](https://modelcontextprotocol.io) at `/mcp`** — five tools over the corpus, the retrieval scores and the eval history, with two scopes, scope-filtered `tools/list`, and a rate limit implemented as a count over [publicly served call records](https://glassbox.glassbox.workers.dev/api/mcp/history) so the limit is auditable rather than trusted. |
| **[docsense](https://github.com/seth-zapata/docsense)** | Production RAG system with QLoRA fine-tuning, built from scratch over the Hugging Face Transformers docs | Hybrid BM25 + dense retrieval with reciprocal rank fusion, cross-encoder re-ranking, and a measured performance report card — MRR 0.685, claim-level faithfulness 0.894, 100% refusal on off-corpus queries. Four generation invariants pinned as CI contracts. Known gaps documented, not hidden. |
| **[options-radar](https://github.com/seth-zapata/options-radar)** | Display-only options analysis platform over a curated tech/AI watchlist | An 11-stage agentic workflow with structured routing, error handling, and state maintained across long processing chains; real-time streaming, multi-source integration under auth and rate limits, and an evaluation harness measuring end-to-end task completion. |
| **[crypto-trading-research](https://github.com/seth-zapata/crypto-trading-research)** | Risk-first algorithmic trading research system | Graph neural networks for multi-asset regime detection with crash-aware asymmetric loss (80% crash detection), validated by walk-forward testing and 1,000-simulation Monte Carlo — plus a documented pivot away from on-chain alpha signals after the analysis showed they weren't tradeable. |
| **[regime-aware-rl-trading](https://github.com/seth-zapata/regime-aware-rl-trading)** | Reinforcement learning over alternative data and multi-modal signals | Regime-conditioned policy learning and embedding-based feature pipelines applied to a noisy, non-stationary domain. |
| **[lstm-stock-prediction](https://github.com/seth-zapata/lstm-stock-prediction)** | Sequence models for price direction research | LSTM / GRU / Transformer architectures across 26 technical indicators, walk-forward backtesting with strict temporal ordering to prevent look-ahead bias, 96 unit tests — and documented negative results rather than a cherry-picked curve. |

---

## Currently

- **MS, Artificial Intelligence** — The University of Texas at Austin
- **BS, Computer Science** (Data Science concentration) — UT San Antonio, Magna Cum Laude
- Most interested in retrieval quality, LLM evaluation methodology, and agent reliability in production

## Tech

**Languages** — Python · TypeScript · Java · SQL

**ML / AI** — PyTorch · Hugging Face (Transformers, PEFT, TRL, Accelerate) · sentence-transformers · FAISS · BM25 · cross-encoder re-ranking · LLM-as-a-judge evaluation · QLoRA · **Model Context Protocol (MCP)**

**Backend** — FastAPI · GraphQL · REST · WebSockets · MCP servers (Streamable HTTP) · microservices · Docker · Kubernetes

**Data** — PostgreSQL · TimescaleDB · Redis · Vectorize · D1 · data pipelines · schema validation · time-series storage

**Cloud & Ops** — AWS (Bedrock, Lambda, ECS, OpenSearch, DynamoDB, CloudWatch) · Cloudflare (Workers, Workers AI, Durable Objects) · CI/CD with regression gates · structlog · Weights & Biases

---

## Reach me

[LinkedIn](https://linkedin.com/in/sethzapata) · San Antonio, TX

Best reached through LinkedIn.
