---
name: poke-holes
description: Review a plan before any code is written by attacking it. Checks the plan against the brief, the design proverbs, how it fails, and whether it can be built in small pieces, then returns a short list of holes ranked by what they would cost later. Use whenever the user says 'poke holes', 'review this plan', 'what am I missing', 'is this plan ready', or has a plan and is about to start building.
---

# Poke Holes

Attack a plan before any code is written. A plan is the cheapest place to be wrong: changing it costs a sentence, and changing the implementation costs a rewrite.

This serves rule 3 of the constitution (plan before code) and checks that rules 4 and 5 (small pieces, build with checks) are possible.

The output is a short list of **holes**: specific things in the plan that will cause trouble later, each with a way to close it. It is not a rewritten plan.

## What you need

- **The plan.** Any form: a document, a list, a paragraph.
- **The brief** the plan is meant to deliver. If there is none, say so. For small work, restate the ask in two sentences and carry on. For anything larger, recommend running `fuzzy-clear` first, because a plan cannot be checked against a goal nobody wrote down.
- **The project's design proverbs**, if it has any. Pass 2 says where to look and what to do when there are none.

## How to run it

### 1. Size it

A plan for a small fix gets a quick read and maybe one hole. A plan for a new system gets all four passes. If the review is heavier than the plan, shrink the review.

### 2. Read before judging

Read the plan, the brief, the project's rules, and the code the plan touches. Do not ask the user what can be looked up. Many holes are simply things that already exist and the plan did not know about.

### 3. Say the plan back

Restate the plan in three plain sentences: what gets built, in what order, and how we will know it worked. If that cannot be done, that is the first hole.

### 4. Make four passes

**Pass 1: against the brief.**

- Does the plan deliver every item under "done looks like"?
- Does it do anything listed as out of scope, or anything nobody asked for?
- Does it respect the constraints?
- Does it leave an open question unanswered that it depends on?

**Pass 2: against the proverbs.**

Use whatever proverbs the project has. This skill depends on their shape, not their content: any list works as long as each entry has a saying and a question to ask of a plan. Never assume a particular proverb exists.

Look in this order and stop at the first one found:

1. A proverbs file that the project's rules file points to.
2. A `PROVERBS.md` at the project root.
3. Neither. Use the starter questions below, and say in the report that the project has no proverbs of its own.

A project's own proverbs replace the starter questions completely. Do not mix the two lists. If an entry has no question, turn its saying into one and note that you did. If the project's rules say a proverb does not apply, skip it and record the reason given.

Starter questions, for projects with no proverbs:

- **What varies?** Which values will someone want to change, who changes them, and how fast do they need to?
- **Who decides?** Where will users want different behavior, and can they change it without the team?
- **Where is the off switch?** If this goes wrong, how is it turned off, and by whom?
- **What happens on the next case?** When a new variation arrives, what gets added and what has to be reopened?
- **Do the pieces stand alone?** Can each part be understood and tested by itself?
- **What does idle cost?** What does this cost with no use, and at ten times the load?

Then ask each question of the plan. Mark each one as **followed**, **broken on purpose** (the plan says why), or **not addressed**. Only "not addressed" is a hole. A proverb broken with a stated reason is a decision, and decisions are allowed.

**Pass 3: how it fails.**

- For each outside dependency: what happens when it is slow, down, or returns something wrong?
- Which step is hardest to undo? What is the way back?
- What is the plan assuming that nobody has checked?

**Pass 4: can it be built in small pieces.**

- Can the work be split into pieces that are each built and checked on their own?
- Does each piece have a stated way to prove it works?
- Is there a first piece that is useful by itself?

### 5. Report the holes

Rank by what the hole would cost if found after the code exists, most expensive first.

- **Every hole comes with a way to close it.** A hole with no suggested fix is a complaint.
- **Recommend one fix**, with a line of why. The user reacts faster to a proposal than to an open question.
- **Separate holes from taste.** "This will break" is a hole. "I would have done it differently" is not, and goes in a separate short list or nowhere.
- **Do not pad.** If the plan is sound, say so in one line. Inventing holes to look thorough teaches the user to ignore the review.

### 6. Give a verdict

One of three:

- **Ready.** Build it.
- **Ready with changes.** List the holes that must be closed first.
- **Not ready.** Say what is missing, and whether the problem is the plan or the brief behind it.

Do not rewrite the plan unless asked, and do not start building.

### 7. Come back

When a problem turns up during the build that this review should have caught, ask which pass missed it and propose a new question for that pass. That is how this skill gets better.

## Report template

```markdown
# Plan review: <short name>

Verdict: ready | ready with changes | not ready
Reviewed: <date>

## The plan in three sentences
<what gets built, in what order, how we know it worked>

## Holes
| # | Hole | Why it matters | Suggested fix | Must close before building? |
|---|---|---|---|---|

## Proverbs
| Proverb | Followed / broken on purpose / not addressed | Note |
|---|---|---|

## Matters of taste
- <optional, short, clearly labeled as opinion>

## What this review did not check
- <anything that could not be read or verified>
```
