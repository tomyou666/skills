---
name: grilling4cursor
description: >-
  Interview the user about a plan or design until shared understanding,
  asking each round's full frontier through Cursor AskQuestion. Use only
  when explicitly invoked.
disable-model-invocation: true
compatibility: Requires Cursor AskQuestion tool
---

# Grilling for Cursor

Interview the user relentlessly until you reach a shared understanding. Map this as a **design tree**: every decision branches into the decisions that hang off it.

Do not act on the design until the user confirms that shared understanding.

## Rounds

Work the tree in **rounds**. The **frontier** is every decision whose prerequisites are already settled: the questions you can ask now without guessing at answers you haven't heard yet.

Ask the whole frontier in one round, in a single AskQuestion call. A question whose answer depends on another question still open in this round belongs to a later round, not this one.

Each round the user answers reshapes the tree: settled decisions push the frontier outward and unblock questions that depended on them. Recompute the frontier and ask the next round. Wait for the user's answers before the next round.

The session is done when the frontier is empty: every branch visited, nothing left silently assumed.

## Facts and decisions

Finding facts is your job, never the user's. When a frontier question needs a fact from the environment (filesystem, tools, etc.), dispatch a sub-agent to find it; don't ask the user for anything you could look up yourself. Don't block on it: a running exploration is an unsettled prerequisite, so only the questions downstream of it wait for the sub-agent to report; ask the rest of the frontier now. The decisions are the user's: put each to them and wait.

## How to ask

Deliver the round only through AskQuestion. In chat, write a short preface: what is already settled, and which round this is. Do not repeat the question text in chat.

One AskQuestion call per round:

- `title`: the round label (for example `Round 2`)
- One entry per frontier decision
- `prompt`: number, title, body, and the reason for the recommendation. The body may be several paragraphs and may name the choices
- `options`: at least two. Put the recommended option first. End its label with ` (Recommended)`
- `allow_multiple`: only when the decision is multi-select
- Free text stays on the tool's Other input. Do not add an Other option yourself

## Shared understanding

When the frontier is empty:

1. Write the shared understanding in chat, in the user's language. This is the record of settled decisions, not a second copy of the questions.
2. Ask one AskQuestion: whether to proceed with that understanding. Recommended option first, label ending with ` (Recommended)`.
3. Do not act until the user chooses to proceed. If they do not, recompute the frontier and continue.
