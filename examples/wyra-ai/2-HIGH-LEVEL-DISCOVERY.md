# 🏗️ Wyra — High-Level Architecture & Platform Overview

> **What is Wyra?** The GTM (Go-To-Market) Intelligence Layer — a pre-CRM platform that turns market signals into targeted outreach with humans in control at every decision point.

---

## 🎯 What Problem Does Wyra Solve?

Effective GTM needs three things at once:

1. **Know your value** clearly (what you sell and why it matters)
2. **Know who needs it** and why now (intelligence)
3. **Execute outreach** with relevance at scale (campaigns)

No single tool did all three with ecosystem intelligence built in. **Wyra fills that gap.**

---

## 🧠 The Wyra Intelligence Loop

This is the **core concept** — everything in the platform revolves around this self-improving loop:

```mermaid
graph TD
    A["🧠 Intelligence<br/>Living company analysis<br/>continuously updated"] --> B["💡 Outreach Ideas<br/>AI-generated campaign angles<br/>signal-informed"]
    B --> C["📦 Offerings<br/>Structured pitch<br/>confidence-scored"]
    C --> D["🚀 Campaigns<br/>Targeted execution<br/>email + LinkedIn + calls"]
    D --> E["💬 Interactions<br/>Human reviews replies<br/>+ pipeline syncs to CRM"]
    E -->|"Performance data feeds back<br/>new signals, sharper ideas"| A

    style A fill:#6366f1,color:#fff
    style B fill:#8b5cf6,color:#fff
    style C fill:#a855f7,color:#fff
    style D fill:#ec4899,color:#fff
    style E fill:#f43f5e,color:#fff
```

> ☝️ **Key insight:** The loop doesn't reset — it **compounds**. Every campaign produces interaction data that sharpens the next wave of ideas.

---

## 🏠 Platform Architecture

```mermaid
graph TB
    subgraph "👤 User Layer"
        USER[Sales / Marketing / Pre-Sales / Leadership]
    end

    subgraph "🤖 AI Agent"
        GIL["Gil — Wyra's AI Agent<br/>Trained on AWS cloud services,<br/>partner programs & ecosystem signals"]
    end

    subgraph "📊 Intelligence Engine"
        CI[Company Intelligence<br/>Auto-researched profile]
        OI[Outreach Ideas<br/>AI-generated angles]
        ART[Artifacts<br/>Case studies, proposals, decks]
        FA[Focus Areas<br/>Solutions, Industries, Tech Stack]
    end

    subgraph "🎯 Execution Engine"
        OFF[Offerings<br/>Structured value props]
        CAMP[Campaigns<br/>Multi-channel outreach]
        SDR[AI SDR<br/>Your identity at scale]
    end

    subgraph "📬 Engagement Layer"
        EMAIL[Email Outreach]
        LI[LinkedIn Outreach]
        CALL[Click-to-Call]
        INT[Interactions<br/>Reply management + AI suggestions]
    end

    subgraph "📈 Analytics"
        DASH[Dashboard<br/>Metrics, reply intelligence, ROI]
    end

    subgraph "🔗 External"
        CRM[CRM Sync]
        LIAPI[LinkedIn API]
        EMAILP[Email Provider]
    end

    USER --> GIL
    GIL --> CI & OI
    ART --> OI
    CI --> FA
    OI --> OFF
    OFF --> CAMP
    CAMP --> SDR
    SDR --> EMAIL & LI & CALL
    EMAIL & LI & CALL --> INT
    INT --> USER
    INT -->|"feeds back"| CI
    CAMP --> DASH
    INT --> CRM

    style GIL fill:#6366f1,color:#fff
    style SDR fill:#ec4899,color:#fff
    style INT fill:#f59e0b,color:#000
```

---

## 🧩 Platform Modules at a Glance

