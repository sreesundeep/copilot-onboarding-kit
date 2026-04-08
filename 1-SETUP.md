# 🔧 1. Setup & Prerequisites

> Get your tools ready before diving into the codebase.

---

## ✅ Required Tools

| Tool | Purpose | Install |
|------|---------|---------|
| **VS Code** | Primary IDE | [Download](https://code.visualstudio.com/) |
| **GitHub Copilot Extension** | AI code assistant | VS Code Marketplace → "GitHub Copilot" |
| **GitHub Copilot Chat Extension** | Conversational AI for code Q&A | VS Code Marketplace → "GitHub Copilot Chat" |
| **Mermaid Preview Extension** | Render diagrams in markdown | VS Code Marketplace → "Markdown Preview Mermaid" |
| **Git** | Version control | `winget install Git.Git` |

## 🧩 Recommended VS Code Extensions for Exploration

| Extension | Why |
|-----------|-----|
| **GitLens** | Blame, history, who changed what and why |
| **Todo Tree** | Find TODOs/FIXMEs across the codebase |
| **Error Lens** | Inline error/warning highlights |
| **Project Manager** | Quick-switch between repos |
| **Markdown Preview Enhanced** | Better Mermaid + diagram rendering |

---

## 🚀 First Steps After Cloning

```bash
# 1. Clone the repo
git clone <REPO_URL>
cd <REPO_NAME>

# 2. Open in VS Code
code .

# 3. Check for setup docs
#    Look for any of these files:
#    README.md, CONTRIBUTING.md, docs/setup.md, Makefile, docker-compose.yml

# 4. Install dependencies (language-specific)
#    Node.js:   npm install / yarn install
#    Python:    pip install -r requirements.txt
#    .NET:      dotnet restore
#    Java:      mvn install / gradle build
#    Go:        go mod download

# 5. Try to build and run
#    Look at package.json scripts, Makefile targets, or CI pipeline YAML
```

---

## 🤖 Verify Copilot is Working

1. Open any source file in VS Code
2. Press `Ctrl+I` (Inline Chat) and type: `Explain this file`
3. Open Copilot Chat panel (`Ctrl+Shift+I`) and type: `@workspace What is this project about?`

If both respond meaningfully, you're ready for Day 1!

---

## 💡 Key Copilot Chat Participants to Know

| Participant | What It Does | Example |
|-------------|-------------|---------|
| `@workspace` | Searches entire repo for context | `@workspace How is authentication handled?` |
| `@terminal` | Helps with terminal commands | `@terminal How do I build this project?` |
| `@vscode` | VS Code settings & features | `@vscode How do I debug this project?` |
| `#file` | Reference a specific file | `Explain #file:src/auth/login.ts` |
| `#selection` | Reference selected code | Select code → `Explain #selection` |
| `#codebase` | Broader codebase context | `#codebase Where is the user model defined?` |

---

*Next → [2-HIGH-LEVEL-DISCOVERY.md](2-HIGH-LEVEL-DISCOVERY.md)*
