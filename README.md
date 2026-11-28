# Autonomous AI Startup Marketing Agent
 

## 💡 Executive Summary

Most early-stage technical founders build remarkable products but struggle with marketing, distribution, and social media presence. Creating consistent short-form videos (YouTube Shorts, Instagram Reels, TikTok) is time-consuming, expensive, and intimidating for founders who do not want to appear on camera.

The **AI Startup Marketing Agent** is an autonomous, multi-agent engine designed to act as a complete growth team for a **"One Person Company"**. Given a startup's URL, pitch deck, or problem description, the system researches market trends, engineers viral hooks, writes high-retention 9:16 scripts, generates visual scene storyboards, orchestrates founder approvals, renders final video assets with voiceovers and captions, and optimizes performance based on viewer retention analytics.

---

## 🔄 End-to-End Autonomous Workflow (9 Phases)

```
┌────────────────────────────────────────────────────────────────────────┐
│                   PHASE 1: STARTUP PROFILER & AUDIENCE                 │
│ Ingests startup URL / pitch to extract USP, ICP, pricing & pain points │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│                 PHASE 2: TREND & COMPETITOR RESEARCH                   │
│ Real-time web search for relevant news, data points & audience habits  │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│                 PHASE 3: VIRAL HOOK & ANGLE GENERATION                 │
│ Generates problem-first, curiosity-driven hooks tailored to founders   │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│                 PHASE 4: 9:16 SHORT-FORM SCRIPTWRITING                 │
│ Paces 30-45s timed scripts with scene narration and visual cues        │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│              PHASE 5: STORYBOARD & VISUAL FRAME DIRECTOR               │
│ Generates consistent character & stylistic prompts for each scene cut  │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
                                    ▼
══════════════════════════════════════════════════════════════════════════
               🛑 PHASE 6: FOUNDER APPROVAL GATE (HITL)
 Founder reviews, edits, regenerates, or approves scripts and visuals
══════════════════════════════════════════════════════════════════════════
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│                  PHASE 7: VIDEO PRODUCTION ASSEMBLY                    │
│ TTS voiceover synthesis + Whisper karaoke subtitles + 9:16 composition │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│                PHASE 8: SOCIAL PACKAGING & PUBLISHING                  │
│ Exports ready-to-upload YouTube Short & Reel with captions & hashtags  │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│               PHASE 9: PERFORMANCE ANALYTICS & RETENTION               │
│ Analyzes 3s retention & watch-time to optimize subsequent video cycles │
└────────────────────────────────────────────────────────────────────────┘
```

---

## 📅 Completed Workshop Milestones (Days 1–5)

| Day | Topic | Project Milestone & Implementation | Mentor Lecture Notes |
|:---:|:---|:---|:---|
| **Day 1** | **How LLMs work and your first API call** | [`LLM_Setup.ipynb`](Day_1/LLM_Setup.ipynb)<br>Resilient dual-provider LangChain fallback (OpenRouter + Groq) and Llama Prompt Guard safety layer. | [`Day 1 (Mentor_notes).html`](Day_1/Day%201%20%C2%B7%20How%20LLMs%20work%20and%20your%20first%20API%20call(Mentor_notes).html) |
| **Day 2** | **Prompts that work, JSON and Python basics** | [`Startup_Marketing_Agent.ipynb`](Day_2/Startup_Marketing_Agent.ipynb)<br>Structured system prompts, few-shot video classification, JSON brief parsing, and sliding-window memory. | [`Day 2 (Mentor_notes).html`](Day_2/Day%202%20%C2%B7%20Prompts%2C%20memory%20and%20the%20Python%20agents%20need(Mentor_notes).html) |
| **Day 3** | **Your first AI agent** | [`Startup_Marketing_Agent.ipynb`](Day_3/Startup_Marketing_Agent.ipynb)<br>First LangChain LCEL agent with conversational memory, evaluation suite (`tests.csv`), and task routing. | [`Day 3 (Mentor_notes).html`](Day_3/Day%203%20%C2%B7%20Your%20first%20agent%2C%20what%20an%20agent%20is%2C%20and%20LangChain(Mentor_notes).html) |
| **Day 4** | **Tools, structured output and Google Sheets** | [`Startup_Marketing_Agent.ipynb`](Day_4/Startup_Marketing_Agent.ipynb)<br>Autonomous agent with Pydantic schemas, pricing/hours tools, and live Google Sheets database logging (`gspread`). | [`Day 4 (Mentor_notes).html`](Day_4/Day%204%20%C2%B7%20Tools%2C%20structured%20output%20and%20Google%20Sheets(Mentor_notes).html) |
| **Day 5** | **Memory and RAG: an agent that remembers and looks things up** | [`Startup_Marketing_Agent.ipynb`](Day_5/Startup_Marketing_Agent.ipynb)<br>Single-agent sign-off with LangGraph checkpointer memory across sessions and ChromaDB RAG vector retrieval. | [`Day 5 (Mentor_notes).html`](Day_5/Day%205%20%C2%B7%20Memory%20and%20RAG%2C%20an%20agent%20that%20remembers%20and%20looks%20things%20up(Mentor_notes).html)<br>[`RAG Working (Mentor_notes).html`](Day_5/RAG%20Working(Mentor_notes).html) |

---

## 📚 Mentor Lecture Notes & Reference Material

