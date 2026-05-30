---
name: study-os
description: >-
  Builds deep, expert-level study and research material from rough keywords/notes, in Notion
  or as a PDF/document, and manages the underlying study database. Use when the user says
  "open this Notion page and build the study material", "structure this study page", "turn these
  notes into a study page", "research this topic and write it up", "make a study PDF about X",
  "deepen / expand this page", "create a study page about X", "reformat this page", "explain this
  concept", "add a study entry", "update my study index", or points to a Notion page/database or
  a document for study, research, theory, notes, deep-dives, or article writing. Produces clean,
  lean, compact, consistently structured material with formatted links (never bare URLs), tables,
  columns, toggles, diagrams, examples, image suggestions, chapters as toggles, sources only where
  they add weight, and a synced database row. Input-agnostic (keywords, notes, dumps, an existing
  page) and output-agnostic (Notion or PDF/doc); detects any Notion database schema at runtime.
  Never uses em dashes in any output.
---

# Study OS

A repeatable engine for turning sparse inputs (keywords, topics, dumped notes) into **complete, expert-level, beautifully structured Notion study pages**, and for keeping the study **database** clean and consistent. Every page comes out with the same architecture, the same writing rules, and the same level of rigor, regardless of topic or who runs it.

This skill exists because generic AI writing stays shallow and high-level. Study OS does the opposite: it researches, goes chapter by chapter, cites dated sources, and lays out content for fast reading and long-term reuse.

---

## Core principle

> Concise does NOT mean shallow. Write dense, expert-level material with clear hierarchy and consistent frameworks. Never pad, never go generic, never stay surface-level.

Rules that override everything else:

1. **Depth with structure.** Bullets to structure claims; short paragraphs (max 5-7 lines) only to fully explain complex points. Tables, columns, toggles, and diagrams when they aid comprehension. Always include concrete **examples** and **deep-dives** for the hard parts.
2. **Lean and compact layout.** Use space well: 2-column blocks for short parallel content, toggles for appendix/deep-dive detail, tables for comparisons, bullet lists for claims. No walls of text, no empty filler sections.
3. **Formatted links only.** Embed every link inside descriptive words. **Never a bare or dirty URL** in any output.
4. **Sources where they add weight, not everywhere.** Cite a specific quote, a statistic, an important claim, or a contested point. Do NOT footnote every line: the goal is a sharp study page, not a thesis. Keep a short Sources block per chapter or at the end.
5. **Consistency is the product.** The same activity type always produces the same shape. A reader should recognize a Study OS page instantly.

### Hard formatting bans (every mode, every output)

- **Never use an em dash (—) anywhere in any output.** Not in Notion, not in PDFs, not in chat. Use a comma, a colon, parentheses, or split the sentence. The only exception is verbatim quoted source text, which is preserved exactly.
- No bare URLs. No numbered chapter titles unless there is a real numeric/priority order.

Full rules live in `references/writing-standards.md`. Read it before writing any page.

---

## When to use which mode

This skill has three modes. Pick based on the request.

| Mode | Trigger | What it does |
| --- | --- | --- |
| **Build** (default) | "build / structure / research / deepen this study page", "create a page about X" | Reads inputs, researches, writes the full page, updates the DB row. |
| **Reformat** | "reformat", "clean up the structure", "make this skimmable" | Restructures blocks WITHOUT changing any words. See `references/reformat-mode.md`. |
| **Explain** | "explain this", "ELI5 this concept" | Answers in chat only (does NOT edit the page). Short, plain-language explanation of a selection/concept. |

If the request is ambiguous, default to **Build**.

---

## Build mode - the workflow

Run these steps in order. Do not skip the index confirmation for theory pages unless the user said "just go" / "autonomous".

### 1. Read the target
- Fetch the Notion page the user points to (`notion-fetch` with the URL/ID). Extract every keyword, topic, note, link, and half-finished thought already on it.
- Fetch the parent database/data source to learn the **schema at runtime** (`notion-fetch` on the `collection://` URL). Never assume property names - read them. See `references/notion-operations.md`.
- If no page exists yet, the user's prompt text IS the input.

### 2. Classify
- Decide **Theory vs Practice** (and whether it's a hybrid). Theory = "why / how to reason"; Practice = "how to do it, step by step". Hybrid pages get two explicit sections. See `references/classification.md`.
- Map the topic to the database's category property values (read them from the schema; don't invent new ones unless asked).

