# xiaocao-clone Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build and install a first usable `xiaocao-clone` skill in the local Codex skills directory, based on the approved design spec and the user's verified tooling environment.

**Architecture:** Create one top-level skill with a concise `SKILL.md`, UI metadata in `agents/openai.yaml`, and focused reference files for persona, workflow, distillation, anti-patterns, tools, MCP ecosystem, plugins, and platform adapters. Keep the skill auto-discoverable in `C:\Users\Administrator\.codex\skills`, and validate it with the bundled skill validator.

**Tech Stack:** Markdown, YAML, Python init/validation scripts from the local `skill-creator` skill, Windows filesystem.

---

### Task 1: Create the plan and skill skeleton

**Files:**
- Create: `D:\xiaocao-sk\docs\superpowers\plans\2026-04-12-xiaocao-clone.md`
- Create: `C:\Users\Administrator\.codex\skills\xiaocao-clone\SKILL.md`
- Create: `C:\Users\Administrator\.codex\skills\xiaocao-clone\agents\openai.yaml`
- Create: `C:\Users\Administrator\.codex\skills\xiaocao-clone\references\`
- Create: `C:\Users\Administrator\.codex\skills\xiaocao-clone\assets\`

- [ ] **Step 1: Verify the target install path is available**

Run:

```powershell
Get-ChildItem 'C:\Users\Administrator\.codex\skills' | Select-Object Name
```

Expected: the directory exists and `xiaocao-clone` is not already present.

- [ ] **Step 2: Initialize the skill skeleton**

Run:

```powershell
python 'C:\Users\Administrator\.codex\skills\.system\skill-creator\scripts\init_skill.py' `
  xiaocao-clone `
  --path 'C:\Users\Administrator\.codex\skills' `
  --resources references,assets `
  --interface display_name='Xiaocao Clone' `
  --interface short_description='Clone Xiao Cao''s coding style, workflow, and distillation rules.' `
  --interface default_prompt='Use $xiaocao-clone to collaborate like Xiao Cao: understand first, plan first, write the spec, then implement.'
```

Expected: `C:\Users\Administrator\.codex\skills\xiaocao-clone\` is created with a starter `SKILL.md`, `agents/openai.yaml`, and resource folders.

- [ ] **Step 3: Check the generated file list**

Run:

```powershell
Get-ChildItem -Recurse 'C:\Users\Administrator\.codex\skills\xiaocao-clone' | Select-Object FullName
```

Expected: only the expected skeleton files and folders exist.

### Task 2: Write the top-level skill contract

**Files:**
- Modify: `C:\Users\Administrator\.codex\skills\xiaocao-clone\SKILL.md`
- Modify: `C:\Users\Administrator\.codex\skills\xiaocao-clone\agents\openai.yaml`

- [ ] **Step 1: Replace the template SKILL.md with the final top-level contract**

Write a `SKILL.md` that includes:

```md
---
name: xiaocao-clone
description: Clone Xiao Cao's collaboration style, coding workflow, and continuous distillation process. Use when the user wants AI to act like Xiao Cao, follow Xiao Cao's project process, distill stable user preferences, or work in a documentation-first style: understand the project, back up, discuss architecture and interfaces, write a spec, then implement.
---
```

The body must define:

- default `enhanced` mode
- optional `authentic` mode
- hard anti-patterns
- bug escalation after three failed fixes
- reference-file loading guidance

- [ ] **Step 2: Align `agents/openai.yaml` with the final skill**

Ensure the generated YAML contains:

```yaml
interface:
  display_name: "Xiaocao Clone"
  short_description: "Clone Xiao Cao's coding style, workflow, and distillation rules."
  default_prompt: "Use $xiaocao-clone to collaborate like Xiao Cao: understand first, plan first, write the spec, then implement."
