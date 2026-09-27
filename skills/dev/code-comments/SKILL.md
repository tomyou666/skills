---
name: code-comments
description: Add Japanese comments to implementations and Japanese summaries to tests. Use when writing, editing, or reviewing code or tests in any language (Java, TypeScript, and others).
---

# Code Comments

Write comments and test descriptions in Japanese. Keep them short. Comment intent, not the code itself.

## Implementation

- Comment each processing step.
- Add a brief Japanese comment to functions, classes, objects, constants, types, enums, and similar declarations.
- Skip comments that add no information.

## Tests

- Give each case a Japanese summary of what is tested and the expected result.
- Use the language's usual field: `description`, `it`, `test`, `@DisplayName`, docstring, etc.

## Style

- Use the current language's comment syntax (`//`, `/* */`, `#`, `--`, Javadoc, JSDoc, etc.).
- Do not translate identifiers or user-facing copy unless asked.
