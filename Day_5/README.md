# Day 5 — Memory and RAG: An Agent That Remembers and Looks Things Up

**Workshop:** One Person Company — 12-Day Agentic AI Workshop (Aditya University)  
**Project:** AI Startup Marketing Agent  
**Primary Provider:** OpenRouter — NVIDIA Nemotron 3.5 Super VL (Free)  
**Fallback Provider:** Groq — GPT-OSS 120B  
**Database:** [Google Sheets Campaign Orders](https://docs.google.com/spreadsheets/d/1WryffEEH-N9TpWcwg8pvdaNU0XGzQWqBRS2Lnt0Ro90/edit?usp=sharing)  
**Notebook:** [`Startup_Marketing_Agent.ipynb`](file:///c:/Skills/Agentic_AI_Workshop/Day_5/Startup_Marketing_Agent.ipynb)  

---

## 📌 Overview

On Day 4, our agent learned to call Python tools and log campaign bookings to Google Sheets. On Day 5, we achieve the **Single-Agent Sign-Off** milestone by equipping the agent with:

1. **Multi-Session Conversational Memory:** Remembering context within individual founder sessions while maintaining strict isolation between different founders using LangGraph `InMemorySaver` and `thread_id`.
2. **Retrieval-Augmented Generation (RAG):** Indexing agency policies, video specifications, and legal rules into a vector database (**ChromaDB**) so the agent answers questions with factual grounding rather than hallucinations.
3. **Guardrails & Out-of-Scope Protection:** A strict refusal rule directing the agent to say *"I'll check with the agency founders"* whenever a question falls outside the indexed knowledge base.

---

## 🧠 The Three Kinds of Agent Memory

```
┌────────────────────────────────────────────────────────────────────────┐
│                        AI AGENT MEMORY SPECTRUM                        │
├───────────────────────┬───────────────────────┬────────────────────────┤
│  1. Conversation      │  2. Customer Memory   │  3. Business Knowledge │
│     (Working Memory)  │     (Long-Term Data)  │     (Semantic Library) │
├───────────────────────┼───────────────────────┼────────────────────────┤
│ Checkpointer & Thread │ Google Sheets / SQL   │ Vector Database        │
│ InMemorySaver()       │ gspread Orders sheet  │ ChromaDB / FAISS       │
│ "What did Sanjay ask  │ Confirmed bookings &  │ 14+ Agency policies,   │
│  2 turns ago?"        │ founder order records │ video specs & legal    │
└───────────────────────┴───────────────────────┴────────────────────────┘
```

---

## 🛠️ The Four Autonomous Agent Tools

```
Founder Chat Message
        │
        ▼
[ Agent Decision Loop (LangGraph + Memory) ]
        │
        ├── get_service_price()      ➔ Exact price calculation from SERVICES catalogue
        ├── check_operating_hours()  ➔ Pipeline rendering & support operating schedule
        ├── log_campaign_order()     ➔ Pydantic validation & Google Sheets persistence
        └── search_knowledge()       ➔ RAG semantic retrieval over ChromaDB policy facts
```

1. **`get_service_price(service: str, qty: int = 1)`**:
   Looks up prices for short-form video services (hooks, scripts, storyboards, voiceovers, assembly).
2. **`check_operating_hours(day: str)`**:
   Returns the agency's working hours and pipeline rendering schedule for any given day.
3. **`log_campaign_order(client_name, startup_name, service, platform, target_date)`**:
   Validates orders with Pydantic `CampaignOrder(BaseModel)` and records confirmed bookings to Google Sheets.
4. **`search_knowledge(question: str)`**:
   Semantic RAG search over ChromaDB for policies (free revisions, turnaround times, 9:16 aspect ratio, commercial audio monetization, NDA confidentiality, cancellation fee, voice cloning, thumbnails).

---

## 📋 Notebook Architecture (6 Core Cells)

| Cell | Topic | Description |
|:---:|:---|:---|
| **1** | Environment & Setup | Dual LLM routing (OpenRouter + Groq) and live Google Sheets connection. |
| **2** | Knowledge Ingestion & Chunking | 14 agency facts, `split_text()` chunking utility, and ChromaDB vector indexing. |
| **3** | Catalogue & Operational Tools | Defines `SERVICES`, `HOURS`, `CampaignOrder` schema, and price/hours/sheet tools. |
| **4** | RAG Tool (`search_knowledge`) | `@tool` querying ChromaDB vector store with rich topic docstring. |
| **5** | Agent with Memory | `create_agent()` with `InMemorySaver()`, multi-thread testing, memory + RAG test, and break-it test. |
| **6** | Benchmark Evaluation Suite | Appends test cases to `tests.csv`, executes `run_tests()`, and verifies 100% pass rate sign-off. |

---

## 🧪 Evaluation Suite & Single-Agent Sign-Off

The automated evaluation suite (`tests.csv`) verifies memory, tool execution, and RAG grounding:

| Question | Expected Keyword | Purpose | Status |
|:---|:---|:---|:---:|
| Do you offer free revisions? | `2` | RAG Policy Retrieval | **PASS** |
| What aspect ratio do you deliver? | `9:16` | Technical Video Specs | **PASS** |
| Is the background music royalty-free? | `royalty-free` | Audio Monetization Rights | **PASS** |
| How much is short script writing? | `700` | Catalogue Price Lookup Tool | **PASS** |
| Can you sign an NDA? | `NDA` | Legal Confidentiality | **PASS** |
| Do you build mobile apps? | `check with the agency founders` | Out-of-Scope Guardrail Check | **PASS** |

**Benchmark Score:** 6/6 Passed (**100.0% Pass Rate** &mdash; target: &ge; 80%).

---

## 🚀 How to Run

### In Google Colab
1. Click the **Open In Colab** badge in [`Startup_Marketing_Agent.ipynb`](file:///c:/Skills/Agentic_AI_Workshop/Day_5/Startup_Marketing_Agent.ipynb).
2. Add `OPENROUTER_API_KEY` and `GROQ_API_KEY` to **Colab Secrets (key icon)**.
3. Click `Runtime -> Run all` and approve the Google account authentication prompt.

### Locally
```bash
jupyter notebook Day_5/Startup_Marketing_Agent.ipynb
```
