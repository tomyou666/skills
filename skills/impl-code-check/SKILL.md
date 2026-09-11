---
name: impl-code-check
description: Review recent implementation for bug risk, dead code, missing tests, and error-handling gaps. Use only when the user explicitly invokes this skill (e.g. /impl-code-check).
---

# Impl Code Check

Review the recent implementation diff (uncommitted or user-specified scope). Read code. No guessing. If clean, write "none".

## Scope

- Target: latest implementation changes. Honor user-specified scope
- Do not fix. Report only. Fix only if user asks

## Output (these 4 headings only)

Short bullets. No long quotes, no full file dumps.

When a finding maps to specific code, always cite the file and the line or range (`path:line` or `path:start-end`). Omit location only when there is none.

### Bug risk

Honest take: is this change bug-prone? One-line why. Concrete risks as bullets.

### Dead code

Unused funcs, unreachable branches, stale call paths, leftover config keys. Else "none".

### Missing tests

Gaps / tests worth adding. High → low priority. Else "none".

### Error handling

Missed nil / timeout / cancel / partial failure. Else "none".

## Rules

- Save tokens: no preamble, summary, or praise
- Prefix severity: `high` / `mid` / `low` when it differs
- Every concrete finding includes file + line (or range); do not drop them to save tokens
- Code blocks only for decisive snippets (few lines), with path and line numbers
- Reply in English unless user asks otherwise
