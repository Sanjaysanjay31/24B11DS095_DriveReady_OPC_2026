# Day 2 — Prompts, Memory, and Python Fundamentals for Agents

**Workshop:** One Person Company — 12-Day Agentic AI Workshop (Aditya University)  
**Project:** AI Startup Marketing Agent  
**Primary Provider:** OpenRouter — NVIDIA Nemotron 3.5 Super VL (Free)  
**Fallback Provider:** Groq — GPT-OSS 120B  
**Notebook:** [`Startup_Marketing_Agent.ipynb`](file:///c:/Skills/Agentic_AI_Workshop/Day_2/Startup_Marketing_Agent.ipynb)  

---

## 📌 Overview

Day 2 focuses on controlling model behavior, implementing few-shot classification, extracting structured JSON briefs, maintaining rolling conversational memory, and writing the Python constructs (type hints, decorators, try/except) needed for autonomous agents.

Supports execution both in **Google Colab** (via Colab Secrets) and **locally** (via `.env`).

---

## 🏗️ Architecture

```
User Message
     │
     ▼
[ Environment Loader (.env / Colab Secrets) ]
     │
     ▼
[ ask_llm() Failover ]
     ├── 1. Primary: OpenRouter (NVIDIA Nemotron 3.5 Super VL)
     └── 2. Fallback: Groq (GPT-OSS 120B)
     │
     ▼
[ Agent Capabilities ]
     ├── Few-Shot Classifier (Categorizes founder intent)
     ├── JSON Extractor (Presents clean structured startup briefs)
     ├── Cost Calculator Tool with @log_call Decorator
     └── Sliding-Window Memory (Retains last 5 turns with rollback safety)
```

---

## 📁 Notebook Breakdown (Compact 7 Cells)

| Cell | Focus | What It Does |
|:---:|:---|:---|
| **1** | Dependencies | Installs `openai` and `python-dotenv`. |
| **2** | Client Setup | Initializes dual clients for OpenRouter and Groq with `.env` / Colab Secrets. |
| **3** | Core Agent & Prompt | Sets `MARKETING_SERVICES` catalogue, system prompt, and resilient `ask_llm()` failover. |
| **4** | Classification & JSON | Few-shot request classifier and structured JSON brief extractor. |
| **5** | Python Tool & Decorator | `calculate_cost()` tool with type hints and `@log_call` execution decorator. |
| **6** | Memory & Error Handling | Sliding-window memory buffer (`MAX_TURNS = 5`) and try/except error recovery. |
| **7** | Verification | Automated multi-turn test checking context retention and pricing calculation. |

---

## 🚀 How to Run

### In Google Colab
1. Click the **Open In Colab** badge in [`Startup_Marketing_Agent.ipynb`](file:///c:/Skills/Agentic_AI_Workshop/Day_2/Startup_Marketing_Agent.ipynb).
2. Add `OPENROUTER_API_KEY` and `GROQ_API_KEY` in **Colab Secrets (key icon)**.
3. Click `Runtime -> Run all`.

### Locally (VS Code / Jupyter)
1. Add keys in `.env`:
   ```env
   OPENROUTER_API_KEY=your_key
   GROQ_API_KEY=your_key
   ```
2. Run:
   ```bash
   jupyter notebook Day_2/Startup_Marketing_Agent.ipynb
   ```
