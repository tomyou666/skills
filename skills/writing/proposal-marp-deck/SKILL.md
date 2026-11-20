---
name: proposal-marp-deck
description: >-
  Creates customer-facing proposal slide decks in Marp. Use when the user
  asks for a proposal deck or system-architecture proposal slides.
disable-model-invocation: true
---

# Proposal Marp deck

Customer-facing **proposal** slides built on the installed `create-marp-deck` skill. Read that skill’s `SKILL.md` before generating.

## Relationship to create-marp-deck

| Topic | This skill |
| --- | --- |
| Frontmatter, CSS palette, breadcrumbs, `<!-- _class: lead … -->`, sentence case, export `--no-stdin` | Follow create-marp-deck |
| Phase 1 one-question-at-a-time interview | **Do not use** — use the workflow below |
| Mermaid as the default diagram in the first draft | **Do not use** — use diagram instruction placeholders |
| Mobile HTML / editable PPTX | Only if the user asks |

`create-marp-deck` is a separate skill. Read its `SKILL.md` before any deck work. If that file cannot be read, Stop and give the user this install command. Continue only after that `SKILL.md` can be read.

```bash
npx skills add https://github.com/omerr/claude-skills --skill create-marp-deck
```

## Workflow (overrides create-marp-deck Phase 1)

1. **Require create-marp-deck** — Confirm its `SKILL.md` can be read. If not, stop with the install command above.
2. **Read inputs** — Notes, requirements, and attachments the user points to. Facts only; no guessing.
3. **Batch missing decisions** — Ask open decisions in one `AskQuestion` call (audience mix, must-cover topics, out-of-scope, depth of logic/examples, output path). Prefer recommended options first with `(Recommended)`.
4. **Outline approval gate** — Before creating or editing any deck file, post a short **text outline** in chat covering:
   - Chapter list under the three bones below (with any case-specific additions)
   - Intent of each planned slide (one line each)
   - Diagram placeholders: what each figure should show (boxes, arrows, labels, emphasis)
   - Out of scope
   - Terminology level (plain language for non-IT readers)
   Wait for explicit approval. Do not write the Marp file until approved.
5. **Generate and export** — Write the Marp markdown, then:

```bash
npx @marp-team/marp-cli@latest --no-stdin FILENAME.md -o FILENAME.html
npx @marp-team/marp-cli@latest --no-stdin --pptx FILENAME.md -o FILENAME.pptx
```

Always use `--no-stdin`.

## Outline bones

Use these three axes as the default spine. Add chapters when the case needs them (e.g. core logic, security, assumptions).

1. **Background and purpose** — Current pain and the goal after introduction. Prefer a Before / After comparison figure near the start.
2. **Overview** — Who uses it, what they enter, what they get back, and the main capabilities.
3. **Detail** — How the main logic or calculation works (short), system shape and access control, assumptions, and out of scope.

A Japanese deck reads `headings.ja.md` beside this file before the outline and before writing slides.

Target roughly **10–16 slides**. One idea per slide. Keep lists to 3–5 bullets.

## Plain language

- Write so a non-IT stakeholder understands each sentence on first read.
- Prefer everyday words over jargon. If a product name is required, pair it with a one-clause role.
- **Do not put on slides:** internal API steps, config values (timeouts, memory, QPS), token/claim/subnet-level detail, or cloud pricing calculator numbers.
- Service names on architecture slides are fine when each has a short role label.

## Diagram placeholders and layout

### First draft: instruction text only

Do not generate images or write Mermaid. On each diagram slide, put the creation brief as text, for example:

```markdown
# Background and purpose (figure)

**図プレースホルダ（作成指示）**

- Left panel titled 現状: input → person searches records by hand → cost calculated in a spreadsheet
- Right panel titled 導入後: user enters an ID → system estimates two ways → user decides with reasons shown
- Large arrow from left to right
- Flat business infographic, 16:9, white background, clear Japanese labels
```

### Split diagram and body text

Always use two slides:

1. **Diagram-only** — Title + placeholder (or later the image). No long bullet list under the figure.
2. **Key points** — Bullets that used to sit under the figure.

Use `<!-- _class: diagram-only -->` on diagram slides. Add this to the shared `<style>` block from create-marp-deck:

```css
section.diagram-only img {
  display: block;
  margin: 0.4em auto 0;
  max-height: 520px;
  width: auto;
  max-width: 1120px;
  object-fit: contain;
}
```

When an image is present, prefer `![height:520px](./images/....png)` over a huge width that crowds the slide.

## Diagram text instead of Mermaid

Do not use Mermaid. Marp does not render it as a figure, so it is not a diagram format for this skill.

On each diagram slide, the creation brief is the figure. Write it as text:

- Panels or boxes, and the title of each
- What each box contains, in reading order
- Arrows and what they connect
- Labels, and which part to emphasize
- Frame: 16:9, white background, and the language of the labels

## Suggested slide order

1. Title (source document if any, audience, date)
2. Agenda (chapter names only)
3. For each chapter: section divider → diagram-only (if any) → key-points → optional short example slides
4. Assumptions / out of scope when needed
5. Open questions for the customer when needed

Part CSS classes: map bones to short names (e.g. `part-purpose`, `part-overview`, `part-detail`) and assign create-marp-deck palette colors.

## Done when

- [ ] `create-marp-deck` `SKILL.md` was read before any deck work; if it was missing, the deck was not written
- [ ] A Japanese deck uses the three chapter titles from `headings.ja.md`
- [ ] Outline was approved in chat before the Marp file was written
- [ ] Deck uses create-marp-deck frontmatter, breadcrumbs, and section styles
- [ ] Each diagram slide is a text creation brief, not Mermaid; body text is on the following slide
- [ ] Language is plain; no implementation/config/pricing-detail dump
- [ ] HTML and PPTX exported with `--no-stdin` (and `--allow-local-files` if local images are embedded)
