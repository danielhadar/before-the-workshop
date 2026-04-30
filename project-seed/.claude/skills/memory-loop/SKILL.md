---
name: memory-loop
description: Use after completing significant project-level work — decisions, public-facing artifacts, structural changes. Closes the project-level loop by updating `brain/decisions.md` and other shared files. Per-agent memory is the agent's own responsibility, not this skill's.
---

# Memory Loop (Project-Level)

After significant work, before moving on — check if anything project-wide needs to be remembered. Decisions that affect future work are worth recording; routine task completions are not.

Each agent (`.claude/agents/<name>.md`) handles its own `MEMORY.md` updates inline. This skill is only for project-level shared knowledge.

## Checklist

- **Noteworthy decision?** → Check `brain/decisions.md` first. If already there, skip. Otherwise, add a dated entry.
- **Project scope/goals changed?** → Update `core/project-brief.md` (rare).
- **User preferences changed?** → Update `core/user-identity.md` (rare).
- **Brand voice evolved?** → Update `core/tone-of-voice.md` (rare).
- **Produced something reusable?** → Would another agent or a future conversation benefit from having this as a standalone file? If yes, save in `brain/artifacts/`.

If nothing changed — skip. Don't force it.

## Decision Entry Format

Include a date heading. Group related decisions under one date.

```markdown
## YYYY-MM-DD — [Title]

### [What changed]
[1-3 sentences: what was decided, why, what was rejected.]
```
