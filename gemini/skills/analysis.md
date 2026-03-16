# Skill: Analysis

## When to Use This Skill

Use this skill for tasks with `type: analysis`. Analysis tasks involve examining data, code, results, or situations to extract patterns, evaluate performance, and produce actionable insights.

## Analysis Process

### Step 1 — Define What to Analyze
- What is the object of analysis? (code, results, market, workflow)
- What decisions will this analysis inform?
- What is the time horizon? (immediate fix vs. long-term strategy)

### Step 2 — Gather Input Data
- Collect all relevant files from `/results/`, `/context/`, and `/tasks/`
- Note what data is available vs. missing
- Identify any assumptions you're making due to missing data

### Step 3 — Apply Analytical Framework

Choose the right lens:

| Analysis Type | Framework | When to Use |
|---|---|---|
| Product/Feature | Jobs-to-be-Done | Understanding user needs |
| Competitive | SWOT or 2x2 Matrix | Positioning decisions |
| Technical Debt | Complexity vs. Frequency | Refactoring priorities |
| Growth | Funnel Analysis | User acquisition/conversion |
| Task Performance | Completion Rate + Quality | Agent improvement |

### Step 4 — Structure the Output
Save results at `results/{task_name}.md`:

```markdown
# Analysis: {title}

**Date:** {YYYY-MM-DD}
**Task:** {task_filename}
**Framework Used:** {framework name}

## Key Findings

1. **{Finding 1}:** ...
2. **{Finding 2}:** ...
3. **{Finding 3}:** ...

## Supporting Evidence

### {Evidence Point 1}
...

### {Evidence Point 2}
...

## Visualizations (Text-Based)

```
Metric A: ████████░░ 80%
Metric B: █████░░░░░ 50%
```

## Recommendations

| Priority | Action | Expected Impact |
|---|---|---|
| High | ... | ... |
| Medium | ... | ... |

## Assumptions & Limitations
- ...

## Next Analysis Needed
- ...
```

### Step 5 — Update Learnings
Append key analytical insights and any patterns discovered to `/context/memory/learnings.md`.

## Quality Checklist

- [ ] Analysis framework is appropriate for the question
- [ ] Findings are numbered and clearly stated
- [ ] Evidence section supports findings
- [ ] Recommendations are prioritized
- [ ] Assumptions are documented
- [ ] Result file saved to `results/{task_name}.md`
- [ ] Task file status updated to `completed`
- [ ] Learnings appended to `context/memory/learnings.md`
