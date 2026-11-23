# Constitution

The standing rules for building software with AI agents. Every piece of work is checked against them. When something goes wrong, the fix is an amendment here, not a one-time workaround.

These rules apply the same way in any tool. Nothing here depends on a vendor.

This document is about how to work. For how to build, see [`PROVERBS.md`](PROVERBS.md).

## Before the rules

Three things this document assumes.

- **The person leads, the agent builds.** The person owns what gets built and whether it is right. The agent does most of the typing. Accountability does not transfer.
- **Working beats perfect.** A process that tries to be complete on day one gets skipped by day three. This one starts small and earns each addition.
- **Size it to the work.** A one-line fix gets a three-line brief. If the process is heavier than the task, shrink the process.

## Make it plain

### 1. Clarify before building

The problem, who it is for, and what "done" looks like are written down and agreed before any code.

*Why:* an agent will build whatever it is handed, quickly and confidently. A vague ask produces a wrong result that looks finished.

### 2. Context first

Read what already exists (code, docs, tickets, standards) before proposing anything. Never ask a person something that can be looked up.

*Why:* most bad plans come from not knowing what is already there.

### 3. Plan before code

A written approach is reviewed and corrected before implementation starts.

*Why:* changing a plan costs a sentence. Changing an implementation costs a rewrite.

### 4. Small pieces

Work is split into tasks that can each be built and checked on their own.

*Why:* small pieces are easy to review, easy to undo, and give the agent a clear finish line.

## Make it work

### 5. Build with checks

Each piece has a way to prove it works, decided before it is built. The agent runs the checks itself and commits often.

*Why:* a check is how the agent knows it is done. Without one, it stops when the code looks plausible.

## Make it right

### 6. Evidence, not claims

"It works" means test output, a command and its result, or a screenshot. A person reviews before it ships. For larger work, a second reviewer that did not write it looks at it fresh.

*Why:* agents report success readily. Evidence is quick to check and holds up when nobody was watching the session.

### 7. Normal pipeline

Agent-written work goes through the same review, automated checks, and sign-off as anyone's.

*Why:* the gates exist to protect the system. Who typed the code does not change what the system needs.

## Make it fast

### 8. Feed lessons back

Every miss becomes an amendment to these rules or to a skill. Speed comes last, and it comes from the process getting better, not from skipping steps.

*Why:* a mistake fixed only in the code will be made again. A mistake fixed in the rules is made once.

## Bring your own

These eight are one person's rules. Yours can differ, and the skills will use yours.

**What a rule needs**

| Part | Required? | Why |
|---|---|---|
| A name, in a few words | Yes | So it can be pointed to when something goes wrong. |
| A plain statement of the rule | Yes | This is the part the skills read. |
| Why it matters | Recommended | So it can be argued with. |

The four steps (make it plain, work, right, fast) are a way to group the rules. They are optional.

**What you can do**

- **Replace the whole list.** Delete these and write your own in the same shape.
- **Add or remove one.** Order and numbering do not matter.
- **Switch one off for a single project.** Say in that project's rules file which rule does not apply there, and why.
- **Keep your list somewhere else.** Point to it from the project's rules file.

**Why nothing breaks**

No skill refers to a rule by number. `fuzzy-clear` reads whatever constitution the project has. If a project has none, it falls back to a short set of starter rules.

Rule numbers appear in the README tables, which are there for readers and are not read by any skill.

**The limit**

Swapping the rules changes what the work is checked against. It does not change what the skills do: `fuzzy-clear` still writes a brief before anything is built. A rule that no skill acts on is only enforced by people remembering it, until someone writes a skill for it.

## How to amend

1. Something goes wrong, or a step turns out to be dead weight.
2. Ask which rule or which question should have caught it.
3. Write the change as a rule or a question, not a story. Keep it small.
4. Log it in [`AMENDMENTS.md`](AMENDMENTS.md) with the date and the reason.

Removing a rule that nobody follows counts as an amendment and is welcome.

**Where an amendment goes:**

- It applies to every project: here, or in the relevant skill.
- It applies to one project: that project's own rules file (for example `AGENTS.md`).
