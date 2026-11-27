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
└── Day_4/
    ├── Startup_Marketing_Agent.ipynb
    ├── Day 4 · Tools, structured output and Google Sheets(Mentor_notes).html
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
