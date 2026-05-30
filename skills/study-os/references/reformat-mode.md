# Reformat Mode

Restructure the layout of existing text WITHOUT changing the text itself. No proofreading, rewriting, or grammar fixes. Goal: optimize reading, space, and a clean structure.

## Text invariance (strict)

- Do NOT add, remove, or modify any words, punctuation, numbers, emojis, or URLs.
- You may only change **structure and block types** (lists, to-dos, headings, toggles, callouts, columns, tables) and whitespace/line-break placement.
- You may change list markers only as required to create proper list blocks. In Notion, author bullets with `-`.

## Scope

- If a selection is present, ONLY change content within it. Touch nothing outside.
- If there is no selection, reformat the entire page (or the provided context).

## Primary goals

- Make the document skimmable.
- Increase visual consistency across sections.
- Preserve meaning by preserving text exactly.

## Structural rules (apply in this order)

### Line breaks and blocks
- Collapse clearly unintended line breaks into a single line.
- Turn valid line breaks into new blocks (prefer multiple short paragraphs over a wall of text).
- One idea per block whenever possible.

### Bullets and checklists
- Convert informal bullets (`· item`, `• item`, `- item` when meant as bullets) into proper bulleted list blocks.
- Convert checklist patterns (`· [ ] item`, `[ ] item`) into proper to-do blocks (`- [ ] item`).
- Keep list indentation consistent, especially under toggles.

### Headings and chapters
- Create headings where there are clear section boundaries.
- Hierarchy: H1 only for the page's main topic when needed (do not repeat the page title as an H1 at the top); H2 for main sections/chapters; H3 for subsections.
- Do not introduce numbering unless the text already uses it.

### Toggles
- Use toggles to reduce clutter only when a section is long or clearly "appendix-like".
- Prefer toggle headings for major chapters on long pages; normal headings for shorter sections.
- Do not create deep nesting unless it already exists.

### Callouts
- Use callouts only for content that is already a "callout concept" (decisions, pending decisions, warnings, key notes).
- Do not rewrite callout text; only move existing lines into the callout.

### Columns
- Use columns only for two parallel lists/blocks of similar importance.
- Use 2 columns to save space when a section has only a little content (a short heading + 2–6 bullets) and it splits cleanly without changing words.
- Do not split a single logical sequence across columns. Limit to 2 columns unless 3+ is already intentional.

### Tables
- Convert to a table only if the text is already table-like (repeated "Label: Value" patterns) and the mapping is unambiguous.
- Do not change any cell text, capitalization, or links.

## Consistency sweep (required)

After reformatting:
- One bullet style per section (no mixed `·` and `-`).
- Checklists are consistently to-do blocks.
- Headings consistent and not duplicated.
- Link text and URLs unchanged.
- Tables valid and unchanged in content.

> Note on em dashes: the global "no em dash" rule applies to text the skill writes. In Reformat mode text invariance wins, so do NOT strip or alter existing em dashes (that would change punctuation). Flag them to the user instead if asked.
