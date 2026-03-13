---
description: Lightweight project init — scans root config files and generates a minimal AGENTS.md
---

Perform a quick, lightweight analysis of this project. Do NOT recursively explore source directories.

Based on what you find, generate or update `AGENTS.md` with the following minimal structure:

```markdown
# Project

> <one-line description of the project>

## Stack

- <technology / framework / language>
- ...

## Common commands

| Action | Command |
|--------|---------|
| <action> | `<command>` |

## Conventions

- <any key convention found in config files>
```

Rules:
- Keep `AGENTS.md` under 80 lines.
- search commands in Makefile
- precise the local dev environment used and force to use the tools used in the project.
- Do not invent information — only use what is explicitly found in the scanned files.
- If `AGENTS.md` already exists, replace its content with the new one.
- Write the file, then confirm with a one-line summary of what was added.
