# Skill: Engineering

## When to Use This Skill

Use this skill for tasks with `type: engineering`. Engineering tasks involve creating or modifying code, configuration files, documentation, or other technical artifacts.

## Engineering Process

### Step 1 — Understand Before Changing
- Read the relevant existing files first
- Understand the current architecture
- Identify the minimal change needed
- Check `/context/memory/learnings.md` for prior engineering decisions

### Step 2 — Plan the Change
- List every file that needs to be created or modified
- Identify dependencies and potential side effects
- Confirm the approach is consistent with existing patterns in the codebase

### Step 3 — Implement
- Make the smallest correct change
- Follow the existing code style (indentation, naming, structure)
- Add comments only where the logic is non-obvious
- Update documentation if behavior changes

### Step 4 — Validate
- Re-read the changed files to catch typos and logic errors
- Verify that referenced files, paths, and variables exist
- Confirm nothing breaks that was working before

### Step 5 — Document Results
Save a result file at `results/{task_name}.md`:

```markdown
# Engineering Task: {title}

**Date:** {YYYY-MM-DD}
**Task:** {task_filename}

## Summary
Brief description of what was done.

## Changes Made

| File | Change Type | Description |
|------|-------------|-------------|
| path/to/file.md | Created | ... |
| path/to/file.yml | Modified | ... |

## Technical Notes
Any important implementation details, limitations, or follow-up items.

## Testing
How to verify the changes work correctly.
```

### Step 6 — Update Learnings
Append key technical decisions to `/context/memory/learnings.md`.

## Quality Checklist

- [ ] Read existing code/files before modifying
- [ ] Changes are minimal and targeted
- [ ] Code follows existing style
- [ ] All file paths are valid
- [ ] Result file saved to `results/{task_name}.md`
- [ ] Task file status updated to `completed`
- [ ] Learnings appended to `context/memory/learnings.md`
