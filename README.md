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

## 📅 12-Day Workshop Schedule & Implementation Plan

| Day | Date | Mode | Topic | Project Milestone & Deliverable |
|:---:|:---:|:---:|:---|:---|
| **Day 1** | Mon, 23 Nov 2026 | Online | **How LLMs work and your first API call** | **Resilient Multi-Provider Fallback**: Dual-provider LangChain integration (OpenRouter + Groq) and Llama Prompt Guard safety layer. |
| **Day 2** | Tue, 24 Nov 2026 | Online | **Prompts that work, JSON and Python basics** | **Startup Profiler & Schema**: Structured Pydantic extraction of product USP, audience, and problem statements into JSON. |
| **Day 3** | Wed, 25 Nov 2026 | Online | **Your first AI agent** | **Hook & Scriptwriting Agent**: Autonomous agent capable of creating problem-first viral video hooks and timed 9:16 scripts. |
| **Day 4** | Thu, 26 Nov 2026 | Online | **Tools, Pydantic and Google Sheets** | **Research Tools & Content Tracker**: Live web search tools for market stats and Google Sheets logging for video concepts. |
| **Day 5** | Fri, 27 Nov 2026 | Online | **Memory and RAG** | **Brand Knowledge Base**: Vector storage of startup pitch decks and competitor case studies for persistent context. |
| **Day 6** | Sat, 28 Nov 2026 | Online | **Workflows with LangGraph** | **Orchestrated Production Graph**: Stateful multi-node workflow linking Profiler $\rightarrow$ Researcher $\rightarrow$ Scriptwriter. |
| **Day 7** | Mon, 30 Nov 2026 | Offline | **Hand-offs and owner approval** | **Human-in-the-Loop Gate**: Interactive founder review portal (Streamlit/CLI) to edit scripts and approve storyboard frames. |
| **Day 8** | Tue, 01 Dec 2026 | Offline | **An AI workforce with a supervisor** | **Supervised Multi-Agent Team**: Supervisor agent managing dedicated Creative, Research, Visual, and QA subagents. |
| **Day 9** | Wed, 02 Dec 2026 | Offline | **Capstone: Telegram, Google Sheets and Gmail** | **Notification & Export Pipeline**: Real-time Telegram alerts on script approval, automated Google Sheet updates, and email drafts. |
| **Day 10** | Thu, 03 Dec 2026 | Offline | **Reliable, safe and affordable agents** | **Guardrails & Cost Optimization**: Token budget controls, caching, rate-limit handlers, and safety checks on generated media. |
| **Day 11** | Fri, 04 Dec 2026 | Offline | **Test it, prove it, show it** | **Automated Video Stitching**: TTS voice generation, subtitle alignment (Whisper), and FFmpeg/MoviePy compilation. |
| **Day 12** | Sat, 05 Dec 2026 | Offline | **Demo Day** | **Live Capstone Showcase**: Complete autonomous run generating a published YouTube Short/Reel from a raw URL. |

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
├── Day_1/                             # Day 1: LLM Fundamentals & Resilient API Setup
│   ├── LLM_Setup.ipynb                # Production notebook with dual-provider failover
│   └── README.md                      # Detailed Day 1 technical documentation
└── Day_2/                             # Upcoming: Structured Prompting & Pydantic Schemas
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
   git clone https://github.com/<your-username>/Agentic_AI_Workshop.git
   cd Agentic_AI_Workshop
   ```
2. Set up environment variables:
   ```bash
   export OPENROUTER_API_KEY="your-openrouter-key"
   export GROQ_API_KEY="your-groq-key"
   ```
3. Open [`Day_1/LLM_Setup.ipynb`](file:///c:/Skills/Agentic_AI_Workshop/Day_1/LLM_Setup.ipynb) and run all cells.
