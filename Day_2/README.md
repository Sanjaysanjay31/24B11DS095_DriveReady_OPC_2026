# Day 2 — Prompts, Memory, and Python Fundamentals for Agents

**Project:** AI Startup Marketing Agent  

---

## 📌 Overview

Day 1 focused on connecting to LLM providers with resilient fallback logic. Day 2 shifts focus to controlling model behavior, enabling conversational memory, and implementing the core Python primitives that every autonomous agent relies on.

By applying these concepts to the **AI Startup Marketing Agent**, we build an intelligent assistant that understands founder marketing requests, extracts structured startup data, calculates campaign budgets, and maintains context across multi-turn conversations.

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