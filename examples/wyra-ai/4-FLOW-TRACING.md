# 🔄 Wyra — End-to-End Flow Tracing

> The 5 most important user journeys traced step by step with diagrams.

---

## Flow 1: First-Time Setup → First Campaign (The "Day 1" Flow)

> **Goal:** Go from zero to a live campaign in 15 minutes.

```mermaid
sequenceDiagram
    participant User
    participant Settings
    participant Intelligence
    participant Offerings
    participant Campaigns
    participant AI_SDR as AI SDR

    User->>Settings: Subscribe + configure account
    User->>AI_SDR: Create AI SDR (name, email, LinkedIn)
    Note over AI_SDR: 14-day warmup begins automatically
    
    User->>Intelligence: Review auto-generated company profile
    User->>Intelligence: Upload artifacts (case studies, decks)
    Note over Intelligence: Wyra generates outreach ideas
    
    User->>Intelligence: Browse & like/dislike ideas
    User->>Offerings: Build offering from best idea (65%+ pre-filled)
    User->>Offerings: Refine value prop, pain points, outcomes
    
    User->>Campaigns: Open 5-step campaign wizard
    Note over Campaigns: Step 1: Value Prop<br/>Step 2: Persona<br/>Step 3: Why Now<br/>Step 4: Messaging<br/>Step 5: Review & Launch
    
    User->>Campaigns: Launch campaign 🚀
    Note over Campaigns: Executes at warmup pace<br/>until Day 14, then full volume
    
    Campaigns->>AI_SDR: AI SDR begins outreach
    AI_SDR->>AI_SDR: Sends emails + LinkedIn messages
```

### Pre-requisites Checklist
- [ ] Active Wyra subscription
- [ ] At least one AI SDR configured (name + email + LinkedIn)
- [ ] Understand that warmup = 14 days (but you can build & launch during it)

---

## Flow 2: Outreach Idea → Live Campaign (The Core Loop)

> **Goal:** Turn an AI-generated idea into a running campaign.

```mermaid
flowchart TD
    A["🧠 Intelligence generates<br/>Outreach Idea"] --> B{"👀 Review the idea"}
    B -->|"Not relevant"| C["👎 Dislike + reason<br/>Engine learns to avoid"]
    B -->|"Interesting!"| D["👍 Like it<br/>More ideas in this direction"]
    D --> E["📖 Open detail view<br/>See persona, pain points, angle"]
    E --> F["🔨 Build into Offering<br/>One click — 65%+ pre-filled"]
    F --> G["✏️ Refine Offering<br/>Edit value prop, outcomes, proof"]
    G --> H["🚀 Create Campaign<br/>5-step wizard"]
    H --> I{"Contact source?"}
    I -->|"Wyra's DB"| J["Define persona filters<br/>Wyra finds + enriches"]
    I -->|"Your list"| K["Upload CSV or select list<br/>Persona step skipped"]
    I -->|"CRM reactivation"| L["Import dormant contacts<br/>Re-enrich with fresh angle"]
    J & K & L --> M["📬 Campaign goes live<br/>Email + LinkedIn + Calls"]

    style A fill:#6366f1,color:#fff
    style F fill:#10b981,color:#fff
    style M fill:#ec4899,color:#fff
```

---

## Flow 3: Campaign Running → Handling Replies (The "Daily" Flow)

> **Goal:** Your 5-minute daily routine for managing replies and converting leads.

```mermaid
sequenceDiagram
    participant AI_SDR as AI SDR
    participant Prospect
    participant Interactions
    participant User as You (Human)
    participant CRM

    AI_SDR->>Prospect: Email / LinkedIn / Connection request
    
    alt Prospect replies
        Prospect-->>Interactions: Reply received
        Interactions->>Interactions: Classify sentiment automatically
        
        alt 🔥 Hot Lead / Interested
            Interactions->>User: Flag as Hot Lead
            Interactions->>User: Show AI-suggested response
            User->>User: Review + edit response
            User->>Prospect: Send personalized follow-up
            User->>CRM: Sync qualified lead
        end
        
        alt ❌ Not Interested
            Interactions->>Interactions: Stop outreach automatically
            Note over Interactions: No further messages sent
        end
        
        alt 🏖️ Out of Office
            Interactions->>Interactions: Extract referral info
            Note over Interactions: Auto-detects alternate contacts
        end
    end

    Note over Interactions: All reply data feeds back<br/>into Intelligence Engine
```

