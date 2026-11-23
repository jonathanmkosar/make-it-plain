# Proverbs

Short sayings about how to build. The [constitution](CONSTITUTION.md) covers how we work. This covers what good work looks like once we start designing.

They are abstract on purpose. No proverb names a language, a framework, or a vendor. Each one should still be true after the tools change.

## How to use them

- **They are defaults, not laws.** A project can override any proverb in its own rules file, as long as it says why.
- **They are checked in the plan, not after.** A setting or an off switch costs a sentence in a plan and a rewrite once the code exists. The `poke-holes` skill asks each proverb's question during plan review.
- **Every proverb says when to break it.** A principle followed everywhere becomes the perfect-system trap: more settings, more flags, more layers, and less of the thing that was valuable.
- **They are mine, and they are replaceable.** Swap in your own and nothing else in this repo breaks. See "Bring your own" at the end.

| # | Proverb | Mostly about |
|---|---|---|
| 1 | Boil up what varies | Architecture, code |
| 2 | Let the user decide at runtime | UI, architecture |
| 3 | Every launch has an off switch | Architecture, release |
| 4 | Add, don't edit | Architecture, code |
| 5 | Compose, don't inherit | Code |
| 6 | Idle costs nothing | Architecture |

---

## 1. Boil up what varies

Any value that differs by environment, by user, or over time lives in a setting, not in the code. Retry counts, timeouts, limits, and thresholds are the usual suspects.

*Why:* these are the values that get tuned once the system meets real use. Changing a setting takes minutes. Changing code takes a release.

**Not everything goes to the user.** For each value, ask who changes it and when. That tells you where it lives.

| Who changes it | Where it lives |
|---|---|
| Nobody | A constant in code |
| The team, at deploy | Configuration |
| An operator, while it's running | A flag or setting |
| The end user | A preference |

*Ask in the plan:* Which values here will someone want to change? Who, and how fast do they need to?

*Break it when:* the value has one right answer, or nobody can name who would change it. Every setting is one more thing to test and one more way to get it wrong. Every setting also needs a default that works with nothing configured.

## 2. Let the user decide at runtime

Where people reasonably differ, make it a preference they can change while using the product. Light or dark. Fresh data or cached.

*Why:* any single hard-coded choice is wrong for someone, and the team becomes the bottleneck for every difference of opinion.

*Ask in the plan:* Where will users want this to behave differently from each other? Can they change it without us?

*Break it when:* the choice affects safety, cost, or other users. Also break it when an option would only hand the user a decision the team should have made. A good default comes first; the preference is for the people it doesn't fit.

## 3. Every launch has an off switch

New behavior ships behind a flag that can be turned off and on without a new release.

*Why:* it separates deploying from releasing. When a launch goes wrong, the fastest fix is turning it off.

*Ask in the plan:* If this goes wrong at 2 a.m., how do we turn it off, and who can?

*Break it when:* the change is trivial, or it cannot sensibly be half on, such as a change to stored data. That kind of change needs a rollback plan instead. Remove the flag once the feature has settled. Old flags pile up and nobody remembers what they guard.

## 4. Add, don't edit

Design so the next case is added beside what exists, not by reopening code that already shipped.

*Why:* working code that nobody touches keeps working. Every edit to shipped code risks breaking something that was fine.

*Ask in the plan:* When the next variation arrives, what do we add, and what do we have to reopen?

*Break it when:* you would be guessing at extension points nobody has asked for. Wait for the second real case before building the place to plug it in.

## 5. Compose, don't inherit

Build behavior from small functions and parts that are combined, not from deep class hierarchies.

*Why:* a small piece can be tested alone, reused, and swapped. A hierarchy ties its members together, so a change at the top ripples down to everything below.

*Ask in the plan:* Can each piece be understood and tested by itself?

*Break it when:* the framework or platform you are working in is built around inheritance. Go with the grain of the tool.

## 6. Idle costs nothing

Prefer designs where you pay for what is used and nothing while nobody is using it.

*Why:* most systems sit idle most of the time. Cost should follow use, and nobody should have to guess capacity in advance.

*Ask in the plan:* What does this cost when nobody is using it? What does it cost at ten times the load?

*Break it when:* steady heavy use makes always-on cheaper, or when the delay of starting from idle is something the user would feel.

---

## Bring your own

These six are one person's preferences. Yours will differ, and the process does not care which ones you use.

**What a proverb needs**

| Part | Required? | Why |
|---|---|---|
| A saying, in a handful of words | Yes | It has to be remembered in a review. |
| A question to ask of a plan | Yes | This is the part the plan review reads. |
| Why it matters | Recommended | So it can be argued with. |
| When to break it | Recommended | So it does not become dogma. |

**What you can do**

- **Replace the whole list.** Delete these and write your own in the same shape.
- **Add or remove one.** Order and numbering do not matter.
- **Override one for a single project.** Say in that project's rules file which proverb does not apply there, and why.
- **Keep your list somewhere else.** Point to it from the project's rules file.

**Why nothing breaks**

No skill refers to a proverb by name or number. `poke-holes` reads whatever list the project has and asks each entry's question. If a project has none, it falls back to a short set of starter questions and says so.

The only other place these six appear is the summary table in the README, which is there for readers and is not read by any skill.

## Changing the list in this repo

A proverb earns its place here by coming up in more than one plan. To add, change, or remove one:

1. Write it in the shape above.
2. Log it in [`AMENDMENTS.md`](AMENDMENTS.md) with the date and the reason.
