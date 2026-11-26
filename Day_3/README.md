# Day 3 — Your First Agent: What an Agent Is, and LangChain

**Workshop:** One Person Company — 12-Day Agentic AI Workshop (Aditya University)  
**Project:** AI Startup Marketing Agent  
**Primary Provider:** OpenRouter — NVIDIA Nemotron 3.5 Super VL (Free)  
**Fallback Provider:** Groq — GPT-OSS 120B  
**Notebook:** [`Startup_Marketing_Agent.ipynb`](file:///c:/Skills/Agentic_AI_Workshop/Day_3/Startup_Marketing_Agent.ipynb)  

---

## 📌 Overview

A chatbot **talks**; an agent **acts to achieve a goal**. 

Day 3 transitions our startup marketing assistant into a structured **LangChain** workflow. We implement conversational memory via `ChatPromptTemplate` and `MessagesPlaceholder`, run automated keyword-based evaluation tests (`tests.csv`), and classify business tasks into plain code, single LLM calls, and autonomous agents.

---

## 🏗️ The 4 Parts of an Agent

1. **Brain**: The LLM reasoning engine (NVIDIA Nemotron 3.5 Super VL via OpenRouter, with Groq failover).
2. **Instructions**: The system prompt defining rules, boundaries, and marketing catalogue pricing.
3. **Memory**: Rolling conversational history tracking founder name, product details, and context.
4. **Tools**: Functions connected to an agent loop to perform actions rather than just generating words.

---

## 📁 Notebook Structure (Simple 4 Cells)

| Cell | Topic | Description |
|:---:|:---|:---|
| **1** | Setup & Dual LLM | Initializes LangChain models with OpenRouter primary and Groq fallback. Supports local `.env` and Colab Secrets. |
| **2** | Template, Memory & Chain | LCEL chain (`prompt \| llm \| StrOutputParser`) with rolling conversation history. |
| **3** | Evaluation Suite | Generates `tests.csv` and runs automated test passes with keyword matching and pass-rate calculation. |
| **4** | Task Classification | Analyzes business operations into Plain Code, Single LLM Call, and Autonomous Agent. |

---

## 🚀 How to Run

### In Google Colab
1. Click the **Open In Colab** badge in [`Startup_Marketing_Agent.ipynb`](file:///c:/Skills/Agentic_AI_Workshop/Day_3/Startup_Marketing_Agent.ipynb).
2. Set `OPENROUTER_API_KEY` and `GROQ_API_KEY` in **Colab Secrets (key icon)**.
3. Click `Runtime -> Run all`.

### Locally (VS Code / Jupyter)
1. Ensure your keys are in `.env`:
   ```env
   OPENROUTER_API_KEY=your_key
   GROQ_API_KEY=your_key
   ```
2. Run:
   ```bash
   jupyter notebook Day_3/Startup_Marketing_Agent.ipynb
   ```
