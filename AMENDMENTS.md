# Amendments

Every change to the rules or the skills, newest first. Each entry says what changed and why.

An entry is added when something went wrong, when a step turned out to be dead weight, or when using the process showed a better way. See "How to amend" in [`CONSTITUTION.md`](CONSTITUTION.md).

---

## 002 · 2026-11-23 · Written once, for any agent

**Changed:** All content is written once in an open format (`SKILL.md` for skills, plain Markdown for rules). Anything tool-specific is a thin file in `adapters/` that points back to the original.

**Why:** The first draft assumed one tool. A process that only works in one vendor's product is a habit, not a process.

**Touches:** repo layout, `AGENTS.md`.

## 001 · 2026-11-23 · `kickoff` became `fuzzy-clear`

**Changed:** The first skill was renamed from `kickoff` to `fuzzy-clear`. The list of unknowns became the "fuzz list" and the readiness checklist became the "clear check". A brief's status now starts at `fuzzy` and moves to `clear`.

**Why:** The name should say what goes in and what comes out. It also works as a verb, which makes it more likely to get used.

**Touches:** `skills/fuzzy-clear/SKILL.md`.
