# Auto Code Buddy — Self-Evolving Knowledge System

A meta-skill for AI coding assistants that builds a personalized knowledge base from your coding sessions. Instead of starting fresh every conversation, Auto Code Buddy automatically retrieves past experiences, captures successful solutions, and gets smarter over time.

Inspired by [Toolsai/auto-skill](https://github.com/Toolsai/auto-skill), adapted for OpenCode in English.

---

## Core Highlights

### 1. Truly "Gets Better With Use"
Traditional AI conversations reset to zero when they end. Auto Code Buddy runs a Core Loop every turn — automatically checking keyword indexes and invoking past "best solutions" or "pitfall guides" when it recognizes a previously solved problem.

### 2. Cross-Skill Experience Layer
When you invoke other skills (e.g., coding, design, deployment), Auto Code Buddy checks the experience library automatically.

For example: when you use a `docker-setup` skill, it might remind you: *"Last time we hit a port conflict — we resolved it by using `--network host`. Applying that approach now."*

### 3. Proactive Experience Capture
No manual note-taking required. When the AI detects a task is complete or you express satisfaction, it proactively asks:

> "We solved [problem] this time. I'd like to record this experience to your knowledge base so next time I can reference it directly. Would that be okay?"

### 4. Structured Knowledge Storage
Uses lightweight JSON indexes + Markdown content — human-readable and machine-parseable.

- **Knowledge Base** — General workflows, preferences, style rules, best practices
- **Skill Experience** — Skill-specific parameters, error solutions, proven techniques

---

## How It Works — The Core Loop

Auto Code Buddy executes a strict 5-step loop every conversation turn:

| Step | Name | What It Does |
|------|------|-------------|
| 1 | **Keyword Fingerprinting** | Extracts 3–8 core keywords from the current message |
| 2 | **Topic Switch Detection** | Detects when you change topics (≥40% keyword diff) |
| 3 | **Skill Experience Reading** | Loads past lessons when specific skills are invoked |
| 4 | **Knowledge Base Retrieval** | Matches keywords against indexed best practices |
| 5 | **Auto Recording** | Prompts to record successful solutions on task completion |

---

## File Structure

```
auto-code-buddy/
├── SKILL.md                    # Skill definition & core loop instructions
├── README.md                   # This file
├── experience/
│   ├── _index.json             # Skill experience index
│   └── skill-[skill-id].md    # Per-skill experience records (auto-created)
└── knowledge-base/
    ├── _index.json             # Knowledge base category index
    └── [category].md           # Per-category knowledge entries (auto-created)
```

---

## Pre-Configured Knowledge Categories

| Category | Keywords |
|----------|----------|
| **Frontend Development** | React, Vue, CSS, HTML, JavaScript, TypeScript, Next.js, Tailwind |
| **Backend Development** | API, database, server, Node.js, Python, Express, REST, GraphQL, SQL |
| **DevOps & Deployment** | Docker, CI/CD, deploy, pipeline, Kubernetes, AWS, cloud |
| **Coding Patterns** | pattern, architecture, refactor, clean code, SOLID, DRY, testing |
| **Workflow & Productivity** | efficiency, automation, workflow, project, git, IDE, debugging |

New categories are created dynamically when your tasks don't fit existing ones.

---

## What Gets Recorded

### Knowledge Base (General)

| Record | Don't Record |
|--------|-------------|
| Reusable workflows & decision steps | Single Q&A with no reusable process |
| High-cost errors & correction paths | Pure conceptual explanations |
| Critical parameters & prerequisites | Context-free conclusions |
| User preferences & style rules | |
| Multi-attempt solutions (with failure reasons) | |
| Reusable templates & checklists | |

### Skill Experience (Per-Skill)

| Record | Don't Record |
|--------|-------------|
| Pitfalls & solutions (with error messages) | Pure theory (keep in knowledge-base) |
| Key parameters affecting results | Conclusions without reproducible steps |
| Reusable templates & workflows | One-off, non-reusable operations |
| Dependency/asset paths | |
| Steps requiring specific sequence | |

---

## Entry Formats

### Knowledge Base Entry
```markdown
## [Short Title]
**Date:** 2026-02-14
**Situation:** One-sentence description of the use case
**Best Practices:**
- Key point 1
- Key point 2 — parameter notes and adjustment guidelines
```

### Skill Experience Entry
```markdown
## [Problem/Technique Title]
**Date:** 2026-02-14
**Skill:** docker-setup
**Situation:** One-sentence description of this issue
**Solution:**
- Specific step 1
- Specific step 2
**Key Files/Paths:**
- /path/to/relevant/file
**Keywords:** docker, port-conflict, networking
```

---

## Installation

### Using Skills CLI
```bash
npx skills add cytsaiap-xyz/auto-code-buddy
```

### Manual
Clone into your skills directory:
```bash
git clone https://github.com/cytsaiap-xyz/auto-code-buddy.git ~/.agents/skills/auto-code-buddy
```

---

## How It Self-Bootstraps

On first activation, Auto Code Buddy automatically:
1. Detects your IDE's global rules file
2. Appends a "Task Startup Protocol" rule ensuring it activates on every task
3. Notifies you that hardening is complete

This ensures the knowledge system is always active, even when other skills are triggered.

---

## License

MIT

---

## Credits

- Inspired by [Toolsai/auto-skill](https://github.com/Toolsai/auto-skill) by Prompt Case
- Adapted for OpenCode in English
