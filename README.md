# AI Journey: Backend Engineer → Applied Research AI Engineer

A 12-month, build-first path from backend engineering to applied research AI engineering:
training, fine-tuning, evaluating and serving models, plus production LLM systems (agents, RAG, MCP).

**Cadence:** ~12–15 hrs/week · **Tracker:** [PROGRESS.md](PROGRESS.md) · **Daily log:** [log.md](log.md)

## Rules

1. **Build before reading the answer.** Implement every idea yourself before looking at a reference.
2. **No claim without a number.** Loss curve, eval score, latency, or cost.
3. **Ship in public.** Every module ends with a repo, write-up, or PR.

## Roadmap

| # | Module | Weeks | Outcome |
|---|---|---|---|
| 0 | [Setup & habits](00-setup/) | 1 | Repo, log, GPU access |
| 1 | [Math & neural-net foundations](01-foundations/) | 2–6 | Backprop from first principles |
| 2 | [Transformers & LLMs from scratch](02-transformers/) | 7–14 | Own GPT-2 (124M) trained |
| 3 | [Classic ML & evaluation](03-classic-ml-eval/) | parallel, 2–20 | Evaluation and metrics depth |
| 4 | [Applied LLM engineering: agents, RAG, MCP](04-applied-llm-agents/) | 15–22 | Production agent with evals |
| 5 | [Fine-tuning & post-training](05-finetuning/) | 23–30 | SFT + DPO model with measured gains |
| 6 | [ML systems: GPUs, distributed, inference](06-ml-systems/) | 31–40 | Fast, cheap serving; a Triton kernel |
| 7 | [Research & visibility](07-research/) | 41–48 | Paper reproduction, OSS PRs |
| 8 | [Interview prep & job hunt](08-interview-prep/) | 44–52 | Ready for applied AI / RE loops |

## Module details

### 0. Setup (week 1)
- Python 3.11+, PyTorch, Jupyter, Colab; GPU rental account (RunPod / Lambda / Vast).
- Daily 3-line entry in `log.md`: learned / confused / next.

### 1. Math & neural-net foundations (weeks 2–6)
- **Learn:** 3Blue1Brown *Essence of Linear Algebra* + *Neural Networks* (ch. 1–4);
  Karpathy *Zero to Hero*: **micrograd**, **makemore 1–3**; reference *Mathematics for Machine Learning* (Deisenroth) ch. 2, 5, 6.
- **Build:** micrograd from scratch (grad-checked vs PyTorch and finite differences); char-level MLP language model.
- **Checkpoint:** derive softmax + cross-entropy gradients on paper; explain BatchNorm and learning-rate failure modes.

### 2. Transformers & LLMs from scratch (weeks 7–14)
- **Learn:** Karpathy makemore 4–5, *Let's build GPT*, *GPT tokenizer*, *Reproduce GPT-2 (124M)*;
  Stanford **CS336** (assignment 1); Raschka *Build a Large Language Model (From Scratch)*;
  papers: *Attention Is All You Need*, GPT-2, Chinchilla.
- **Build:** BPE tokenizer and GPT-2-small trained on a rented GPU, with loss curves and LR/warmup ablations.
- **Checkpoint:** implement multi-head attention from memory; explain the KV cache; diagnose a loss spike.

### 3. Classic ML & evaluation (parallel, ~4 hrs/week, via Scaler, selective)
- **Keep:** statistics, hypothesis and A/B testing, metrics, cross-validation, leakage, XGBoost/LightGBM, feature engineering.
- **Skim:** SVM derivations, classic NLP pipelines, BI modules. Supplement: Géron *Hands-On ML* ch. 2–7.
- **Build:** a tabular model on real data with a baseline, proper splits, and error analysis.
- **Checkpoint:** pick and justify a business metric; design an A/B test with a power calculation.

### 4. Applied LLM engineering: agents, RAG, MCP (weeks 15–22)
- **Learn:** Chip Huyen *AI Engineering*; Anthropic *Building effective agents*; Model Context Protocol docs;
  LangChain Academy *Intro to LangGraph*; Hamel Husain's posts on LLM evals.
- **Build:** (1) raw tool-calling agent → (2) the same agent in LangGraph with your own MCP server →
  (3) RAG with hybrid search + re-ranker (pgvector/Qdrant) → (4) eval harness: golden set, judge checked against human labels,
  CI regression runs, Langfuse tracing.
- **Capstone:** incident-investigation agent (logs + repos + k8s audit tools), evaluated on real past incidents.
- **Checkpoint:** prove with numbers that an agent change helped, and that it isn't noise.

### 5. Fine-tuning & post-training (weeks 23–30)
- **Learn:** Hugging Face *LLM Course* and *smol-course*; TRL and PEFT docs; papers: LoRA, QLoRA, InstructGPT, DPO,
  one RL-for-reasoning (GRPO-style) paper; CS336 alignment lectures.
- **Build:** SFT → DPO on an open 1–8B model; compare base / SFT / DPO and a hosted API on quality and cost.
- **Checkpoint:** decide fine-tune vs prompt vs RAG; debug overfitting or forgetting.

### 6. ML systems: GPUs, distributed, inference (weeks 31–40)
- **Learn:** GPU MODE lectures; Triton tutorials; Hugging Face *Ultra-Scale Playbook*; *How to Scale Your Model*;
  papers: FlashAttention, PagedAttention (vLLM), speculative decoding.
- **Build:** a Triton kernel with a measured speedup; a multi-GPU run with scaling-efficiency numbers;
  the Module 5 model served on vLLM with quantization and latency/throughput benchmarks.
- **Checkpoint:** estimate memory and throughput for serving a 7B model on paper, then verify by measuring.

### 7. Research & visibility (weeks 41–48)
- Reproduce one recent paper (including what didn't replicate) and publish it.
- 2+ non-trivial PRs to vLLM / SGLang / TRL / PyTorch / llama.cpp.
- One technical write-up per month.

### 8. Interview prep & job hunt (weeks 44–52)
- **Learn:** Chip Huyen *Introduction to ML Interviews* and *Designing ML Systems*; NeetCode 150.
- **Practise:** ML depth (attention, loss spikes, fine-tune + eval plans); ML system design (LLM serving, RAG at scale, recsys);
  behavioural stories (problem → evidence → fix → impact).
- **Apply:** from month 8 to applied AI / ML platform roles; from month 11 to research-engineer roles.
