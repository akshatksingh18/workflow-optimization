# Coding Optimization — Setup

This is Akshat's research workspace for evaluating optional AI-coding workflow tools around
Claude Code and Codex on Windows 11. It records what a tool is for, whether it is worth trying,
and the condition that would justify adopting it.

**Status:** Research/evaluation — no optional workflow tool or model gateway is currently adopted.

## Files
- `.gitignore` — local editor, environment, log, temporary, and OS-generated file exclusions.
- `important-tools.md` — **current evaluation board.** Read it in full before making tooling
  recommendations or setup changes. It categorizes candidates by function, records overlaps and
  decision triggers, and replaces prior decisions in place rather than keeping research history.

## Working agreement
- Current baseline is Claude Code + Codex + the shared `CLAUDE.md` hierarchy. Do not describe a
  candidate as installed, configured, or adopted without confirming that state with Akshat or the
  actual environment.
- Add tooling only to solve an observed workflow problem. Trial one candidate per category on a
  bounded real task, define success before installing, and record only the current decision.
- Check privacy, token/cost impact, Windows 11 support, Claude/Codex compatibility, maintenance,
  overlap, and rollback before recommending adoption.
- Windows 11 is the primary OS. Where a tool assumes a Unix shell, note that WSL2 is the
  fallback, not the default.
- **Whenever a new file is added to this folder**, add a bullet for it under `## Files` above,
  in the same edit, with a one-line description of what it's for.
