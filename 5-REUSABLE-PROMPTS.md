# 📋 5. Reusable Prompts Cheat Sheet

> Copy-paste these prompts into GitHub Copilot Chat (`@workspace`) for any project. Replace `[PLACEHOLDERS]` with your specifics.

---

## 🏠 Project Overview Prompts

### The "Explain Everything" Prompt
```
@workspace Give me a complete overview of this project:
1. What does this application do? Who uses it?
2. What is the tech stack? (languages, frameworks, databases, cloud services)
3. How is the repository organized? Explain each top-level folder.
4. What are the main services/components?
5. How do I build and run it locally?
Create a Mermaid architecture diagram showing all components and how they interact.
```

### The "I'm New Here" Prompt
```
@workspace I'm a new developer joining this project today. Give me a survival guide:
1. The 10 most important files I should read first (and why)
2. The 5 most important classes/modules to understand
3. Common terminology or domain concepts used in the code
4. Known gotchas or tricky parts of the codebase
5. How to run tests and what test framework is used
```

### The "Architecture Decision Records" Prompt
```
@workspace What major architectural decisions were made in this project?
Look at the tech choices, patterns, and project structure to infer:
1. Why was [FRAMEWORK] chosen?
2. Why is the code structured this way?
3. What trade-offs were made?
4. Are there any ADR (Architecture Decision Record) documents?
```

---

## 🔍 Module & File Analysis Prompts

### Understand a Specific File
```
Explain #file:[PATH_TO_FILE] in detail:
1. What is its responsibility?
2. What are the key functions/methods and what do they do?
3. What does it depend on? What depends on it?
4. Are there any complex algorithms or non-obvious logic?
5. What would break if I changed this file?
```

### Understand a Folder/Module
```
@workspace Analyze the [FOLDER_PATH] directory:
1. What is this module's single responsibility?
2. List all files with a one-line description of each
3. What is the public API of this module?
4. Draw a Mermaid class diagram of the key types
5. What design patterns does it use?
```

### Understand a Class or Interface
```
@workspace Explain the [CLASS_NAME] class:
1. What is its purpose and responsibility?
2. What are its properties/fields?
3. What are its methods and what does each do?
4. What interfaces does it implement?
5. How is it instantiated? (DI, factory, direct)
6. Show me all places in the codebase that use this class.
```

---

## 🔄 Flow Tracing Prompts

### Trace an API Endpoint
```
@workspace Trace the complete flow of [HTTP_METHOD] [ENDPOINT_PATH]:
1. Which controller/handler receives the request?
2. What middleware runs before it?
3. How is the input validated?
4. What service methods are called?
5. What database queries execute?
6. What is returned to the caller?
7. What happens on error?
Create a Mermaid sequence diagram.
```

### Trace a Background Job / Event
```
@workspace Trace the flow of the [JOB_OR_EVENT_NAME]:
1. What triggers this job/event?
2. What handler processes it?
3. What does it do step by step?
4. How is failure handled? Is there retry logic?
5. What data does it read/write?
Create a Mermaid sequence diagram.
```

### "Follow the Data" Prompt
```
@workspace Trace how [DATA_ENTITY] data flows through the system:
1. Where is it created? (API endpoint, background job, migration)
2. Where is it stored? (database table, cache, file)
3. Where is it read? (which services query it)
4. Where is it updated or deleted?
5. Is it published to other systems? (events, webhooks, APIs)
Create a Mermaid data flow diagram.
```

---

## 🧪 Testing & Quality Prompts

### Understand the Test Strategy
```
@workspace Analyze the testing approach in this project:
1. What test frameworks are used?
2. What types of tests exist? (unit, integration, e2e, performance)
3. How are tests organized? (file naming, folder structure)
4. How do I run all tests? Run a single test?
5. What is the test coverage? Are there coverage thresholds?
6. Are there test utilities, fixtures, or factories?
7. What mocking/stubbing approach is used?
```

### Generate Tests for a Module
```
@workspace Generate comprehensive tests for [FILE_OR_CLASS]:
1. Test all public methods
2. Include happy path and error cases
3. Test edge cases (null input, empty arrays, boundary values)
4. Use the same testing patterns and utilities already in this project
5. Mock external dependencies consistently with existing tests
```

---

## 🔧 Configuration & DevOps Prompts

### Understand Configuration
```
@workspace Map all configuration in this project:
1. What config files exist and what does each control?
2. What environment variables are required?
3. How does config differ across environments?
4. Where are secrets stored and how are they accessed?
5. What happens if a config value is missing?
```

### Understand CI/CD
```
@workspace Explain the CI/CD pipeline:
1. What triggers a pipeline run? (PR, merge, schedule)
2. What stages/steps does the pipeline have?
3. What quality gates must pass? (tests, coverage, scans)
4. How is deployment done? (manual, automatic, canary)
5. How do I debug a failed pipeline?
Create a Mermaid flowchart of the pipeline.
```

---

## 🗃️ Database & Data Prompts

### Understand the Data Model
```
@workspace Analyze the database schema:
1. List all tables/collections with their purpose
2. Show columns/fields, types, and constraints for each
3. Map all relationships (foreign keys, references)
4. What indexes exist and why?
5. How are migrations managed?
Create a Mermaid ER diagram.
```

### Understand a Specific Query
```
@workspace Explain what this query does and why:
[PASTE QUERY OR REFERENCE FILE:LINE]
1. What tables does it touch?
2. What is the expected result?
3. Is it performant? Any N+1 or full scan issues?
4. When is this query executed in the application flow?
```

---

## 🛡️ Security & Auth Prompts

### Understand Authentication
```
@workspace How does authentication work in this project?
1. What auth mechanism is used? (JWT, OAuth, session, API key)
2. Where is the auth middleware/filter defined?
3. How are tokens generated and validated?
4. Where are user credentials stored and how are they hashed?
5. How does token refresh work?
6. Which endpoints are public vs protected?
Create a Mermaid sequence diagram for the auth flow.
```

---

## 🐛 Debugging & Troubleshooting Prompts

### Understand an Error
```
@workspace I'm getting this error: [PASTE ERROR MESSAGE]
1. What file/function is the error coming from?
2. What causes this error?
3. What is the fix?
4. Are there similar issues elsewhere in the codebase?
```

### Understand a Performance Issue
```
@workspace Help me analyze potential performance issues:
1. Are there N+1 query patterns?
2. Are there missing database indexes?
3. Are there expensive operations in hot paths?
4. Is caching used effectively?
5. Are there synchronous calls that should be async?
```

---

## 💡 Pro Tips for Better Prompts

| Tip | Example |
|-----|---------|
| **Be specific** | ❌ "Explain auth" → ✅ "Explain JWT token validation in src/middleware/auth.ts" |
| **Reference files** | Use `#file:path/to/file` to give Copilot exact context |
| **Ask for diagrams** | Always add "Create a Mermaid diagram" at the end |
| **Chain prompts** | Start broad, then zoom in: Project → Module → File → Function |
| **Ask "why"** | "Why was this designed this way?" reveals more than "What does this do?" |
| **Compare** | "How does [Module A] differ from [Module B]?" |
| **Ask for examples** | "Show me an example of how [pattern] is used in this project" |

---

*Next → [6-OUTPUT-TEMPLATES.md](6-OUTPUT-TEMPLATES.md)*
