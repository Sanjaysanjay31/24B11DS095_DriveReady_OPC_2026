# Day 4 — Tools, Structured Output, and Google Sheets


**Project:** AI Startup Marketing Agent  
**Primary Provider:** OpenRouter — NVIDIA Nemotron 3.5 Super VL (Free)  
**Fallback Provider:** Groq — GPT-OSS 120B   

---

## 📌 Overview

On Day 3, our agent learned conversational memory. On Day 4, it gains **autonomous tools**—Python functions it calls by itself to fetch factual data and write records into a persistent database.

We connect the **AI Startup Marketing Agent** to a live Google Sheet (`1WryffEEH-N9TpWcwg8pvdaNU0XGzQWqBRS2Lnt0Ro90`). The agent answers pricing and timing questions using dedicated tools, gathers required campaign specifications from the founder, validates the details with a **Pydantic schema**, and automatically appends a new row to the sheet upon confirmation.

---

## 🛠️ The Three Autonomous Tools

```
Founder Chat Message
        │
        ▼
[ Agent Decision Loop ]
        │
        ├── get_service_price()       ➔ Fetches exact price from SERVICES catalogue
        ├── check_operating_hours()   ➔ Checks rendering & support pipeline schedule
        └── log_campaign_order()      ➔ Validates with Pydantic & logs to Google Sheet
```

1. **`get_service_price(service: str, qty: int = 1)`**:
   Looks up prices for short-form video services (hooks, scripts, storyboards, voiceovers, assembly).
2. **`check_operating_hours(day: str)`**:
   Returns the agency's working hours and pipeline rendering schedule for any given day.
3. **`log_campaign_order(client_name, startup_name, service, platform, target_date)`**:
   Enforces structured validation using Pydantic `CampaignOrder(BaseModel)` and records the confirmed campaign into Google Sheets:
   `[client_name, startup_name, service, platform, target_date, total_price]`

---

## 📋 Notebook Structure (4 Core Cells)

| Cell | Topic | Description |
|:---:|:---|:---|
| **1** | Environment & Sheets Setup | Configures dual LLM fallback (OpenRouter + Groq) and initializes `gspread` connection to Google Sheet. |
| **2** | Catalogue & Pydantic Schema | Defines `SERVICES` pricing, `HOURS` schedule, and the `CampaignOrder` data validation model. |
| **3** | Tool Definitions | Registers `@tool` functions for price lookup, hours checking, and sheet logging. |
| **4** | Agent Execution | Binds tools to `create_agent()`, manages multi-turn memory, and runs test booking workflows. |

---




