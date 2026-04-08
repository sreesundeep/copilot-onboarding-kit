# 📐 6. Output Templates & Diagram Reference

> Ready-to-fill templates for documenting your understanding. Copy, fill in, and save.

---

## Template 1: Project Summary Card

```markdown
# [PROJECT NAME] — Summary Card

| Field | Value |
|-------|-------|
| **Purpose** | [What does it do in 1 sentence] |
| **Users** | [Who uses it] |
| **Tech Stack** | [Languages, Frameworks, DBs] |
| **Repo** | [URL] |
| **Main Branch** | [main/master/develop] |
| **Build Command** | [npm run build / dotnet build / etc.] |
| **Run Command** | [npm start / dotnet run / etc.] |
| **Test Command** | [npm test / dotnet test / etc.] |
| **CI/CD** | [GitHub Actions / Azure Pipelines / etc.] |
| **Deployed To** | [AKS / App Service / AWS / etc.] |
| **Docs** | [Link to docs folder or wiki] |
| **Team Channel** | [Teams/Slack channel] |
```

---

## Template 2: Module Documentation

```markdown
# Module: [MODULE_NAME]

## Purpose
[1-2 sentences explaining what this module does]

## Key Files
| File | Purpose |
|------|---------|
| `[file1]` | [description] |
| `[file2]` | [description] |

## Public API
| Method/Endpoint | Parameters | Returns | Description |
|-----------------|-----------|---------|-------------|
| [name] | [params] | [return type] | [what it does] |

## Dependencies
- **Depends on**: [list of modules this depends on]
- **Depended by**: [list of modules that depend on this]

## Data Models
[Mermaid ER diagram or class diagram]

## Key Flows
[Mermaid sequence diagram of the main flow]

## Notes
- [Any gotchas, tech debt, or important context]
```

---

## Template 3: Flow Documentation

```markdown
# Flow: [FLOW_NAME] (e.g., "User Registration")

## Trigger
[What initiates this flow — API call, event, scheduled job]

## Happy Path
[Mermaid sequence diagram]

## Error Scenarios
| Error | Cause | Handling | User Impact |
|-------|-------|----------|-------------|
| [error] | [cause] | [how handled] | [what user sees] |

## Data Changes
| Table/Entity | Operation | Fields Affected |
|-------------|-----------|-----------------|
| [table] | INSERT/UPDATE/DELETE | [fields] |

## Side Effects
- [ ] Email sent
- [ ] Event published
- [ ] Cache updated
- [ ] Log entry written
- [ ] External API called
```

---

## Mermaid Diagram Quick Reference

### Architecture Diagram (Top-Down)
```mermaid
graph TD
    A[Component A] --> B[Component B]
    A --> C[Component C]
    B --> D[(Database)]
    C --> E[External API]
```

### Sequence Diagram
```mermaid
sequenceDiagram
    participant A as Client
    participant B as Server
    participant C as Database

    A->>B: Request
    B->>C: Query
    C-->>B: Result
    B-->>A: Response
```

### Flowchart (Decision Logic)
```mermaid
flowchart TD
    START([Start]) --> CHECK{Condition?}
    CHECK -->|Yes| ACTION1[Do This]
    CHECK -->|No| ACTION2[Do That]
    ACTION1 --> END1([End])
    ACTION2 --> END2([End])
```

### Entity Relationship
```mermaid
erDiagram
    PARENT ||--o{ CHILD : "has many"
    PARENT {
        int id PK
        string name
    }
    CHILD {
        int id PK
        int parentId FK
        string value
    }
```

### Class Diagram
```mermaid
classDiagram
    class Interface {
        <<interface>>
        +method1() ReturnType
        +method2(param) void
    }
    class Implementation {
        -privateField: Type
        +method1() ReturnType
        +method2(param) void
    }
    Interface <|.. Implementation
```

### State Machine
```mermaid
stateDiagram-v2
    [*] --> Created
    Created --> Active : activate
    Active --> Paused : pause
    Paused --> Active : resume
    Active --> Completed : complete
    Paused --> Cancelled : cancel
    Completed --> [*]
    Cancelled --> [*]
```

### Pie Chart (for tech stack breakdown, etc.)
```mermaid
pie title Codebase Composition
    "TypeScript" : 45
    "Python" : 30
    "YAML/Config" : 15
    "Other" : 10
```

### Gantt Chart (for onboarding timeline)
```mermaid
gantt
    title Onboarding Timeline
    dateFormat YYYY-MM-DD
    section Week 1
        Setup & High-Level    :a1, 2024-01-01, 2d
        Module Deep-Dives     :a2, after a1, 2d
        Flow Tracing          :a3, after a2, 1d
    section Week 2
        First Small PR        :b1, after a3, 2d
        Pair Programming      :b2, after b1, 3d
```

---

## Mermaid Syntax Cheat Sheet

| Element | Syntax | Notes |
|---------|--------|-------|
| Rectangle | `A[Text]` | Standard node |
| Rounded | `A(Text)` | Soft edges |
| Stadium | `A([Text])` | Start/End |
| Diamond | `A{Text}` | Decision |
| Database | `A[(Text)]` | Cylinder |
| Arrow | `A --> B` | Solid line |
| Dotted Arrow | `A -.-> B` | Dashed line |
| Arrow + Label | `A -->|label| B` | Labeled edge |
| Subgraph | `subgraph Title ... end` | Grouping |
| Color | `style A fill:#color` | Node styling |
| Note | `Note over A,B: text` | Sequence diagram notes |

---

## 🎓 Putting It All Together

After completing the onboarding, create one master document:

```markdown
# [Project Name] — Onboarding Summary

## 1. Architecture Overview
[Architecture diagram + 2-3 paragraph summary]

## 2. Tech Stack
[Categorized dependency list]

## 3. Module Map
[Table of all modules with 1-line descriptions]

## 4. Key Flows
[Top 3 flows with sequence diagrams]

## 5. Data Model
[ER diagram]

## 6. Getting Started
[Build/run/test commands]

## 7. Important Files
[Top 10 files every developer should know]

## 8. Glossary
[Domain-specific terms and their meanings]
```

---

## 🤝 Share with Your Team

Save your filled-in templates to the project's `docs/onboarding/` folder so the next person can:
1. Read your summaries first (saves them hours)
2. Use the same prompts to go deeper
3. Update the docs as the project evolves

---

*🎉 You've completed the onboarding kit! Happy coding!*
