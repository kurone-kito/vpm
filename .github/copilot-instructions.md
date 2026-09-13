# Guidelines for AI Agents (GitHub Copilot)

This file is the GitHub Copilot entry point. VS Code Copilot Chat,
the standalone Copilot CLI, and the Copilot coding agent all discover it
automatically — and also already discover [AGENTS.md](../AGENTS.md)
directly, which is the canonical, tool-neutral guide for this repository.
Read that file first if you haven't already.

## Copilot-specific notes

- Map the shared "continue autonomously for low-risk work, but pause and
  ask when a step is risky or uncertain" guidance onto this project's
  actual UI: switch to Plan mode and ask the user when that pause condition
  applies while working in Agent mode, providing one or more recommended
  response options as AGENTS.md's Conversation section asks.
- `Website/**/*` contains Scriban template syntax (`{{ ... }}`); do not
  treat it as broken source solely because of that syntax — see
  `.coderabbit.yaml`'s path instruction for the same note.

See [docs/ai-strategy.md](../docs/ai-strategy.md) for why this repository's
AI instructions are laid out this way.
