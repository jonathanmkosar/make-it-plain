# Brief: proverbs and poke-holes

Type: new
Requester: Jonathan Kosar
Owner: Jonathan Kosar
Status: clear
Last updated: 2026-11-23

## The ask

"I want a doc for coding, architecture, and UI approaches. More abstract than anything. Nothing specific like which technology to use. I want to do this diligence before we implement. Later it doesn't work as well."

## The problem

The constitution says how to work, but nothing says how to build. My design preferences come up in every plan, and today they only get applied if I remember to say them.

## Why now

These preferences are cheap to apply in a plan and expensive to add once code exists. The next skill in the loop is the plan review, and it needs something to check a plan against.

## Done looks like

- `PROVERBS.md` holds each design preference as a short saying with a reason, a question to ask in the plan, and when to break it.
- `poke-holes` reviews a plan against the brief, the proverbs, how it fails, and whether it can be built in small pieces.
- `fuzzy-clear` asks what will need to change after launch.
- A plan reviewed with `poke-holes` comes back with each proverb marked followed, broken on purpose, or not addressed.
- Someone can replace the proverbs with their own and nothing else in the repo breaks.

## Out of scope

- Naming any language, framework, or vendor.
- Proverbs I have not actually stated. The list starts with six and grows by amendment.
- Rewriting a plan. The review finds holes; the author closes them.

## Constraints

- Abstract enough to still be true after the tools change.
- Every proverb says when to break it, so the list does not become a checklist that kills good work.
- A project can override a proverb in its own rules file with a stated reason.

## What already exists

- Known names for most of these: configuration over hard-coding, feature flags, the open/closed principle, composition over inheritance, pay-per-use.
- A precedent for the format in short engineering sayings such as the Go proverbs.

## Terms

- **Proverb**: a short design saying that holds unless there is a stated reason to break it.
- **Hole**: a specific thing in a plan that will cause trouble later, reported with a way to close it.
- **The ladder**: where a changeable value lives, decided by who changes it and when (constant, configuration, setting, preference).

## Decisions

| Decision | Why | Hard to reverse? | Owner |
|---|---|---|---|
| Call it `PROVERBS.md` | Keeps the thread of the repo name, and short sayings are easier to remember in a review than a principles document. | No | Jonathan |
| Proverbs are checked at plan review | That is the cheapest point to act on them. | No | Jonathan |
| Each proverb carries a "break it when" | A principle applied everywhere becomes the perfect-system trap. | No | Jonathan |
| Build the proverbs and `poke-holes` together | The review needs something to check against, and the proverbs need a place where they get asked. | No | Jonathan |

## Risks

- The list reads as dogma -> every proverb says when to break it, and breaking one with a reason is not counted as a hole.
- "Make it configurable" becomes everything is a setting -> the ladder asks who would change the value before it becomes one.
- The review pads its findings to look thorough -> the skill says to report a sound plan as sound in one line.

## How we will prove it works

Run `poke-holes` on a real plan from a personal project. The report names at least one hole the author agrees is real, and none the author considers invented.

## Release and sign-off

Jonathan reviews both files before they are committed.

## Open questions

| Question | Owner | Blocks start? |
|---|---|---|
| Which real plan is the first test of `poke-holes`? | Jonathan | No |
| Should `adapters/` stay as an empty folder or be removed until needed? | Jonathan | No |

## Log

- 2026-11-23: Brief written from Jonathan's description of his design preferences. Six proverbs, all his own. The ladder and the "break it when" line were added during the conversation.
