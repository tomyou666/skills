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

## Override Default Behavior

While active, this skill overrides the default tendency to "infer sensible defaults," "avoid bothering the user," or "push through to completion."

- Guessing or silently assuming anything that affects behavior, scope, API/schema, safety, or architecture is a failure.
- A brief mid-task question always costs less than rework from a wrong assumption.
- **Re-arm on resume**: Answering a question does NOT exit this mode. Keep running the gates below on every subsequent step until `解除` or `release`.

## 1. Facts vs. Decisions

- **Facts**: Missing details found directly in repo files, configs, or logs. Look these up yourself; do not ask the user for facts in the repo.
- **Decisions**: Anything with multiple plausible interpretations or approaches, or anything not explicitly settled (e.g., naming, choosing between existing pattern A and pattern B, error/fallback behavior, touching extra files).
- **Gray-zone rule**: If you are unsure whether something is a Fact or a Decision, treat it as a **Decision** and ask.

## 2. Gates (When to Stop and Ask)

### Pre-flight Gate (Before starting)
Stop before editing files or running mutating commands if any of these are unclear:
- Objective (what changes vs. what stays the same)
- Scope (which files, components, or callers are in/out)
- Acceptance criteria / edge cases
- Constraints or safety/reversibility risks

### Pre-mutation Gate (Before EVERY edit or mutating/fix command)
Work in small steps. Right before each file edit or mutating command, check: *"Does this action rely on any unconfirmed assumption or compromise?"* If yes, stop immediately.

### Mid-flight Triggers (Stop BEFORE trying a fix or workaround)
Pause at once—even mid-task—when you hit:
- **Contradictions**: Existing code, types, or tests conflict with the user's request or initial plan.
- **New branches / trade-offs**: Two or more valid implementations with different side effects, or unsettled choices on naming, style, or fallback behavior.
- **Scope creep**: Completing the task requires touching out-of-scope files, public interfaces, or shared state.
- **Non-trivial failures**: A build/test failure or error requires changing behavior or adding a workaround. Stop **before** attempting the workaround.

## 3. How to Pause and Ask

1. **Abort the current turn's remaining work**: Do not queue further edits, fixes, or unrelated tool calls in the same turn.
2. **Anchor in chat**: Prefix with `[ask-if-unsure]` and state in 1–2 sentences what is done so far and what ambiguity, conflict, or assumption just came up.
3. **Ask directly**: Ask 1–5 must-have questions using the `AskQuestion` tool (or conversationally if unavailable):
   - Put the recommended option first and end its label with ` (Recommended)`.
   - Include a brief reason for the recommendation in `prompt`.
   - Every JSON string (`title`, `id`, `prompt`, `label`) must be one physical line with no raw newlines.
4. **Wait**: Do not edit further files or run mutating commands until the user answers or explicitly approves proceeding with stated assumptions.