### Your Daily Routine

```mermaid
flowchart LR
    A["☀️ Morning"] --> B["📊 Check Dashboard<br/>Reply Rate + Hot Leads"]
    B --> C["💬 Open Interactions<br/>Filter by 'Replied'"]
    C --> D["🔥 Handle Hot Leads<br/>Review AI suggestion → respond"]
    D --> E["📈 Check Campaigns<br/>All active? Volume normal?"]
    E --> F["✅ Done in 5 min"]

    style A fill:#f59e0b,color:#000
    style F fill:#10b981,color:#fff
```

---

## Flow 4: Uploading an Artifact → New Campaign Angle

> **Goal:** Turn a new customer win into your next campaign.

```mermaid
sequenceDiagram
    participant User
    participant Artifacts
    participant Engine as Intelligence Engine
    participant Ideas as Outreach Ideas
    participant Offerings
    participant Campaigns

    User->>Artifacts: Upload case study (PDF/DOCX/PPTX)
    Note over Artifacts: Processing... (few minutes)
    
    Artifacts->>Engine: Extract client, industry,<br/>pain points, outcomes, metrics
    Engine->>Ideas: Generate 1 Outreach Idea<br/>Tagged with "Artifact" badge
    
    Note over Ideas: Appears on Intelligence tab<br/>+ full Ideas page
    
    User->>Ideas: Open artifact-sourced idea
    User->>Offerings: Build into offering (pre-filled)
    User->>Campaigns: Launch campaign targeting<br/>same industry + persona as the win
    
    Note over Campaigns: 🎯 Your best campaigns<br/>come from real customer wins
```

> **The compounding effect:** Close a deal → upload case study → Wyra generates idea targeting same profile → launch campaign → close another deal → repeat.

---

## Flow 5: New Team Member Onboarding

> **Goal:** Add a new sales rep and get them running campaigns.

```mermaid
flowchart TD
    A["👤 Admin invites team member"] --> B["🤖 Create their AI SDR<br/>Name + Email + LinkedIn + Calendar"]
    B --> C["⏰ 14-day warmup starts<br/>automatically"]
    C --> D{"While warming up..."}
    D --> E["📄 Upload their case studies<br/>as artifacts"]
    D --> F["📦 Build offerings from<br/>their territory/expertise"]
    D --> G["🚀 Launch campaigns<br/>(run at warmup pace)"]
    E & F & G --> H["📅 Day 14: Full capacity!<br/>Campaigns auto-scale to full volume"]
    H --> I["💬 Monitor Interactions<br/>Handle replies daily"]

    style A fill:#6366f1,color:#fff
    style C fill:#f59e0b,color:#000
    style H fill:#10b981,color:#fff
```

> **Pro tip:** Invite 3 team members at once — all 3 warm up in parallel and hit full capacity on the same day, tripling your outreach.

---

## 🗺️ The Complete User Journey Map

```mermaid
flowchart TB
    subgraph "🔧 One-Time Setup"
        S1["Subscribe"] --> S2["Create AI SDR"]
        S2 --> S3["14-day warmup begins"]
    end

    subgraph "📈 Build (During Warmup)"
        B1["Intelligence auto-researches you"] --> B2["Upload artifacts"]
        B2 --> B3["Browse outreach ideas"]
        B3 --> B4["Build offerings"]
    end

    subgraph "🚀 Execute (Day 14+)"
        E1["Launch campaigns<br/>(5-step wizard)"] --> E2["AI SDR sends<br/>Email + LinkedIn + Calls"]
        E2 --> E3["Replies surface in<br/>Interactions"]
    end

    subgraph "🔄 Daily Loop"
        D1["Check Dashboard<br/>(2 min)"] --> D2["Handle hot leads<br/>in Interactions"]
        D2 --> D3["Reply data feeds back<br/>into Intelligence"]
        D3 --> D4["New/better ideas<br/>appear"]
        D4 --> D1
    end

    S3 --> B1
    B4 --> E1
    E3 --> D1

    style S1 fill:#6366f1,color:#fff
    style E1 fill:#ec4899,color:#fff
    style D1 fill:#10b981,color:#fff
    style D3 fill:#f59e0b,color:#000
```

---

*This completes the Wyra onboarding documentation! 🎉*
