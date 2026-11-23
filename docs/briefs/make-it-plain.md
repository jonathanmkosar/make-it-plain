# Brief: make-it-plain

Type: new
Requester: Jonathan Kosar
Owner: Jonathan Kosar
Status: clear
Last updated: 2026-11-23

## The ask

"I want one way of starting work with agents that I can use anywhere and keep fixing."

## The problem

I have a process for agent-led work, but it lives in my head and in chat logs. Nobody else can see it, and I can't improve what isn't written down.

## Why now

Without a written version, the process drifts from project to project and every lesson has to be relearned. It also can't be shown to anyone who asks how I work.

## Done looks like

- The constitution, one working skill (`fuzzy-clear`), and one real worked example are public.
- A stranger can run the skill in their own agent in under five minutes.
- The top screen of the README states the point of view and shows one before and after.
- Every change to the rules is logged with a date and a reason.

## Out of scope

- Anything tied to one vendor's product.
- Employer code, names, or examples.
- Claims that can't be backed by something in the repo: no usage numbers, no testimonials.
- The other four skills. They are added one at a time after launch.

## Constraints

- Built on personal time and equipment.
- Plain Markdown in open formats only. No build step, no dependencies.
- Readable by a non-technical person.

## What already exists

- The eight-step process, drafted as a one-page interview answer.
- A first draft of the `fuzzy-clear` skill.
- Open formats that already cover portability: Agent Skills (`SKILL.md`) for skills and `AGENTS.md` for repo rules.

## Terms

- **Brief**: the one-page document `fuzzy-clear` produces. Requirements and plans are written from it.
- **Constitution**: the eight standing rules.
- **Amendment**: a dated, reasoned change to a rule or a skill.
- **Skill**: a folder with a `SKILL.md` that an agent can follow.
- **Adapter**: a small tool-specific file that points back to a skill.

## Decisions

| Decision | Why | Hard to reverse? | Owner |
|---|---|---|---|
| Name the repo `make-it-plain` | Habakkuk 2:2 supplies the step that comes before "make it work, make it right, make it fast". | Somewhat. Links break on rename. | Jonathan |
| Interviewer is the first reader, developer second | The top screen has to make the case in 60 seconds. Install steps can sit lower. | No | Jonathan |
| Write once, adapters only where needed | A process tied to one tool stops being useful when the tool changes. | No | Jonathan |
| Launch with one skill | A history that shows the repo growing is stronger than five untested skills on day one. | No | Jonathan |
| Silly names, serious content | The names get remembered. The content has to hold up. | No | Jonathan |
| MIT license | Anyone can use it, including at work. | Yes, for released versions | Jonathan |

## Risks

- It reads as a prompt collection -> lead with the point of view and the amendments log, not the file list.
- A skill is listed as ready before it has been tested -> nothing is marked ready until it has been run.
- The process grows until nobody follows it -> removing a rule counts as an amendment and is encouraged.
- It quietly becomes tied to one tool -> the write-once rule is in `AGENTS.md` and checked on every change.

## How we will prove it works

Run `fuzzy-clear` cold in three different agents on the same fuzzy ask. All three produce a brief that passes the clear check. Record the results in this log.

## Release and sign-off

Jonathan reviews every file, then the repo is made public. Later changes that touch a rule or a skill are logged in `AMENDMENTS.md`.

## Open questions

| Question | Owner | Blocks start? |
|---|---|---|
| What is the exact skills folder for each major tool? | Jonathan | No. Needed before per-tool install steps are added. |
| Which skill comes second? | Jonathan | No |

## Log

- 2026-11-23: Brief written from one round of questions. The first draft assumed a single tool; corrected to tool-agnostic and logged as amendment 002.
- 2026-11-23: Working name changed to `make-it-plain`.
