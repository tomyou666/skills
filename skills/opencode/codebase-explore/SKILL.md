---
name: codebase-explore
description: >-
  Prefer codebase_context/peek and lsp_*/implementation_lookup/call_graph over
  grep for OpenCode exploration with oh-my-opencode-slim and open-codebase-index.
disable-model-invocation: true
---

# Codebase Explore

- When exploring a codebase, prefer `codebase_context` or `codebase_peek` before repeating a simple `grep`.
- To investigate a symbol's definition, references, or call path, use `lsp_*` tools or `implementation_lookup` / `call_graph`.
