# Day 1 — How LLMs Work and Your First API Call

---

## 📌 Overview

Day 1 establishes the foundational layer of building autonomous agentic software: understanding how Large Language Models (LLMs) operate under the hood, how tokens and inference engines work, and how to connect to LLM APIs programmatically using **LangChain**.

Rather than relying on a basic single-provider call, this implementation introduces an **enterprise-grade multi-provider fallback architecture** that ensures high availability and zero downtime.

---

## 🏗️ Architecture: Resilient Multi-Provider Fallback

A common point of failure in production agentic workflows is provider throttling, network timeouts, or sudden API downtime. This implementation implements a primary-to-fallback failover mechanism:

```
                      ┌──────────────────────┐
                      │    Incoming Query    │
                      └──────────┬───────────┘
                                 │
                                 ▼
                      ┌──────────────────────┐
                      │    ask(question)     │
                      └──────────┬───────────┘
                                 │
                                 ▼
                     [ Attempt Primary LLM ]
                   OpenRouter: NVIDIA Nemotron
                                 │
                    ┌────────────┴────────────┐
                    │                         │
            (Success: 200 OK)         (Error / Timeout / 429)
                    │                         │
                    ▼                         ▼
         ┌─────────────────────┐   ┌─────────────────────┐
         │ Return Model Output │   │ Trigger Failover    │
         └─────────────────────┘   └──────────┬──────────┘
                                              │
                                              ▼
                                   [ Fallback LLM on Groq ]
                                     OpenAI GPT-OSS 120B
                                              │
                                              ▼
                                   ┌─────────────────────┐
                                   │ Return Model Output │
                                   └─────────────────────┘
```

---

## 🤖 Models & Capabilities

### 1. Primary Model: NVIDIA Nemotron 3.5 Super VL
- **Provider:** OpenRouter (`nvidia/nemotron-3.5-super-vl:free`)
- **Architecture:** Hybrid Mamba-Transformer Mixture-of-Experts (MoE)
- **Parameters:** 12B active parameters out of 120B total
- **Context Window:** 1,000,000 tokens (1.0M)
- **Modalities:** Multimodal (Text, Images, Documents, GUI screenshots, and Video input $\rightarrow$ Text output)
- **Specialty:** Built specifically for long-running agents combining visual understanding with reasoning and tool use.
- **Reasoning:** Enabled by default (hybrid reasoning with token budget control).
- **Performance:** ~87 tokens/sec throughput, ~1.49s average latency, 99.90% uptime.
- **Cost:** Free tier on OpenRouter.

### 2. Fallback Model: OpenAI GPT-OSS 120B
- **Provider:** Groq (`openai/gpt-oss-120b`)
- **Architecture:** 120B dense open-weights model hosted on Groq's custom LPU (Language Processing Unit) inference hardware.
- **Performance:** Extremely low latency token generation.
- **Groq Tier Limits:**
  - Requests: 30 requests/min, 1,000 requests/day
  - Tokens: 8,000 tokens/min, 200,000 tokens/day
- **Role:** Instantaneous fallback when the primary provider encounters network issues or rate limits.

---

## 🛡️ Security Layer: Llama Prompt Guard

To protect the marketing agent from malicious prompt injection and jailbreaks, the notebook integrates **Llama Prompt Guard**:

- **Model:** `meta-llama/llama-prompt-guard-2-22m`
- **Function:** Classifies inputs and returns an injection probability score.
- **Threshold Rule:** Inputs with a score $> 0.5$ are flagged as malicious and rejected before reaching the main generation models.

```python
score = float(guard_response.content.strip())
if score > 0.5:
    print("[ALERT] Injection / Jailbreak attempt detected. Input rejected.")
```

---
