# AI tooling strategy

This repository's day-to-day AI work centers on Claude Code, with other
harnesses (Codex CLI, GitHub Copilot, Gemini CLI, and similar tools)
available as fallbacks when Claude Code is unavailable. The
AI-instruction layout follows that harness mix — see "Canonical
guidance" below for which of those actually read `AGENTS.md`
directly versus needing an adapter.

## Canonical guidance

- [AGENTS.md](../AGENTS.md) is the canonical, fully detailed AI guide.
  It follows the [AGENTS.md](https://agents.md) convention —
  a vendor-neutral standard now stewarded by the Linux Foundation's Agentic
  AI Foundation — that a growing set of agent tools discover
  automatically at the repository root, OpenAI Codex and GitHub
  Copilot (CLI, coding agent, and Chat) confirmed among them. Check
  each tool's own documentation for its current level of support,
  since this keeps changing. Keep new guidance here first.
- [CLAUDE.md](../CLAUDE.md) and [GEMINI.md](../GEMINI.md) are thin adapters
  for the two tools that do not read `AGENTS.md` by default (Claude Code,
  and Gemini CLI unless a user has opted into `AGENTS.md` in their own
  settings). Each imports `AGENTS.md` via a standalone `@AGENTS.md`
  directive so its content loads automatically; they should stay a few
  lines and rarely need edits.
- [.github/copilot-instructions.md](../.github/copilot-instructions.md)
  is a thin GitHub Copilot adapter. Copilot already auto-discovers
  `AGENTS.md` directly, so this file only carries the small amount of
  guidance genuinely specific to Copilot's own UI, plus a pointer to the
  Scriban-template note that also lives in `.coderabbit.yaml`.

## Change policy

- `AGENTS.md` is the source of truth. Adapters exist only to get the
  content in front of tools that would otherwise miss it — do not
  duplicate guidance into them.
- When a rule needs tool-specific vocabulary (like Copilot's Agent mode /
  Plan mode), keep the neutral wording in `AGENTS.md` and put the
  vocabulary mapping in that tool's own adapter.

## Maintenance notes

- Treat this file as a human-facing strategy note, not as the primary
  instruction file for any agent.
- When updating AI guidance, review `AGENTS.md` first, then `CLAUDE.md`,
  `GEMINI.md`, `.github/copilot-instructions.md`, `README.md`, and the
  `.github/CONTRIBUTING*.md` family (which link directly into
  `AGENTS.md`'s section anchors) for anything that references it.

This layout was adopted directly from
[`kurone-kito/pnpm-project-template`](https://github.com/kurone-kito/pnpm-project-template)
when this repository's Node.js toolchain was introduced, rather than
evolving from an earlier Copilot-only setup in this repository.
