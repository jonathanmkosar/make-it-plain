# Amendments

Every change to the rules or the skills, newest first. Each entry says what changed and why.

An entry is added when something went wrong, when a step turned out to be dead weight, or when using the process showed a better way. See "How to amend" in [`CONSTITUTION.md`](CONSTITUTION.md).

---

## 003 · 2026-11-23 · Design proverbs, and a plan review that checks them

**Changed:** Added `PROVERBS.md`, six short sayings about how to build, each with a reason, a question to ask in the plan, and when to break it. Drafted the `poke-holes` skill, which reviews a plan against the brief, the proverbs, how it fails, and whether it can be built in small pieces. `fuzzy-clear` now asks what will need to change after launch.

The proverbs are replaceable. Skills depend on their shape (a saying and a question), not on which ones are listed, so anyone can swap in their own.

**Why:** The constitution covered how to work, but nothing said how to build. Design preferences cost a sentence in a plan and a rewrite once the code exists, so they belong at plan review.

**Touches:** `PROVERBS.md`, `skills/poke-holes/SKILL.md`, `skills/fuzzy-clear/SKILL.md`.

## 002 · 2026-11-23 · Written once, for any agent

**Changed:** All content is written once in an open format (`SKILL.md` for skills, plain Markdown for rules). Anything tool-specific is a thin file in `adapters/` that points back to the original.

**Why:** The first draft assumed one tool. A process that only works in one vendor's product is a habit, not a process.

**Touches:** repo layout, `AGENTS.md`.

## 001 · 2026-11-23 · `kickoff` became `fuzzy-clear`

**Changed:** The first skill was renamed from `kickoff` to `fuzzy-clear`. The list of unknowns became the "fuzz list" and the readiness checklist became the "clear check". A brief's status now starts at `fuzzy` and moves to `clear`.

**Why:** The name should say what goes in and what comes out. It also works as a verb, which makes it more likely to get used.

**Touches:** `skills/fuzzy-clear/SKILL.md`.
