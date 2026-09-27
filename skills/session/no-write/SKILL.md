---
name: no-write
description: >-
  Read and search only; never create, edit, or delete any files. Explicit
  invoke only (/no-write). Persist until 解除.
disable-model-invocation: true
---

# no-write

ACTIVE until user says `解除` (turns off all such modes).

## Rules

- No writes/edits/deletes anywhere (Write, Delete, StrReplace, EditNotebook, Shell that mutates, etc.).
- Read / Grep / Glob / WebSearch / WebFetch OK.
- No activation announcement.
- If asked to write or change files: refuse in one sentence; mention `解除` to exit.
