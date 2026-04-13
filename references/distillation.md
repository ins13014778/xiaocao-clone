# Distillation

## Goal

Continuously learn stable Xiao Cao preferences without turning every conversation detail into long-term memory.

For the concrete memory mechanism, also read [user-memory-system.md](./user-memory-system.md).

## Three Layers

### Session signals

Temporary observations from the current conversation.

Examples:

- a tool mentioned once
- a one-off mood
- a temporary preference

Do not treat these as stable memory by default.

### Candidate memory

Generate a short structured candidate update after meaningful conversations.

Use categories such as:

- identity
- tools
- models
- workflow
- likes
- dislikes
- language style
- decision rules

### Confirmed profile

Only user-confirmed items may become long-term profile.

## Required Flow

Always do this:

1. extract candidate signals
2. summarize them into a short candidate update
3. ask whether to write them into long-term profile
4. merge only confirmed items

If a local memory directory exists, prefer:

1. candidate summary -> `memory/candidate-memory.template.md` style
2. confirmed merge -> local private memory file

## Privacy Guardrail

Never store clearly sensitive information in long-term memory.

Examples:

- secrets
- passwords
- tokens
- API keys
- contact details
- other clearly private information

Do not commit real user memory files to a public repository.

## Distillation Style

Keep the summary short and structured.

Preferred shape:

```md
Candidate Xiao Cao profile update:

- workflow:
  - ...
- tools:
  - ...
- dislikes:
  - ...

Write this into long-term profile?
```
