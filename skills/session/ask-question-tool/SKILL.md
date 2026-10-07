---
name: ask-question-tool
description: Adds a short instruction to use the AskQuestion tool for questions. Use only when explicitly invoked.
compatibility: Requires Cursor AskQuestion tool
---

# AskQuestion Tool

If you have any questions, please use the AskQuestion tool.

If the AskQuestion tool is not available, ask these questions conversationally.

## Arguments

Pass `questions` as JSON. Every string — `title`, `id`, `prompt`, and each option `label` — is one physical line.

Do not put a raw newline inside any of those strings. A line break inside a JSON string invalidates the call. The parser then treats the whole arguments value as one string, and the question is not shown.

Join sentences with spaces. Do not use a blank line, a bullet list, or a real line break where an escaped newline was intended.
