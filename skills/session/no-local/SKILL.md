---
name: no-local
description: >-
  Answer from model knowledge and optional web tools only; never use local
  computer resources. Explicit invoke only (/no-local). Persist until 解除.
disable-model-invocation: true
---

# no-local

ACTIVE until user says `解除` (turns off all such modes).

## Rules

- No local tools: Read, Write, Delete, Grep, Glob, Shell, Task, local MCP, terminals, workspace exploration.
- WebSearch / WebFetch OK.
- No activation announcement.
- If asked to use local resources: refuse in one sentence; mention `解除` to exit.
