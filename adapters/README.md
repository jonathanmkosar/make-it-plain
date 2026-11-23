# Adapters

Small, tool-specific files for agents that need something beyond the standard skill folder.

**There are none yet, on purpose.** Every skill in this repo is a standard `SKILL.md` folder, which most agents can read directly, and any agent can be told to read the file and follow it.

## When to add one

Add an adapter only when a specific tool cannot use a skill as written. For example, it needs a different file name, a different folder, or a command wrapper.

## Rules

- One folder per tool: `adapters/<tool>/`.
- An adapter points to the skill. It never restates the skill's content.
- Say at the top which tool and version it was tested with, and the date.
- If the tool later reads the standard format, delete the adapter and log it in `AMENDMENTS.md`.
