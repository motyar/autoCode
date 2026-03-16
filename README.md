# autoCode 🤖

> **An autonomous AI development system that runs, builds, and improves your project 24/7 — powered by Google Gemini and GitHub Actions.**

[![GitHub Actions](https://img.shields.io/github/actions/workflow/status/motyar/autoCode/agent.yml?label=agent&style=flat-square)](https://github.com/motyar/autoCode/actions)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square)](LICENSE)

---

## What It Does

autoCode is an autonomous agent loop that operates entirely within GitHub Actions. Every workflow run:

- 📋 **Picks the next pending task** from `/tasks/`
- 🧠 **Loads project context** from `/context/project/mission.md` and memory
- 🤖 **Executes the task** using specialized AI skills (research, engineering, marketing, analysis)
- 💾 **Saves results** to `/results/`
- 🔄 **Queues the next task** automatically via the Visionary step

No servers. No infra. Just GitHub Actions + Gemini.

---

## How It Works

```
Every Workflow Run:
┌─────────────────────────────────────────────────────────┐
│  1. Find oldest pending task in /tasks/                 │
│  2. Load context (mission + memory + relevant skill)    │
│  3. Gemini executes the task, saves to /results/        │
│  4. Create PR with results + updated task status        │
│  5. Visionary: plan + queue the next task               │
└─────────────────────────────────────────────────────────┘
```

### Directory Layout

```
autoCode/
├── .github/workflows/agent.yml   ← The orchestration engine
├── context/
│   ├── project/mission.md        ← Project identity & goals (edit this!)
│   ├── agents/                   ← Agent role definitions (CEO, Engineering, Marketing, Research)
│   └── memory/learnings.md       ← Collective hive mind — grows with every task
├── gemini/skills/                ← How-to guides per task type
│   ├── research.md
│   ├── engineering.md
│   ├── marketing.md
│   └── analysis.md
├── tasks/                        ← Work queue (pending → completed)
├── results/                      ← All agent outputs land here
├── Polsia.md                     ← Architectural inspiration
└── README.md                     ← This file
```

---

## Quick Start

### 1. Fork the Repository

```bash
# Fork via GitHub UI or:
gh repo fork motyar/autoCode --clone
```

### 2. Add Your Gemini API Key

In your forked repo: **Settings → Secrets and variables → Actions → New repository secret**

```
Name:  GEMINI_API_KEY
Value: your-gemini-api-key-here
```

Get a free key at [aistudio.google.com](https://aistudio.google.com).

### 3. Customize Your Project Mission

Edit `context/project/mission.md` to describe **your** project. This is what every agent reads before working. Be specific about:
- What you're building
- Who it's for
- What success looks like

### 4. Create Your First Task

Add a file to `/tasks/task_001_your_task.md`:

```markdown
# Task: Your Task Title

**Status:** pending
**Type:** research
**Priority:** high
**Created:** 2026-01-01

## Description
Describe what needs to be done...

## Expected Output
What should be produced and where it should be saved...

## Instructions
1. Step-by-step instructions...
2. Save results to results/task_001_your_task.md
3. Update this file: change "status: pending" to "status: completed"
```

### 5. Trigger the Workflow

Go to **Actions → Gemini Agent → Run workflow**. The agent will:
1. Find your task
2. Execute it using Gemini
3. Open a PR with the results

---

## Task File Format

```markdown
# Task: {Title}

**Status:** pending          ← Required: pending | completed
**Type:** research           ← Required: research | engineering | marketing | analysis
**Priority:** high           ← high | medium | low
**Created:** 2026-01-01      ← ISO date

## Description
What needs to be done and why.

## Expected Output
What file(s) should be created and where.

## Instructions
1. Numbered steps for the agent to follow.
2. Always include: save results to results/{task_name}.md
3. Always include: update this file status to "completed"
```

**Naming convention:** `task_{NNN}_{short_slug}.md` (e.g., `task_001_create_readme.md`)

---

## Available Skills

Agents automatically use the skill matching their task type:

| Skill | File | Used For |
|-------|------|----------|
| 🔍 Research | `gemini/skills/research.md` | Competitive analysis, trend research, information gathering |
| ⚙️ Engineering | `gemini/skills/engineering.md` | Code, configuration, documentation |
| 📣 Marketing | `gemini/skills/marketing.md` | Copy, content strategy, growth tactics |
| 📊 Analysis | `gemini/skills/analysis.md` | Data analysis, performance review, architecture review |

---

## Agents

| Agent | File | Role |
|-------|------|------|
| 🎯 CEO | `context/agents/ceo.md` | Strategy, prioritization, run summaries |
| ⚙️ Engineering | `context/agents/engineering.md` | Code and technical work |
| 📣 Marketing | `context/agents/marketing.md` | Content and growth |
| 🔍 Research | `context/agents/research.md` | Intelligence and analysis |

---

## The Autonomous Loop

The system is self-sustaining:

1. **Executes** the current task → saves result to `/results/`
2. **Visionary step** analyzes the project and plans the next task
3. **Creates** a new task file in `/tasks/` and pushes it
4. **Next run** picks it up automatically

As long as the workflow runs (via schedule, dispatch, or issue trigger), the system never stops improving.

---

## Configuration

All configuration is in `.github/workflows/agent.yml`:

```yaml
env:
  GEMINI_MODEL: gemini-2.0-flash-lite   # Model to use
  GEMINI_CLI_VERSION: "0.1.21"          # CLI version (do not change)
```

To add a scheduled run, add to the `on:` block:
```yaml
on:
  schedule:
    - cron: '0 6 * * *'   # Every day at 6am UTC
  workflow_dispatch:
```

---

## Steer the System

You are the "passive investor" — you can steer without managing:

| Action | Effect |
|--------|--------|
| Edit `context/project/mission.md` | Changes the project's direction |
| Create a file in `tasks/` | Queues specific work |
| Edit `context/memory/learnings.md` | Gives agents direct guidance |
| Open a GitHub Issue | Triggers issue-fix workflow (fallback) |

---

## Contributing

1. Fork the repo
2. Create a task in `/tasks/` describing your improvement
3. Let the agent implement it 😄
4. Or implement it yourself and open a PR

---

## Architecture Inspiration

This system is inspired by [Polsia](Polsia.md) — an autonomous AI platform that runs entire businesses. autoCode adapts those principles for open-source software development on GitHub.

---

## License

MIT — see [LICENSE](LICENSE) for details.

---

*Built autonomously. Improved continuously.*
