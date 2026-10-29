---
name: ask-if-unsure
description: >-
  Pause and ask for confirmation both before starting and mid-execution
  whenever requirements, edge cases, or trade-offs are ambiguous. Explicit
  invoke only (/ask-if-unsure). Persist until 解除 or release.
disable-model-invocation: true
---

# Ask If Unsure (Pre-flight & Mid-flight Gate)

ACTIVE until user says `解除` or `release` (turns off all such modes).

Never guess or silently assume when a decision affects behavior, scope, API/schema, safety, or architecture. Pause and get approval both **before starting** and **during work**.

## 1. Facts vs. Decisions

- **Facts**: If a missing detail can be found by reading files, configs, or logs, look it up yourself. Do not ask the user for facts available in the repo.
- **Decisions**: If multiple plausible interpretations or approaches exist, stop and ask the user.

## 2. When to Stop and Ask

### Pre-flight (Before acting)
Stop before editing files or running mutating commands if any of these are unclear:
- Objective (what changes vs. what stays the same)
- Scope (which files, components, or callers are in/out)
- Acceptance criteria / edge cases
- Constraints or safety/reversibility risks

### Mid-flight (During execution)
Immediately pause ongoing work—even in the middle of a multi-step task—when you encounter:
- **Contradictions**: Existing code, types, or tests conflict with the user's request or initial plan.
- **New branches / trade-offs**: Discovering two or more valid ways to implement a step with different side effects.
- **Scope creep**: Fixing or completing the task requires touching out-of-scope files, public interfaces, or shared state.
- **Non-trivial failures**: A build/test failure or error cannot be fixed without changing behavior or adding a workaround.

## 3. How to Ask

1. When pausing mid-flight, state in 1–2 sentences in chat: what is done so far and what ambiguity/conflict was just found.
2. Use the `ask-question-tool` skill to ask the user. If that skill is not available, ask 1–5 must-have questions using the `AskQuestion` tool (or conversationally if unavailable):
   - Put the recommended option first and end its label with ` (Recommended)`.
   - Include a brief reason for the recommendation in `prompt`.
   - Every JSON string (`title`, `id`, `prompt`, `label`) must be one physical line with no raw newlines.
3. Do not edit further files or run mutating commands until the user answers or explicitly approves proceeding with stated assumptions.
