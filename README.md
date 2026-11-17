# 🚀 AI Lead Generation & CRM Automation

<p align="center">
  <img src="https://img.shields.io/badge/Workflow-n8n-FF6584?style=for-the-badge&logo=n8n&logoColor=white" alt="n8n" />
  <img src="https://img.shields.io/badge/Type-Lead%20Scoring-blue?style=for-the-badge" alt="Lead Scoring" />
  <img src="https://img.shields.io/badge/Status-Production%20Ready-success?style=for-the-badge" alt="Production Ready" />
  <img src="https://img.shields.io/badge/License-MIT-orange?style=for-the-badge" alt="License" />
</p>

A lightweight, high-performance **n8n automation** that instantly captures website leads, validates contact details, calculates an intelligent qualification score, and routes actionable insights to your sales pipeline.

---

## 🧭 System Flow & Architecture

```mermaid
flowchart TD
    %% Styling
    classDef input fill:#e1f5fe,stroke:#0288d1,stroke-width:2px,color:#01579b;
    classDef process fill:#fff3e0,stroke:#f57c00,stroke-width:2px,color:#e65100;
    classDef output fill:#e8f8f5,stroke:#26a69a,stroke-width:2px,color:#004d40;
    classDef ext fill:#f3e5f5,stroke:#8e24aa,stroke-width:2px,color:#4a148c;

    Form["🌐 Web Form / Landing Page"]:::input
    Webhook["📥 1. Lead Intake Webhook"]:::input
    Validate["⚙️ 2. Validate & Score Engine"]:::process
    Response["📤 3. Instant API Response"]:::output

    Form -->|POST JSON| Webhook
    Webhook --> Validate
    Validate -->|Score & Priority| Response
    Response -->|JSON Result| Form

    %% Integration Ecosystem
    subgraph Ecosystem ["🔌 Optional Next Steps & Integrations"]
        LLM["🤖 AI Summaries (OpenAI / Gemini)"]:::ext
        CRM["📊 CRM Sync (HubSpot / Notion / Airtable)"]:::ext
        Alerts["💬 Team Alerts (Slack / Email)"]:::ext
    end

    Validate -.-> LLM
    Validate -.-> CRM
    Validate -.-> Alerts
```

---

## ⚡ How It Works in 3 Steps

| Step | Component | Description |
| :---: | :--- | :--- |
| **1** | **Ingest** | Captures incoming lead requests from any contact form via a secure webhook. |
| **2** | **Score** | Evaluates project budget, urgency, company name, and requirements to generate a **0–100 score**. |
| **3** | **Route** | Flags the lead as **`HOT`**, **`WARM`**, or **`COLD`** with immediate next-step guidance. |

---

## 🎯 Lead Priority Matrix

```
   Score Range        Priority          Recommended Action
 ┌──────────────┬──────────────────┬──────────────────────────────────────────┐
 │   70 – 100   │   🔥  HOT        │   Call immediately & book discovery call  │
 │   40 – 69    │   ⚡  WARM       │   Send personalized follow-up in 24 hrs   │
 │    0 – 39    │   ❄️  COLD       │   Enroll in long-term nurture sequence    │
 └──────────────┴──────────────────┴──────────────────────────────────────────┘
```

---

## 🔌 APIs & Integrations Required

### 1. Inbound Webhook (Core)
- **Method:** `POST`
- **Path:** `/webhook/portfolio-lead-intake`
- **Payload Schema:**
  ```json
  {
    "name": "Jane Doe",
    "email": "jane@example.com",
    "company": "Acme Corp",
    "budget": 10000,
    "timeline": "immediate",
    "message": "Looking for n8n CRM automation."
  }
  ```

### 2. Connected & Extensible APIs

| Service | Category | Purpose | Status |
| :--- | :--- | :--- | :--- |
| **Webhook API** | Core | Ingests lead submissions from web forms | `Included` |
| **OpenAI / Gemini API** | AI & LLM | Generates executive summaries & pitch drafts | `Ready to connect` |
| **HubSpot / Airtable API** | CRM | Auto-creates contacts, deals, and notes | `Ready to connect` |
| **Slack / Resend API** | Notifications | Real-time alerts for high-value `HOT` leads | `Ready to connect` |

---

## 🚀 Quick Start

1. **Import:** In your n8n workspace, click **Add Workflow** > **Import from File** and select [`AI_Lead_Generation_CRM.json`](./AI_Lead_Generation_CRM.json).
2. **Activate:** Open the **Lead Intake Webhook** node and switch the workflow toggle to **Active**.
3. **Connect:** Point your website form's `POST` request to the generated webhook URL.

---

## 📄 License

Distributed under the [MIT License](LICENSE).
