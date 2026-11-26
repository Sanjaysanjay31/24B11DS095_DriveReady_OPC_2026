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

## 📅 Completed Workshop Milestones (Days 1–3)

| Day | Date | Mode | Topic | Project Milestone & Deliverable |
|:---:|:---:|:---:|:---|:---|
| **Day 1** | Mon, 23 Nov 2026 | Online | **How LLMs work and your first API call** | **Resilient Multi-Provider Fallback**: Dual-provider LangChain integration (OpenRouter + Groq) and Llama Prompt Guard safety layer. |
| **Day 2** | Tue, 24 Nov 2026 | Online | **Prompts that work, JSON and Python basics** | **Startup Marketing Agent**: Structured system prompt, few-shot classification, JSON brief extraction, and sliding-window memory. |
| **Day 3** | Wed, 25 Nov 2026 | Online | **Your first AI agent** | **First LangChain Agent**: LCEL chain with memory, automated test suite (`tests.csv`), and task classification (Code vs LLM vs Agent). |

---

## 🛠️ Technology Stack

- **Large Language Models:**
  - `nvidia/nemotron-3.5-super-vl:free`: Hybrid Mamba-Transformer MoE (120B total, 12B active, 1M context) via OpenRouter.
  - `openai/gpt-oss-120b`: High-throughput open model hosted on Groq LPUs for zero-latency failover.
  - `meta-llama/llama-prompt-guard-2-22m`: Input security classifier for injection and jailbreak protection.
- **Orchestration & Agents:** LangChain, LangGraph, Pydantic v2.
- **Tools & Data:** Tavily Web Search, Google Sheets API, Telegram Bot API.
- **Media & Assembly Pipeline:** Edge-TTS / ElevenLabs, OpenAI Whisper (word-level timestamps), FFmpeg / MoviePy.

---

## 📁 Repository Structure

```
Agentic_AI_Workshop/
├── README.md                          # Master workshop repository documentation
├── .env.example                       # Environment variables template
├── Day_1/                             # Day 1: LLM Fundamentals & Resilient API Setup
│   ├── LLM_Setup.ipynb                # Production notebook with dual-provider failover
│   └── README.md                      # Day 1 technical documentation
├── Day_2/                             # Day 2: Prompts, Memory & Python Agent Fundamentals
│   ├── Startup_Marketing_Agent.ipynb  # Interactive marketing agent notebook
│   └── README.md                      # Day 2 curriculum and technical documentation
└── Day_3/                             # Day 3: First Agent, LangChain & Evaluation
    ├── Startup_Marketing_Agent.ipynb  # LangChain LCEL chain with memory & test suite
    └── README.md                      # Day 3 documentation and eval guide
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
4. Launch the notebooks:
   - Day 1: [`Day_1/LLM_Setup.ipynb`](file:///c:/Skills/Agentic_AI_Workshop/Day_1/LLM_Setup.ipynb)
   - Day 2: [`Day_2/Startup_Marketing_Assistant.ipynb`](file:///c:/Skills/Agentic_AI_Workshop/Day_2/Startup_Marketing_Assistant.ipynb)
