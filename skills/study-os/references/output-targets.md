# Output Targets

The skill is output-agnostic: one content model, multiple renderings. Decide the target from the request ("in Notion", "as a PDF", "a document"). Default is Notion. The structure, depth, examples, and formatting rules are identical across targets; only the rendering mechanics change.

## The shared content model

Every output, regardless of target, carries the same parts:
- Meta (Last Updated + Related Pages) and a Purpose + Non-scope intro.
- A main topic, then chapters: each with Summary bullets and dense Content.
- Tables for comparisons, 2-column blocks for short parallel content, bullet lists for claims, diagrams for processes.
- Concrete examples and deep-dives for the hard parts.
- Image suggestions where they aid learning.
- Sources only where they add weight (quotes, statistics, key/contested claims), as a short section per chapter or at the end.
- Formatted links (descriptive words, never bare URLs). No em dashes anywhere.

## Rendering to Notion (default)

- Use the block syntax in `page-architecture.md`: `<callout>`, `<details><summary>### Chapter - Title</summary>`, `<table>`, `<columns>`, `<mention-page>`, `<mention-date>`, `<table_of_contents>`.
- Chapters are toggle headings. Links are inline `[text](url)`.
- After writing, sync the database row (`notion-operations.md`).

## Rendering to PDF / document

- Build with the relevant document skill (e.g. `pdf` or `docx`). Map the model like this:

| Model element | Notion | PDF / document |
| --- | --- | --- |
| Chapter (toggle) | toggle heading | clear H2 section, listed in a table of contents |
| Meta + Purpose | callouts | a boxed/intro block at the top |
| Comparison | `<table>` | a real table |
| Short parallel content | `<columns>` | a 2-column layout or a compact table |
| Deep-dive/appendix | nested toggle | an appendix section or a clearly labeled sidebar |
| Link | inline mention/link | hyperlinked descriptive text (never a raw URL) |
| Image suggestion | inline note | placed figure with caption, or a noted placeholder |

- Keep it lean and compact: a reader should skim the table of contents and jump. No padding.
- Page numbers, a title page, and a table of contents are appropriate for longer PDFs.

## Choosing the target

- "in Notion", a Notion URL, "update the page", "study index" -> Notion.
- "PDF", "document", "export", "printable", "hand this to someone" -> PDF/doc.
- If unspecified and a Notion page/database is in play -> Notion. Otherwise ask only if it is genuinely ambiguous; default to Notion.
