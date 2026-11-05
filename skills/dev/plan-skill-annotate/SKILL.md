---
name: plan-skill-annotate
description: >-
  Annotate a Cursor plan markdown with matching project/user skill notes per step.
  Explicit invoke only (e.g. plan under `.cursor/plans/`).
compatibility: Requires Cursor plan-mode markdown
disable-model-invocation: true
---

# Plan Skill Annotate

User names this skill **and** a plan MD. Do not auto-run.

## Steps

1. Read the plan MD.
2. List `SKILL.md` under project `.agents/skills`, `.claude/skills`, `.cursor/skills` and user `~/.agents/skills`, `~/.claude/skills`, `~/.cursor/skills` (skip missing dirs).
3. For each skill except `plan-skill-annotate`, use frontmatter `name` + `description`; skim body only if match is unclear.
4. Where a step clearly fits a skill, prepend at the **top** of that step's bullets (skip if that skill is already mentioned):

```markdown
- **Skill:** Use the `skill-name` skill.
```

Optional `(short reason)`. English only; exact `name`. Several skills → extra **Skill:** line or `; ` on one line.

5. Brief reply: skills added and steps, or no matches (do not invent notes).

## Limits

- No `~/.cursor/skills-cursor/`.
- Do not rewrite plan content, dump all skills, or change todos / plan frontmatter unless asked.

## Examples (this repo)

| Plan work | Skill |
|-----------|--------|
| Go funcs / methods / struct fields | `go-docstring-style` |
| Wire / providers / wire_gen | `go-wire` |
| TSX copy / labels / aria | `tsx-i18n-messages` |
| Tests | `test-overview-style` |
| Feature/fix after impl | `update-changelog` |
| DESIGN.md → shadcn CSS | `design-to-shadcn-css` |

Elsewhere: same match from each skill's `description`.
