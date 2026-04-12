# xiaocao-clone

`xiaocao-clone` is a Codex/Claude-style skill that clones Xiao Cao's engineering workflow, coding habits, tool preferences, and long-term distillation rules.

This project is not just a personality prompt. It is a documentation-first engineering skill for:

- writing code
- continuing existing projects
- embedded development
- website and backend work
- admin systems
- mini-program work
- UI implementation
- bug fixing
- refactoring
- deployment and operations

## What This Skill Does

The skill tries to act like Xiao Cao's enhanced engineering clone.

Core behavior:

- back up first when practical
- read the whole project first
- write a project-understanding document
- discuss architecture, functionality, interfaces, database, and return values
- write a spec before coding
- implement one feature at a time
- test one feature at a time
- write markdown delivery docs for each feature
- back up after stable feature acceptance
- stop blind debugging after repeated failure and switch to official docs and primary sources

## Key Personality And Workflow Traits

- prefers discussion before action
- does not like endless questioning once enough context exists
- dislikes coding without planning
- dislikes changing code before understanding the project
- dislikes hallucination
- prefers clear structure and explicit module boundaries
- avoids over-engineering and unnecessary abstraction
- treats MCP-assisted workflows as normal, especially for UI, browser automation, and research

## Included Files

- `SKILL.md`
  Top-level skill entry, trigger description, hard rules, and reference routing
- `agents/openai.yaml`
  UI-facing metadata
- `references/persona.md`
  Xiao Cao's personality, tone, and mode differences
- `references/workflow.md`
  Core engineering process and delivery rules
- `references/distillation.md`
  Candidate-memory and long-term confirmation flow
- `references/anti-patterns.md`
  Behaviors the clone should avoid
- `references/tools.md`
  Core tools, models, embedded tools, and UI workflow preferences
- `references/mcp-ecosystem.md`
  Verified Codex and Claude MCP environment profile
- `references/plugins.md`
  Verified Claude plugin environment profile
- `references/platform-adapters.md`
  Claude Code and Codex adaptation notes
- `assets/spec-template.md`
  Reusable "spec before code" template

## Install

Copy this project into your Codex skills directory:

```powershell
Copy-Item -Path .\xiaocao-clone -Destination "$HOME\\.codex\\skills" -Recurse
```

Or clone the repo directly into your skills folder.

For this repository layout, the repo root itself is the skill folder. If you clone it elsewhere, copy the repository contents into:

```text
~/.codex/skills/xiaocao-clone
```

## Validation

If you already have the Codex `skill-creator` system skill installed, validate with:

```powershell
python "$HOME\\.codex\\skills\\.system\\skill-creator\\scripts\\quick_validate.py" "<path-to-xiaocao-clone>"
```

## Trigger Examples

These are the kinds of prompts this skill is designed to match:

- "Write this feature in Xiao Cao's style."
- "Help me continue this project, but understand it first."
- "Fix this bug, check logs and configs first."
- "Write embedded code and give me the spec before implementation."
- "Build this backend API with database and return values planned first."
- "Design this UI with Figma MCP, then implement it."

## Working Style

The skill supports two modes:

- `enhanced`
  Default mode. More stable, more proactive, still keeps Xiao Cao's method.
- `authentic`
  More personal tone and stronger slang when the user explicitly wants the real vibe.

## Testing Preference

- For websites: prefer `Playwright MCP`
- For UI tasks: often prefer `Figma MCP`
- For mini-program or app tasks: tell the user to run tests in official developer tools

Important test focus:

- interface testing
- feature testing
- permission testing
- database read/write testing
- exception testing
- bug finding
- post-deployment testing

## License

No license has been added yet. Add one before broad public reuse if you want explicit open-source permissions.
