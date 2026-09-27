# skills

[日本語](../README.md)

[![skills.sh](https://skills.sh/b/tomyou666/skills)](https://skills.sh/tomyou666/skills)

Agent Skills for commits, reviews, writing, Obsidian, and Qiita.

## Install

Interactively pick skills and agents.

```bash
npx skills@latest add tomyou666/skills
```

For all projects, append `-g` to each command.

To install a single skill (replace `<SKILL>` with the skill name):

```bash
npx skills@latest add tomyou666/skills --skill <SKILL>
```

### Groups

Install only the groups you need.

```bash
# Conversation behavior
npx skills@latest add tomyou666/skills/skills/session

# Implementation, Git, review
npx skills@latest add tomyou666/skills/skills/dev

# Procedures, proposals/estimates, explanations, glossaries, theory notes, math sheets, design docs
npx skills@latest add tomyou666/skills/skills/writing

# Vault folders, naming, and formatting
npx skills@latest add tomyou666/skills/skills/obsidian

# Qiita articles
npx skills@latest add tomyou666/skills/skills/qiita
```

Verify what you installed:

```bash
npx skills list
```

## How to invoke

Mention the skill name in chat. In Cursor, use `/skill-name` or `@skill-name`.

**User-invoked** skills run only when you name them. **Model-invoked** skills may be chosen by the agent when the task matches. Name the skill if you need it to follow every time.

## Skills

### session

Conversation behavior.

- **[ask-question-tool](../skills/session/ask-question-tool/SKILL.md)** (User-invoked): Put questions on Cursor’s AskQuestion tool
- **[brief-english-final](../skills/session/brief-english-final/SKILL.md)** (User-invoked): Keep interim progress in one English line; keep the final answer in the configured language
- **[grilling4cursor](../skills/session/grilling4cursor/SKILL.md)** (User-invoked): Ask design questions in rounds, then package ready questions into AskQuestion. Do not start until shared understanding is confirmed
- **[no-local](../skills/session/no-local/SKILL.md)** (User-invoked): Do not use local files or commands until released
- **[no-write](../skills/session/no-write/SKILL.md)** (User-invoked): Do not create, edit, or delete files until released
- **[say-once](../skills/session/say-once/SKILL.md)** (User-invoked): Use only words a typical adult can follow in one pass; write only what is not yet known

### dev

Implementation, Git, review.

- **[git-commit-en](../skills/dev/git-commit-en/SKILL.md)** (User-invoked): Write English Conventional Commits from the staged diff
- **[git-commit-jn](../skills/dev/git-commit-jn/SKILL.md)** (User-invoked): Write Japanese Conventional Commits from the staged diff
- **[code-comments](../skills/dev/code-comments/SKILL.md)** (User-invoked): Write implementation comments and test summaries in Japanese
- **[design-to-shadcn-css](../skills/dev/design-to-shadcn-css/SKILL.md)** (User-invoked): Map `DESIGN.md` color tokens to shadcn CSS variables
- **[go-docstring-style](../skills/dev/go-docstring-style/SKILL.md)** (User-invoked): Add docstrings to Go functions, methods, and fields
- **[go-wire](../skills/dev/go-wire/SKILL.md)** (User-invoked): Keep Google Wire assembly inside the composition root
- **[test-overview-style](../skills/dev/test-overview-style/SKILL.md)** (User-invoked): Align test suite overviews and case naming
- **[tsx-i18n-messages](../skills/dev/tsx-i18n-messages/SKILL.md)** (User-invoked): Move TSX display copy into i18n messages
- **[update-changelog](../skills/dev/update-changelog/SKILL.md)** (Model-invoked): Append one Japanese line under Unreleased in `CHANGELOG.md`
- **[impl-code-check](../skills/dev/impl-code-check/SKILL.md)** (User-invoked): Report bug risk, dead code, missing tests, and error handling in the recent diff (do not fix)
- **[plan-skill-annotate](../skills/dev/plan-skill-annotate/SKILL.md)** (User-invoked): Annotate each step in a plan markdown with the skills to use
- **[pr-overview](../skills/dev/pr-overview/SKILL.md)** (User-invoked): Produce a non-technical Japanese PR/MR title and body

### writing

Procedures, proposals/estimates, explanations, glossaries, theory notes, math sheets, design docs.

- **[design-doc-builder](../skills/writing/design-doc-builder/SKILL.md)** (User-invoked): Split requirements into a design doc by chapter. Do not create a file unless a save path is given
- **[explanation-writing](../skills/writing/explanation-writing/SKILL.md)** (User-invoked): Write or rewrite clear explanations that start from the big picture
- **[finance-theory-collection](../skills/writing/finance-theory-collection/SKILL.md)** (User-invoked): Create or append a finance theory collection in a shared format (Obsidian note format)
- **[glossary-writing](../skills/writing/glossary-writing/SKILL.md)** (User-invoked): Write glossaries with plain explanations and minimal theory (Obsidian note format)
- **[math-cheat-sheet](../skills/writing/math-cheat-sheet/SKILL.md)** (User-invoked): Create or update math cheat-sheet notes (Obsidian note format)
- **[procedure-writing](../skills/writing/procedure-writing/SKILL.md)** (User-invoked): Write procedures that can be followed from top to bottom
- **[proposal-estimate-draft](../skills/writing/proposal-estimate-draft/SKILL.md)** (User-invoked): Create or revise customer proposals and high-level estimate line items in Markdown

### obsidian

Vault folders, naming, and formatting.

- **[obsidian-vault](../skills/obsidian/obsidian-vault/SKILL.md)** (Model-invoked): Follow vault folder layout, naming, creation flow, and Markdown/math formatting

### qiita

Qiita articles.

- **[qiita-article-planner](../skills/qiita/qiita-article-planner/SKILL.md)** (User-invoked): Ask for theme and persona, then build a heading outline
- **[qiita-sample-pattern-extractor](../skills/qiita/qiita-sample-pattern-extractor/SKILL.md)** (User-invoked): Extract like-attracting patterns from sample articles
- **[qiita-writing-principles](../skills/qiita/qiita-writing-principles/SKILL.md)** (User-invoked): Check article structure and reader design for like-attracting posts

## Develop in this repository

When using these skills from Cursor inside this repo, run from the repository root.

```bash
npx skills@latest add . -a cursor -y
```