| Module | What It Does | Key Concept |
|--------|-------------|-------------|
| **Intelligence** | Auto-researches your company, generates outreach ideas | Living analysis — never static |
| **Outreach Ideas** | AI-generated campaign angles from signals + your artifacts | Like/dislike trains the engine |
| **Offerings** | Structured value propositions with confidence scoring | Your pitch, refined by AI |
| **Campaigns** | Multi-channel execution (email + LinkedIn + calls) | 5-step wizard: Value Prop → Persona → Why Now → Messaging → Launch |
| **AI SDR** | Your professional identity running outreach at scale | Not a bot — it's *you*, amplified |
| **Interactions** | Reply management with AI-suggested responses | Human-in-the-loop — you close, AI opens |
| **Lists** | Contact management — upload CSV, use Wyra's DB, or CRM reactivation | Three paths into campaigns |
| **Dashboard** | Real-time metrics, reply intelligence, ROI | Your 2-minute morning briefing |
| **Settings & Admin** | Domains, email accounts, team management | Infrastructure for deliverability |

---

## 🔑 Key Concepts to Know

### 🤖 Gil — The AI Agent
Gil is Wyra's AI agent, trained on **AWS cloud services, partner programs, and ecosystem signals**. Gil:
- Analyzes your company and market position
- Generates campaign ideas with full offering scaffolding
- Scores contacts for relevance
- Executes outreach across email, LinkedIn, and calls

Gil is the **first** in Wyra's verticalized agent family. More agents (for other ecosystems) are coming.

### 🧑‍💼 AI SDR (Sales Development Representative)
- **Not a bot** — it's YOUR identity (your name, email, LinkedIn) executing at scale
- Each team member gets their own AI SDR
- Manages sending reputation automatically
- Goes through a **14-day warmup** before full-volume sending

### 🔄 Human-in-the-Loop
Wyra is **not** fire-and-forget:
- AI executes outreach → replies surface in **Interactions**
- Humans review, edit, and approve every response
- Hot leads are flagged automatically
- AI suggests replies, but **you decide**

---

## 👥 Who Uses Wyra?

```mermaid
graph LR
    subgraph "Revenue Team"
        SALES["🎯 Sales Teams<br/>Warm, pre-qualified pipeline<br/>with full context"]
        MKT["📊 Marketing Teams<br/>Campaign intelligence &<br/>reply analytics"]
        PRESALES["🔧 Pre-Sales Teams<br/>Enriched prospect profiles<br/>& discovery questions"]
        LEAD["👔 Leadership<br/>Full pipeline visibility<br/>& ROI metrics"]
    end

    style SALES fill:#10b981,color:#fff
    style MKT fill:#3b82f6,color:#fff
    style PRESALES fill:#f59e0b,color:#000
    style LEAD fill:#8b5cf6,color:#fff
```

---

## 🚦 Three Ways to Start a Campaign

```mermaid
flowchart TD
    START{How do you want<br/>to find contacts?} -->|"No list needed"| A["🔍 Wyra's Database<br/>Define offering + persona<br/>Wyra finds & enriches contacts"]
    START -->|"Upload a list"| B["📋 Your Own Contacts<br/>Upload LinkedIn URLs or emails<br/>Wyra enriches with your offering context"]
    START -->|"Dormant pipeline"| C["🔄 CRM Reactivation<br/>Re-enrich stale CRM contacts<br/>Fresh offering-led angle"]

    A --> D["📦 Offering shapes intelligence"]
    B --> D
    C --> D
    D --> E["🚀 Campaign Executes<br/>Email + LinkedIn + Calls"]

    style START fill:#6366f1,color:#fff
    style D fill:#f59e0b,color:#000
    style E fill:#ec4899,color:#fff
```

---

## ⚡ What Wyra is NOT

| ❌ NOT this | ✅ What it IS |
|---|---|
| Not a CRM | Operates **before** the CRM, feeding it qualified pipeline |
| Not a data provider | Enrichment is tied to **your specific offering context** |
| Not marketing automation | Generates the **strategy**, not just the sends |
| Not fire-and-forget | **Humans stay in the decision seat** at every step |

---

*Next → [3-MODULE-DEEP-DIVE.md](3-MODULE-DEEP-DIVE.md) — Detailed breakdown of each module*
