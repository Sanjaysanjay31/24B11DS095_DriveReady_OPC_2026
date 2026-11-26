# Day 2 — Prompts, Memory, and Python Fundamentals for Agents

**Workshop:** One Person Company — 12-Day Agentic AI Workshop  
**Institution:** Department of Technical Training, Aditya University  
**Project:** AI Startup Marketing Agent  
**Primary Provider:** OpenRouter — NVIDIA Nemotron 3.5 Super VL (Free)  
**Fallback Provider:** Groq — GPT-OSS 120B  
**Notebook:** [`Startup_Marketing_Assistant.ipynb`](file:///c:/Skills/Agentic_AI_Workshop/Day_2/Startup_Marketing_Assistant.ipynb)  
**Environment:** Dual-Mode (Google Colab & Local Python with `.env`)  

---

## 📌 Overview

Day 1 established multi-provider LLM connectivity and failover. Day 2 shifts focus to controlling model behavior, enabling conversational memory, and implementing the core Python primitives that every autonomous agent relies on.

By applying these concepts to the **AI Startup Marketing Agent**, we build an intelligent assistant that understands founder marketing requests, extracts structured startup data, calculates campaign budgets, and maintains context across multi-turn conversations.

---

## 🏗️ Architecture: Dual-Provider + Dual-Environment

```
                ┌──────────────────────────────────────┐
                │          Environment Setup           │
                │  Local: .env via python-dotenv       │
                │  Colab: google.colab.userdata        │
                └──────────────────┬───────────────────┘
                                   │
                                   ▼
                ┌──────────────────────────────────────┐
                │        ask_llm(messages)             │
                │                                      │
                │  1. Primary: OpenRouter              │
                │     (NVIDIA Nemotron 3.5 Super VL)   │
                │                 │                    │
                │         (Fail / Timeout)             │
                │                 ▼                    │
                │  2. Fallback: Groq (GPT-OSS 120B)    │
                └──────────────────┬───────────────────┘
                                   │
                                   ▼
                ┌──────────────────────────────────────┐
                │    Startup Marketing Assistant UI    │
                │    - Intent Classifier (Few-shot)    │
                │    - JSON Brief Extractor            │
                │    - Cost Calculator with Decorator  │
                │    - Rolling Memory Buffer (5 turns) │
                └──────────────────────────────────────┘
```

---

## 🧠 Core Topics & Concepts Implemented

### 1. Messages and Roles
LLMs process conversational interactions through three distinct roles:
- `system`: Permanent behavioral constraints, rules, and operational context.
- `user`: Prompts and messages submitted by the startup founder.
- `assistant`: Generated replies and tool decisions produced by the model.

### 2. The Structured System Prompt
The system prompt is structured into four distinct pillars:
- **ROLE**: Intelligent AI Startup Marketing Assistant for early-stage founders.
- **FACTS**: Explicit service catalogue with fixed prices in rupees.
- **RULES**: Boundary conditions (never guarantee viral views, never invent fake user stats, quote prices only from the catalogue).
- **FORMAT**: Concise responses (under 60 words) with an encouraging, practical tone.

### 3. Few-Shot Intent Classification
To route incoming requests to specialized agent sub-modules, a few-shot prompt classifies inputs into exact categories:
- `hook_creation`
- `scriptwriting`
- `storyboard`
- `voiceover`
- `video_assembly`
- `pricing_inquiry`
- `other`

### 4. Structured JSON Extraction
Extracts unstructured founder descriptions into validated JSON schema:
```json
{
    "founder_name": "Sanjay",
    "startup_name": "DevPulse",
    "product_domain": "AI code review assistant",
    "services_requested": ["viral_hook_generation", "short_script_writing"],
    "target_problem": "Developers are ignoring pull requests and shipping bugs due to fatigue"
}
```
Includes sanitization logic to strip markdown code blocks (```` ```json ````) before executing `json.loads()`.

### 5. Memory by Hand (Sliding Window Buffer)
Maintains conversational continuity across multiple turns without inflating token context:
- Stores interactions in a list `marketing_history`.
- Injects `recent_history = marketing_history[-(MAX_TURNS * 2):]` into each API call.
- Implements rollback (`marketing_history.pop()`) in case of API failure so the state is never corrupted.

### 6. Python Constructs for Agents
- **Dictionaries**: `MARKETING_SERVICES` mapping services to prices.
- **Type Hints & Docstrings**: Explicit type annotations (`services: list[str] -> int`) and docstrings for future tool registration.
- **Decorators**: `@log_execution` wrapping functions with `@functools.wraps` to audit execution names and returned results.
- **Exception Handling**: Catching `RateLimitError`, `AuthenticationError`, and `APIConnectionError` to prevent runtime halts.

---

## 📊 Notebook Structure

| Cell | Type | Description |
|:---:|:---:|:---|
| **0** | Markdown | Colab badge and Day 2 curriculum overview |
| **1** | Code | Install dependencies (`openai`, `python-dotenv`) |
| **2** | Code | Dual client setup (OpenRouter primary, Groq fallback) with `.env` and Colab Secrets loading |
| **3** | Code | Marketing service catalogue and pricing dictionary |
| **4** | Code | System prompt (Role, Facts, Rules, Format) |
| **5** | Code | Resilient LLM invocation helper function (`ask_llm`) with automatic failover |
| **6** | Code | Single-turn marketing chat helper (`marketing_chat`) |
| **7** | Code | Verification query for service catalogue compliance |
| **8** | Code | Few-shot marketing request classifier (`classify_marketing_request`) |
| **9** | Code | Unstructured brief extraction into JSON (`extract_startup_details`) |
| **10** | Code | Campaign cost calculation with `ValueError` guards |
| **11** | Code | Execution logging decorator (`@log_execution`) |
| **12** | Code | Robust exception handling wrapper (`safe_marketing_chat`) |
| **13** | Code | Sliding window conversation memory (`marketing_chat_with_memory`) |
| **14** | Code | Automated 6-turn dialogue test verifying contextual memory retention |
| **15** | Code | Interactive command-line chat session |

---

## 🚀 How to Run

### Option A: Local Execution (VS Code / Jupyter)
1. Copy `.env.example` to `.env` in the root folder:
   ```bash
   cp .env.example .env
   ```
2. Open `.env` and paste your API keys:
   ```env
   OPENROUTER_API_KEY=your_openrouter_api_key
   GROQ_API_KEY=your_groq_api_key
   ```
3. Install dependencies:
   ```bash
   pip install openai python-dotenv
   ```
4. Run the notebook:
   ```bash
   jupyter notebook Day_2/Startup_Marketing_Assistant.ipynb
   ```

### Option B: Google Colab
1. Click the **Open In Colab** badge at the top of [`Startup_Marketing_Assistant.ipynb`](file:///c:/Skills/Agentic_AI_Workshop/Day_2/Startup_Marketing_Assistant.ipynb).
2. In Colab's left sidebar, click **Secrets (key icon)** and add:
   - `OPENROUTER_API_KEY`: Your OpenRouter API key.
   - `GROQ_API_KEY`: Your Groq API key.
3. Run all cells (`Runtime -> Run all`).
