---
name: fuzzy-clear
description: Start any new piece of work (a new build, an integration, or a fix) by turning a fuzzy ask into a clear written brief through rounds of questions. Use whenever the user says 'fuzzy clear', 'let's fuzzy-clear this', 'help me define this', 'I have a vague ask', 'grill me', or begins something new before requirements exist.
---

# Fuzzy Clear

Take something fuzzy in, hand something clear back. Turn a vague ask into a written brief before any building starts. The ask may come from an executive, a project manager, a customer, an internal team, or the user's own head. It works the same in any tool and any project.

The idea behind it: most problems that show up late (wrong thing built, rework, surprise constraints) were already present at the start as an unasked question. Asking those questions up front is cheap. Finding them in review or production is not.

The output is one short document, the **brief**. It is not a requirements spec or a technical plan. It is the thing those get written from.

## The constitution

These are the standing rules the process protects. Every run checks the work against them. When something goes wrong later, the fix is to amend this list or the questions below, not to work around it once.

1. **Clarify before building.** The problem, who it is for, and what "done" looks like are written down and agreed before any code.
2. **Context first.** Read what already exists (code, docs, tickets, standards) before proposing anything.
3. **Plan before code.** A reviewed approach comes before implementation. This is the cheapest place to catch a wrong direction.
4. **Small pieces.** Work is split into tasks that can each be built and checked on their own.
5. **Build with checks.** Each piece has a way to prove it works, decided before it is built.
6. **Evidence, not claims.** "It works" means test output, a screenshot, or a reproduced result. A person reviews before it ships.
7. **Normal pipeline.** Agent-written work goes through the same review and release gates as anyone's.
8. **Feed lessons back.** Every miss becomes an amendment to this process.

## How to run it

### 1. Size it

Match the effort to the work. A one-line bug fix needs a three-line brief and maybe two questions. A new system needs the full interview. If the process feels heavier than the work, shrink it. A process people skip protects nothing.

Also name the type, because it changes which questions matter most:

- **New**: who is it for, and what is the smallest version that is useful?
- **Integrate**: what is the agreement between the two sides, who owns the other side, and what happens when it fails?
- **Fix**: can it be reproduced, what is expected versus actual, when did it start, and how will we know it stays fixed?

### 2. Read before asking

Look at whatever is reachable: the codebase, existing docs, linked tickets, connected tools, earlier briefs. Never ask the user something that can be looked up. Asking it wastes their attention and signals the homework was skipped. If something found contradicts what the user said, raise it.

### 3. Restate and list the fuzz

Say the ask back in two or three plain sentences. Then list what is fuzzy: unclear, assumed, or undecided. This list is the agenda for the interview. Start the brief file now with whatever is already known, so there is something concrete to correct.

### 4. Interview in rounds

Ask a round of three to five questions, then stop and wait. Then the next round.

- **Order by impact.** Ask first what would most change what gets built.
- **Recommend an answer** to every question, with one line of why. Reacting to a proposal is far easier than answering cold, and it exposes the assumptions being made.
- **Write as you go.** When an answer settles something, put it in the brief right away and cross it off the fuzz list. The conversation disappears; the document does not.
- **Challenge vague words.** "Fast", "simple", "users", "integrate", "soon" each hide a decision. Ask what they mean here. If a term conflicts with how the project already uses it, say so and settle on one meaning.
- **Push on the weak spots.** Ask what happens when it fails, who disagrees, what was tried before, and what would make this not worth doing.
- **Ask what will change.** What will need to change after launch, and who changes it? Values and behavior that vary are cheap to plan for now and expensive to add later. Record the answer under constraints.
- **Accept "I don't know".** The user often does not have the answer because the requester has not said. Record it as an open question with an owner. Do not invent an answer to keep moving.
- **Stop when further questions would not change what gets built.** More questions past that point are delay.

### 5. Clear check

Before handing off, confirm each line. Anything that fails is either fixed now or listed as an open question with an owner.

- The problem is stated in one or two sentences a non-technical person would agree with.
- "Done" is something observable, not a feeling.
- Out of scope is written down.
- Constraints are known: deadline, budget, technology, compliance, people.
- Hard-to-reverse decisions are named and have an owner.
- There is a stated way to prove it works.
- It is clear who signs off and how it gets released.
- No open question blocks starting.

### 6. Hand off

Give the user the brief and, separately, a short list of **questions to take back to the requester** if any remain. Then offer the next step: a plan, then tasks. Do not start building inside this skill.

### 7. Come back

The process is meant to be corrected by use.

- **During the work:** if the brief turns out wrong, update the brief first, then the work. The brief stays the source of truth.
- **When something goes wrong later:** ask which step of the constitution or which question would have caught it. Propose a specific amendment: a new question, a new clear-check line, or a changed rule.
- **At the end:** one line in the brief's log on what this run missed, even if the answer is "nothing".

Project-specific amendments go in that project's standing rules file (for example `AGENTS.md`). Amendments that apply everywhere are proposed as a change to this skill. Keep amendments small and worded as a rule or a question, not a story.

## Where the brief lives

In a repository, write it to `docs/briefs/<short-name>.md` unless the project already has a convention. Outside a repository, produce it as a document in whatever form the environment offers. Either way it is a file the user can keep, share, and edit, not a chat message.

## Brief template

Use this structure. Drop sections that do not apply to small work rather than filling them with filler.

```markdown
# Brief: <short name>

Type: new | integrate | fix
Requester: <who asked>
Owner: <who is accountable>
Status: fuzzy | clear | in progress | done
Last updated: <date>

## The ask
<the original request, in the requester's words>

## The problem
<one or two plain sentences: what is wrong or missing, and for whom>

## Why now
<what happens if nothing is done>

## Done looks like
- <observable outcome>
- <observable outcome>

## Out of scope
- <what this will not do>

## Constraints
<deadline, budget, technology, compliance, people>

## What already exists
<relevant systems, code, docs, prior attempts, and who owns them>

## Terms
- **<term>**: <what it means here>

## Decisions
| Decision | Why | Hard to reverse? | Owner |
|---|---|---|---|

## Risks
- <risk> -> <what we do about it>

## How we will prove it works
<tests, checks, or evidence required before it is called done>

## Release and sign-off
<how it ships and who approves>

## Open questions
| Question | Owner | Blocks start? |
|---|---|---|

## Log
- <date>: <what changed in this brief, or what this run missed>
```