### 3. Propose the index
- Draft a chapter-level **index of content** (chapter titles + one-line scope each) and a short **source list** you intend to use.
- Present it in chat and ask for a quick confirm - UNLESS the user requested autonomous mode, in which case proceed directly.
- Chapters use the term **"Chapter"**, never numbered unless there is a real numeric/priority order ("Chapter - Title", not "Chapter 1 - Title").

### 4. Research (this is what makes it deep)
- Use web search to gather authoritative, current sources. Prefer primary sources, official docs, standards bodies, academic/industry references.
- Capture **absolute dates** for anything time-sensitive (prices, regulations, versions, leadership, stats).
- Collect: key facts, competing viewpoints, concrete numbers, a few high-quality videos, and points where an **image/diagram would help** (flag these inline).
- Full sourcing rules: `references/research-protocol.md`.

### 5. Write the page
- Build with the exact block syntax and architecture in `references/page-architecture.md` and `references/notion-operations.md`.
- Page skeleton (every page):
  - Meta callout (gray): `Last Updated` + `Related Pages`.
  - Purpose callout (blue): **Page Purpose** + **Non-scope** + **Related Pages**.
  - `# Main Topic` then a horizontal rule.
  - Chapters as **toggle headings**, each: `Chapter - Title` → **Summary** bullets → **Content** → chapter Sources/Links/Glossary.
  - Tables for 3+ options/dimensions; 2-column layouts for short parallel blocks to save space; diagrams/flowcharts for processes.
  - Image suggestions where they aid learning.
  - A short **Sources** (and optional **Glossary** / **Links**) section at the end of each chapter or the page.
- Hard style rules: **no em dashes** in your own writing; bold the label before a colon in bullets; embed links in descriptive text; gray=neutral, blue=insight, green=positive outcome.
- Write the content into Notion via `notion-update-page` (`insert_content` / `update_content` / `replace_content`). Preserve existing child pages when replacing - see `references/notion-operations.md`.

### 6. Update the database
- Set/refresh the row's properties from the schema you read: title, category, scope (Theory/Practice), a 1–2 line content description, reading order, page URL, and Done as appropriate.
- Keep anti-duplication discipline: if a sibling page covers part of this, note the difference in the Non-scope / Related Pages lines rather than repeating content.
- Details: `references/notion-operations.md` → "Database management".

### 7. Consistency sweep (required)
- **Scan the entire output for "—" and remove every one** (replace with comma/colon/parentheses or split the sentence), except inside verbatim quotes.
- Every link is formatted descriptive text, not a bare URL. Examples present for non-obvious concepts. Sources attached to quotes/key data but not over-applied.
- One bullet style per section; headings consistent and not duplicated; tables valid; no stray numbering; layout is lean (columns/toggles/tables used where they help).
- Confirm the page matches the standard skeleton and that the DB row is coherent with reality.

---

## Agnostic by design

This skill must work for **any topic, any input, any output, any workspace, any user**.

**Input-agnostic.** The input can be a few keywords, a messy note dump, a list of links, a half-written page, or just the user's prompt. Treat whatever is provided as raw material; the workflow is the same.

**Output-agnostic.** The same content model renders to different targets. Decide the target from the request:
- **Notion** (default): write/update the page with the block syntax in `references/page-architecture.md`, then sync the database row.
- **PDF / document**: produce the same lean, compact structure as a clean document. Build it with the relevant document skill (e.g. the `pdf` or `docx` skill) from the same chapter model: meta + purpose block, chapters, summary bullets, content, tables, 2-column layouts where they save space, formatted links, image suggestions, and a sources section. Toggles collapse to clearly labeled sections (or a table of contents) in a PDF.
- The structure, depth, and formatting rules are identical across targets. Only the rendering mechanics differ. See `references/output-targets.md`.

**Workspace-agnostic.** Never hardcode category lists, property names, or database IDs. Always read them from the live schema. If the target database lacks a useful property (e.g. Scope, Reading Order), proceed with what exists and optionally suggest adding it (`notion-update-data-source`), but only with user consent.

**Language.** Default output language is **English**; switch only if the user explicitly asks.

---

## Reference files

Read these as needed; they hold the precise rules so output is identical every time.

- `references/writing-standards.md` - voice, formatting, visual structure, study-page rules.
- `references/page-architecture.md` - the page skeleton, templates, chapter structure, block syntax.
- `references/notion-operations.md` - how to read/write Notion, schema detection, DB management, safe edits.
- `references/research-protocol.md` - source quality, dating, videos, images, depth bar.
- `references/classification.md` - Theory vs Practice vs Real Setup decision rules.
- `references/reformat-mode.md` - strict text-invariant restructuring rules.
- `references/output-targets.md` - how the content model renders to Notion vs PDF/doc.
