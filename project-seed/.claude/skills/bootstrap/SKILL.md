---
name: bootstrap
description: First-run setup. Reads the questionnaire and brand materials, generates core files, evaluates if a specialist agent is needed, and presents the team.
disable-model-invocation: true
---

# Bootstrap

## Setup Sequence

1. **Read inputs**
   - `brain/reference-docs/questionnaire.md` — the user's filled questionnaire.
   - `brain/reference-docs/brand-materials/` — any files the user placed here (writing samples, brand docs). May be empty.

2. **Generate core files**
   - `core/project-brief.md` — project scope, goals, audience, success criteria, constraints. Distill from the questionnaire into a clean brief.
   - `core/user-identity.md` — user's name, preferences, personality, operating principles.
   - `core/tone-of-voice.md` — the project's brand voice. If `brand-materials/` has files, read them all and extract tone, style, patterns, vocabulary. If empty, derive from the questionnaire.

3. **Evaluate specialist need**
   The seed already includes 4 agents in `.claude/agents/`: designer, writer, gatekeeper, developer. Based on the project type, decide if a specialist is a clear must-have. Be conservative — most projects work fine with the base team.
   - Max 2 specialists. Prefer 0 or 1.
   - Examples: a frontend specialist for design-heavy apps, a researcher for research-heavy projects, a social-media specialist for content creators, a financial-analyst for finance work.
   - If adding: use `brain/agent-template.md` as the structure. Create `.claude/agents/<name>.md` and a starter `.claude/agent-memory/<name>/MEMORY.md`.

4. **Present team summary**
   - Project summary — show you understood the questionnaire in 2-3 sentences.
   - Team roster: list each agent (the 4 base + any specialists) with one line on how they'll work for this specific project.
   - If you added a specialist: explain why, and tell the user to restart Claude Code (or run `/agents`) so the new agent is dispatchable.
   - Ask: "Anything you'd change before we start working?"

5. **Wait for a task**
   - Setup approval ("looks good", "no changes") is not a work request. Don't start building.
   - Ask: "Great. So what are we building first?"
