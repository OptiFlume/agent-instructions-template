# One AGENTS.md for Codex, Cursor and Claude Code

A template repository: one `AGENTS.md` holds the rules every AI coding tool should follow, a one-line
`CLAUDE.md` imports it for Claude Code, and a small Cursor rule carries only what is Cursor-specific.
Codex and Cursor read `AGENTS.md` directly; Claude Code reads it through the `@AGENTS.md` import
(and, since v2.1.277, can read `AGENTS.md` itself). The reasoning, what each vendor's docs say and
the trade-offs are in the guide:
**[AGENTS.md vs CLAUDE.md vs Cursor rules](https://optiflume.ai/learn/agents-md-vs-claude-md-vs-cursor-rules)**.

## Use it

1. Click **Use this template** → create your repository, or copy the four files into an existing one.
2. Edit `AGENTS.md`: replace the stack line and every command with yours. A stale command is worse
   than none; the agent will run it.
3. Keep `CLAUDE.md` as the one-line import plus anything only Claude Code needs.
4. Edit or delete `.cursor/rules/project.mdc`; keep it only for Cursor-specific conventions.
5. `CLAUDE.local.md` is in `.gitignore` for personal notes that should not be shared.

## Files

| File | Read by | What goes in it |
| :--- | :--- | :--- |
| `AGENTS.md` | Codex, Cursor, Claude Code (via the import) | Stack, commands, style, what not to touch, commit rules, what to ask before doing |
| `CLAUDE.md` | Claude Code | `@AGENTS.md`, then Claude Code-only notes |
| `.cursor/rules/project.mdc` | Cursor | Cursor-only conventions; `alwaysApply: true` |
| `.gitignore` | | `CLAUDE.local.md` |

## What an instructions file cannot do

It is a request, not a guardrail: a model can ignore it, and a long session can compact it away.
Anything that must hold (no reading `.env`, no force push, no deleting files that existed before
the session) belongs in the tool's permissions or hooks, or in a tool that checks every call.
The guide covers the layers: [Guardrails for AI coding agents](https://optiflume.ai/learn/ai-coding-guardrails).

MIT licence. Maintained by [OptiFlume](https://optiflume.ai); issues and suggestions in
[optiflume/feedback](https://github.com/optiflume/feedback).
