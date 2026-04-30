# Project

[Bootstrapped from the questionnaire — describes what this project is.]

## Session Start

Read silently before doing anything:
- `core/user-identity.md` — who the user is, how to work with them
- `core/project-brief.md` — what this project does
- `core/tone-of-voice.md` — how the project sounds
- `brain/decisions.md` — standing decisions

If those files don't exist yet, the project hasn't been bootstrapped. Ask the user if they want to run `/bootstrap`.

## How Work Happens

You orchestrate. Subagents in `.claude/agents/` execute:
- **designer** — creative direction, tone, brand
- **writer** — all user-facing copy
- **gatekeeper** — last-line quality review
- **developer** — code (frontend, scripts, apps, automations)

(Plus any specialists added during bootstrap.)

Each subagent has its own persistent memory at `.claude/agent-memory/<name>/MEMORY.md`. Auto-loaded at agent start; agents update it themselves after meaningful work.

When the user asks for something, dispatch the right agent (auto-routing handles most cases) or do it yourself for quick structural tasks.

When a task warrants closing the project-level loop (decisions, public-facing artifacts, structural changes), invoke `/memory-loop` — it handles `brain/decisions.md` and project-level artifact updates.

## Folder Structure

```
.claude/
  agents/             # subagent definitions (YAML frontmatter)
  agent-memory/       # per-agent persistent memory
  skills/             # workflow-encoded skills
core/                 # project identity (bootstrapped from the questionnaire)
brain/
  decisions.md        # standing decisions log
  artifacts/          # specs, plans, research
  reference-docs/     # uploaded docs (incl. brand-materials/)
  agent-template.md   # template for adding new agents
output/               # deliverables
resources/
  prompts/            # ready-made prompt templates
```

No new folders. Flat file naming. If you think a new folder is needed, ask first.
