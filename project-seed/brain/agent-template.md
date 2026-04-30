# Agent Template

When adding a new agent, save as `.claude/agents/<name>.md` and use this structure:

```yaml
---
name: agent-name
description: One line of what this agent does + when to dispatch. Use proactively for X. Use immediately when Y.
color: blue
memory: project
skills:
  - relevant-skill-1
---

# [Role]

You are the [role]. [1-2 sentences about your scope and how you relate to other agents.]

## What You Do

[Bullet list. Specific. Actionable.]

## How You Work

1. Read the relevant files: `core/...`, `brain/...`, etc.
2. [Approach to the task.]
3. Use any relevant skills.
4. After meaningful work, update your MEMORY.md with patterns and corrections.

## What You Don't Do

[Clear boundaries — out of scope.]

## Rules

[Optional. Project-specific norms.]
```

## Frontmatter Fields

- `name` (required) — lowercase, hyphenated. Becomes the @-mention identifier and the matching folder under `.claude/agent-memory/`.
- `description` (required) — Claude uses this for auto-routing. Front-load with "Use proactively..." trigger phrases. Bad descriptions cause wrong-agent dispatch.
- `color` — visual identifier in the task list. One of: `red`, `blue`, `green`, `yellow`, `purple`, `orange`, `pink`, `cyan`.
- `memory: project` — gives the agent persistent memory at `.claude/agent-memory/<name>/MEMORY.md`. The first ~200 lines auto-load every invocation.
- `skills` — preload skills into the agent's startup context. Use only when always needed (preload uses context).

Omit `tools` and `model` — settings handle the first; `inherit` is the default for the second.

## After Creating an Agent File

Anthropic loads `.claude/agents/` at session start. **After adding the file, restart Claude Code or run `/agents` to refresh** — otherwise the agent won't be dispatchable until next session.

Also create a starter memory file at `.claude/agent-memory/<name>/MEMORY.md` so the agent has somewhere to write learnings from day one.

## Naming

Lowercase-hyphenated. The role IS the name: `writer`, `designer`, `gatekeeper`, `frontend-dev`, `developer`. No human names.

## Guidelines

- **Identity first.** The agent should know who it is before it knows what to do.
- **Second person.** Write as "You are the [role]..." — these are instructions to Claude about who to be.
- **Trigger phrases in `description`.** "Use proactively" / "Use immediately when" — these drive auto-dispatch.
- **Tight body.** Aim under ~50 lines. The body is loaded fresh each invocation.
- **Self-managed memory.** Each agent's body says "update your MEMORY.md after meaningful work" — agents handle their own learning.