Each day's folder preserves the instructor's original session curriculum and lecture notes in interactive HTML format:
- **Day 1 Notes:** [`Day 1 · How LLMs work and your first API call(Mentor_notes).html`](file:///c:/Skills/Agentic_AI_Workshop/Day_1/Day%201%20%C2%B7%20How%20LLMs%20work%20and%20your%20first%20API%20call(Mentor_notes).html) — Fundamentals of tokens, temperature, system prompts, API wrappers, and pricing.
- **Day 2 Notes:** [`Day 2 · Prompts, memory and the Python agents need(Mentor_notes).html`](file:///c:/Skills/Agentic_AI_Workshop/Day_2/Day%202%20%C2%B7%20Prompts%2C%20memory%20and%20the%20Python%20agents%20need(Mentor_notes).html) — Structured prompting, few-shot reasoning, JSON schema extraction, and conversation history.
- **Day 3 Notes:** [`Day 3 · Your first agent, what an agent is, and LangChain(Mentor_notes).html`](file:///c:/Skills/Agentic_AI_Workshop/Day_3/Day%203%20%C2%B7%20Your%20first%20agent%2C%20what%20an%20agent%20is%2C%20and%20LangChain(Mentor_notes).html) — Agent concept, Code vs LLM vs Agent taxonomy, LangChain LCEL chains, and test evaluation.
- **Day 4 Notes:** [`Day 4 · Tools, structured output and Google Sheets(Mentor_notes).html`](file:///c:/Skills/Agentic_AI_Workshop/Day_4/Day%204%20%C2%B7%20Tools%2C%20structured%20output%20and%20Google%20Sheets(Mentor_notes).html) — Autonomous agent tools (`@tool`), Pydantic validation, and live database persistence with Google Sheets.
- **Day 5 Notes:** [`Day 5 · Memory and RAG, an agent that remembers and looks things up(Mentor_notes).html`](file:///c:/Skills/Agentic_AI_Workshop/Day_5/Day%205%20%C2%B7%20Memory%20and%20RAG%2C%20an%20agent%20that%20remembers%20and%20looks%20things%20up(Mentor_notes).html) & [`RAG Working(Mentor_notes).html`](file:///c:/Skills/Agentic_AI_Workshop/Day_5/RAG%20Working(Mentor_notes).html) — Multi-session conversational memory (`InMemorySaver`), vector databases (ChromaDB / FAISS), chunking, and RAG semantic search.

---

## 🛠️ Technology Stack

- **Large Language Models:**
  - `nvidia/nemotron-3.5-super-vl:free`: Hybrid Mamba-Transformer MoE (120B total, 12B active, 1M context) via OpenRouter.
  - `openai/gpt-oss-120b`: High-throughput open model hosted on Groq LPUs for zero-latency failover.
  - `meta-llama/llama-prompt-guard-2-22m`: Input security classifier for injection and jailbreak protection.
- **Orchestration & Agents:** LangChain, LangGraph, Pydantic v2.
- **Tools & Data:** Google Sheets API (`gspread`), Tavily Web Search, Telegram Bot API.
- **Media & Assembly Pipeline:** Edge-TTS / ElevenLabs, OpenAI Whisper (word-level timestamps), FFmpeg / MoviePy.

---

## 📁 Repository Structure

```
Agentic_AI_Workshop/
├── README.md
├── .env.example
├── requirements.txt
├── Day_1/
│   ├── LLM_Setup.ipynb
│   ├── Day 1 · How LLMs work and your first API call(Mentor_notes).html
│   └── README.md
├── Day_2/
│   ├── Startup_Marketing_Agent.ipynb
│   ├── Day 2 · Prompts, memory and the Python agents need(Mentor_notes).html
│   └── README.md
├── Day_3/
│   ├── Startup_Marketing_Agent.ipynb
│   ├── Day 3 · Your first agent, what an agent is, and LangChain(Mentor_notes).html
│   ├── tests.csv
│   └── README.md
├── Day_4/
│   ├── Startup_Marketing_Agent.ipynb
│   ├── Day 4 · Tools, structured output and Google Sheets(Mentor_notes).html
│   └── README.md
└── Day_5/
    ├── Startup_Marketing_Agent.ipynb
    ├── Day 5 · Memory and RAG, an agent that remembers and looks things up(Mentor_notes).html
    ├── RAG Working(Mentor_notes).html
    ├── tests.csv
    └── README.md
```

---

## 🚀 Getting Started

### Prerequisites
- Python 3.10+
- Jupyter Notebook / Google Colab
- API Keys:
  - [OpenRouter API Key](https://openrouter.ai/)
  - [Groq API Key](https://console.groq.com/)

### Setup Instructions
1. Clone this repository:
   ```bash
   git clone https://github.com/Sanjaysanjay31/24B11DS095_DriveReady_OPC_2026.git
   cd 24B11DS095_DriveReady_OPC_2026
   ```
2. Set up environment variables (for local execution):
   Copy `.env.example` to `.env` and add your keys:
   ```bash
   cp .env.example .env
   ```
   Or export them directly:
   ```bash
   export OPENROUTER_API_KEY="your-openrouter-key"
   export GROQ_API_KEY="your-groq-key"
   ```
3. For Google Colab:
   Add `OPENROUTER_API_KEY` and `GROQ_API_KEY` to **Colab Secrets (key icon)** in the left sidebar.
