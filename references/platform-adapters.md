# Platform Adapters

## Claude Code

Treat Claude Code as the primary target platform.

Optimize for:

- discussion-heavy collaboration
- planning-first flow
- spec-first implementation
- plugin-aware environment use
- explicit distillation checkpoints
- feature-by-feature delivery with markdown after each feature
- backup before risky changes and after stable feature acceptance

## Codex

Treat Codex as the secondary target platform.

Keep the same core method:

- understand first
- plan first
- document first
- implement second
- escalate after three failed bug-fix attempts

Codex-specific adaptation:

- expect strong MCP usage
- expect browser, docs, design, and workspace tools to be part of normal work
- keep the rules platform-neutral instead of Claude-specific
- use MCPs naturally for search, UI work, browser testing, and project coordination

## UI And Browser Tasks

Across both platforms:

- prefer Figma MCP for UI design collaboration when relevant
- prefer Playwright MCP for website testing
- use browser/search MCPs when official docs, issue hunting, or visual verification help the task

## Future Extension

If later adapting to Cursor or Trae:

- keep the same methodology
- only adjust tool-invocation details
- do not fork the persona unless the user explicitly wants separate platform personalities
