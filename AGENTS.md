# Working in this repo

Instructions for any AI agent (or person) making changes here.

## What this repo is

A process for building software with AI agents: a constitution of eight rules, a set of skills that carry them out, and a log of every change to both. It is public and meant to be used with any agent.

## Rules for changes

- **Write once.** A skill's content lives in `skills/<name>/SKILL.md` and nowhere else. Do not copy it into tool-specific files.
- **Adapters stay thin.** If a tool needs something special, add a small file under `adapters/` that points back to the skill. An adapter never restates the skill.
- **Nothing vendor-specific in skills or the constitution.** No tool names, no tool-only commands. If an instruction only works in one product, it belongs in an adapter.
- **Log every rule change.** Any edit to `CONSTITUTION.md` or a skill's behavior gets an entry in `AMENDMENTS.md` with the date and the reason. Typo fixes do not.
- **Plain language.** Short sentences, no jargon, no filler. A non-technical reader should be able to follow the README and the constitution.
- **No unbacked claims.** Do not add usage numbers, testimonials, or "used by" lines. A skill is marked ready only after it has been run.
- **No private material.** No employer code, names, or examples. Worked examples come from personal projects or invented asks.

## Adding a skill

1. Run `fuzzy-clear` on the idea first and save the brief under `docs/briefs/`.
2. Create `skills/<name>/SKILL.md` with `name` and `description` in the frontmatter.
3. Say which constitution rules it serves.
4. Add it to the skills table in `README.md`, marked planned until it has been run on real work.

## Layout

```text
CONSTITUTION.md   the rules
AMENDMENTS.md     the change log
skills/           one folder per skill
adapters/         tool-specific pointers, only where needed
docs/briefs/      briefs produced by the process
```
