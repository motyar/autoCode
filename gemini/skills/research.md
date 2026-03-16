# Skill: Research

## When to Use This Skill

Use this skill for tasks with `type: research`. Research tasks involve gathering, analyzing, and synthesizing information about topics relevant to the project.

## Research Process

### Step 1 — Define the Research Question
Before doing anything, clearly state:
- What specific question needs answering?
- Who will use this information, and how?
- What does "done" look like?

### Step 2 — Gather Information
Draw from:
- Your training knowledge about the topic
- The existing files in this repository (especially `/context/`, `/results/`, and `Polsia.md`)
- Known public information about tools, trends, and competitors

### Step 3 — Analyze & Synthesize
- Identify patterns across sources
- Note contradictions and explain them
- Separate facts from opinions/estimates
- Rank findings by relevance to the project mission

### Step 4 — Structure the Output
Always produce a result file at `results/{task_name}.md` with:

```markdown
# Research: {topic}

**Date:** {YYYY-MM-DD}
**Task:** {task_filename}

## Executive Summary
- Key finding 1
- Key finding 2
- Key finding 3

## Detailed Findings

### {Section 1}
...

### {Section 2}
...

## Competitive Landscape (if applicable)

| Tool/Product | Strengths | Weaknesses | Relevance |
|---|---|---|---|
| ... | ... | ... | ... |

## Recommendations
1. ...
2. ...

## Follow-up Questions
- ...
```

### Step 5 — Update Learnings
Append 1-3 key takeaways to `/context/memory/learnings.md`:
```
- `{date}` | `research` | {concise learning}
```

## Quality Checklist

- [ ] Executive summary is 3-5 bullets, each actionable
- [ ] Findings are organized under clear headers
- [ ] Competitive table (if applicable) has at least 3 rows
- [ ] At least 2 concrete recommendations
- [ ] Result file saved to `results/{task_name}.md`
- [ ] Task file status updated to `completed`
- [ ] Learnings appended to `context/memory/learnings.md`
