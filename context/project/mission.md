# autoCode — Mission & Project Context

## What is autoCode?

**autoCode** is a fully autonomous AI-powered development and operations system that runs, builds, and improves software projects 24/7 with little to no ongoing human involvement. It is powered by Google Gemini and operates entirely through GitHub Actions workflows.

Inspired by [Polsia](../../Polsia.md), autoCode acts as an AI co-founder for any project — handling planning, engineering, marketing research, competitive analysis, documentation, and continuous self-improvement. All orchestration happens via Markdown files: tasks are queued in `/tasks/`, executed by agents, and results land in `/results/`.

## Core Principles

1. **Everything in Markdown** — Tasks, results, agent definitions, and learnings are all `.md` files. Human-readable, Git-tracked, auditable.
2. **Tasks Drive Work** — Every workflow run picks the oldest pending task from `/tasks/`, executes it using specialized skills, and saves output to `/results/`.
3. **Context is King** — Agents always read this mission file + `/context/memory/learnings.md` before working, so every action is informed by prior decisions.
4. **Continuous Improvement** — After each task, agents append learnings back to `/context/memory/learnings.md`, building a collective memory (hive mind).
5. **Specialist Agents** — Different task types use different skills from `/gemini/skills/` for consistent, high-quality output.
6. **Autonomous Loop** — At the end of every workflow run, the Visionary step plans the next task and queues it automatically — the cycle never stops.

## Project Goal

Build a fully functional, self-improving open-source autonomous AI development platform that can:

- Analyze and understand an existing codebase
- Generate and execute a development roadmap
- Conduct marketing research and competitive analysis
- Create documentation, READMEs, and content
- Track its own progress through tasks and results
- Learn from each run and improve future performance

## Tech Stack

- **AI Model:** Google Gemini (via `gemini-2.0-flash-lite` by default, configurable)
- **Orchestration:** GitHub Actions (`.github/workflows/agent.yml`)
- **Task Management:** Markdown files in `/tasks/`
- **Results Storage:** Markdown files in `/results/`
- **Skills:** Instruction files in `/gemini/skills/`
- **Agent Definitions:** Markdown files in `/context/agents/`
- **Memory:** `/context/memory/learnings.md`

## Directory Layout

```
autoCode/
├── .github/workflows/agent.yml   ← Orchestration workflow (Gemini-powered)
├── context/
│   ├── project/mission.md        ← THIS FILE — project context & goals
│   ├── agents/                   ← Agent role definitions
│   └── memory/learnings.md       ← Shared hive-mind memory
├── gemini/skills/                ← Skill instructions per task type
├── tasks/                        ← Pending/completed task definitions
├── results/                      ← Task outputs & research findings
├── Polsia.md                     ← Architectural inspiration
└── README.md                     ← Public-facing documentation
```

## Autonomy Levels

- **Fully Automatic:** Workflow dispatched on schedule or issue trigger — no human needed.
- **Guided:** Humans can manually create task files in `/tasks/` to direct the agents.
- **Hybrid:** Reply to generated issues or edit `context/project/mission.md` to steer direction.
