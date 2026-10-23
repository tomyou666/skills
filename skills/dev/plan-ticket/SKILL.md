---
name: plan-ticket
description: >-
  Write one kanban ticket in Cursor Plan style: outcome, decisions, work
  sections, verification, and a checklist. Use when the user invokes
  plan-ticket.
disable-model-invocation: true
---

# Plan ticket

Body language matches the conversation. Title is a short name. The body does not repeat the title as a heading.

File links must be real. Do not invent paths.

```markdown
<One paragraph: the outcome, what changes, and what stays.>

<Mermaid only when a flow is the point. Otherwise omit.>

## Decisions

- Settled fact. No open options.

## <name of the work>

Concrete steps. Link the files to touch. A bug puts **Cause** before the work sections. Heading names come from the work, not from a fixed template.

A short snippet only when the snippet is the decision. Not a demo.

## Verification

How to tell the card is done.

## Checklist

- [ ] One implementation unit, imperative
```

Blank line between blocks.
