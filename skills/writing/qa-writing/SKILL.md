---
name: qa-writing
description: Turn chat Q&A exchanges, notes, or meeting records into a structured QA.md file. Use when asked to save, summarize, or extract questions and answers into a file.
disable-model-invocation: true
---

# QA Writing

Write or update `QA.md` from questions and answers in the chat or in given notes.

## File placement

```
/
├── QA.md
└── <context>/
    └── QA.md
```

Put `QA.md` in the target folder, or at the root when the workspace has a single context. Create it if missing; append new entries to the end if it already exists. Do not ask where to save it.

## Ordering and grouping

- Always append new Q&A entries at the end of the file. Do not insert them by topic order, overview-first order, or anywhere else in the middle.
- Single topic: use `## Q. <Question>`.
- Multiple topics or appending a new topic: group under `## <Category>` and use `### Q. <Question>`. When the category already exists, still append the new entry at the file end (do not insert under the existing heading mid-file).
- Make each question self-contained so it makes sense without the prior conversation.
- Record only the final answer. Drop false starts and mid-chat corrections.

## Entry format

```markdown
## <Category>

### Q. <Self-contained question>

**A. <Direct answer in 1–2 sentences>**

- <Supporting detail, breakdown, or table, only when needed>
- **Open**: <Unsettled point, only when one remains>
```

### Sources

Include sources only when the user asks for them upfront. When requested, add a bullet list at the end of the entry:

```markdown
- **Sources**:
  - `<path or doc>`: <what it supports>
```