```

Expected: UI metadata matches the actual skill behavior and naming.

### Task 3: Write the reference knowledge files

**Files:**
- Create: `C:\Users\Administrator\.codex\skills\xiaocao-clone\references\persona.md`
- Create: `C:\Users\Administrator\.codex\skills\xiaocao-clone\references\workflow.md`
- Create: `C:\Users\Administrator\.codex\skills\xiaocao-clone\references\distillation.md`
- Create: `C:\Users\Administrator\.codex\skills\xiaocao-clone\references\anti-patterns.md`
- Create: `C:\Users\Administrator\.codex\skills\xiaocao-clone\references\tools.md`
- Create: `C:\Users\Administrator\.codex\skills\xiaocao-clone\references\mcp-ecosystem.md`
- Create: `C:\Users\Administrator\.codex\skills\xiaocao-clone\references\plugins.md`
- Create: `C:\Users\Administrator\.codex\skills\xiaocao-clone\references\platform-adapters.md`
- Create: `C:\Users\Administrator\.codex\skills\xiaocao-clone\assets\spec-template.md`

- [ ] **Step 1: Write `persona.md`**

Include concrete facts:

```md
- Xiao Cao is a first-year university student.
- He is somewhat introverted in real life.
- He often collaborates with AI before acting.
- Authentic mode may use strong slang and joking nicknames naturally.
- Enhanced mode keeps his method but uses cleaner execution language.
```

- [ ] **Step 2: Write `workflow.md`**

Include the exact sequence:

```md
1. Read the whole project first.
2. Create a safe backup or rollback point.
3. Discuss architecture, functionality, interfaces, and rules.
4. Write the document/spec first.
5. Implement against the document.
6. Verify the result against the document.
```

- [ ] **Step 3: Write `distillation.md`**

Include:

```md
- session signals
- candidate memory
- confirmed profile
- privacy exclusion for sensitive data
- user confirmation before long-term persistence
```

- [ ] **Step 4: Write `anti-patterns.md`**

Include:

```md
- do not modify code before understanding the project
- do not skip planning
- do not hallucinate
- after three failed bug-fix attempts, stop and check official docs
```

- [ ] **Step 5: Write `tools.md`, `mcp-ecosystem.md`, and `plugins.md`**

Capture verified environment facts:

```md
- Codex core tools: Claude Code, Codex, Cursor, Trae, GitHub, ChatGPT
- Embedded tools: aily blockly, Arduino, DevEco Studio
- Codex MCP emphasis: figma, notion, linear, pencil, chrome-bridge, grok-search, playwright
- Claude MCP and plugin ecosystem: chrome-devtools, superpowers, codex plugin, code-review, feature-dev, frontend-design, skill-creator, plugin-dev, mcp-server-dev
```

- [ ] **Step 6: Write `platform-adapters.md` and `spec-template.md`**

Add concise guidance for:

- Claude Code first-class usage
- Codex secondary usage
- a reusable spec template with sections for goal, scope, interfaces, rules, risks, and verification

### Task 4: Validate the installed skill

**Files:**
- Test: `C:\Users\Administrator\.codex\skills\xiaocao-clone\`

- [ ] **Step 1: Run skill validation**

Run:

```powershell
python 'C:\Users\Administrator\.codex\skills\.system\skill-creator\scripts\quick_validate.py' 'C:\Users\Administrator\.codex\skills\xiaocao-clone'
```

Expected: validation passes with no YAML or naming errors.

- [ ] **Step 2: Inspect the top-level files one more time**

Run:

```powershell
Get-Content -Raw 'C:\Users\Administrator\.codex\skills\xiaocao-clone\SKILL.md'
Get-Content -Raw 'C:\Users\Administrator\.codex\skills\xiaocao-clone\agents\openai.yaml'
```

Expected: skill metadata and instructions match the approved spec.

- [ ] **Step 3: Report install location and validation result**

Report:

```text
Installed skill path: C:\Users\Administrator\.codex\skills\xiaocao-clone
Validation: PASS
```
