---
name: skill-fb
description: >-
  Write feedback and improvements from the current session at the end of
  that session. Use the whole chat so far. Cover missing, ambiguous,
  harmful, and worth-keeping instructions, plus a gap against a written
  done condition. Improvements are only defects likely to recur, each with
  a reason and one episode, and no replacement wording.
disable-model-invocation: true
---

# skill-fb

The invoke is the end of the session to review. Do not offer this skill on your own.

Chat only. Do not edit files.

## Material

Use this chat from the start through the invoke. That whole stretch is the session. Do not narrow it to the latest skill, and do not ask which skill to review.

Read each `SKILL.md` that was followed in the session.

## Items

Judge the instructions that shaped the session, including each skill that was followed. A clear instruction the session simply did not follow is not an item.

Start each item with one of these labels and nothing else in front of it:

| Label | Use when |
| --- | --- |
| Missing instruction | The user later supplied a judgment, input, or step the instructions did not contain |
| Ambiguous instruction | The session had to guess what the instructions meant |
| Harmful instruction | The instructions contradicted themselves, ran long, asked too early, or spelled a step the session never used |
| Worth keeping | That wording is what made the session work |
| Done-condition gap | A followed skill states a done condition, and the session showed that the wording does not match what finishing required |

Skip `Done-condition gap` when no followed skill states a done condition. When an item is about a skill, name that skill in the reason.

## Headings

`Improvements`, then `Feedback`.

- `Improvements`: a wording defect another session would likely hit again. Put the most likely first. `Worth keeping` never goes here.
- `Feedback`: a one-off episode from this session, and every `Worth keeping`.

Each item is the label, the reason, and one episode from this session. Do not name a heading inside a skill file. Do not draft a replacement sentence.

Omit a label with no item. When `Improvements` has no item, write `No improvements`, then write `Feedback` if it has items.
