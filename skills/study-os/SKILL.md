---
name: study-os
description: >-
  Builds deep, expert-level study material from rough keywords, notes or an existing index, as pages or as
  a document. Use when the user says: build the study material, structure this study page, turn these notes
  into a study page, complete this index, what is missing from this page, research this topic and write it
  up, summarise this book, book summary, language course or grammar page, make a study PDF about X, deepen or
  expand this page, reformat this page, explain this concept, or points at a page, a database or a document
  for study, research, theory, notes, books or languages. Three page types: topic, book summary, language
  course. Finds gaps and conflicts with other pages before writing; keeps the core agnostic and puts
  domain applications in vertical sub-pages. Produces dense,
  unpadded material with formatted links (never bare URLs), tables, columns, diagrams, examples, chapters as
  real headings, sources only where they add weight, and a synced database row. Input and output agnostic.
  No em dashes.
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
6. **Give it soul.** A correct page that reads like a generated template is a failure. Open chapters with a hook, vary the structure to fit the material, write like an expert talking to a smart peer, and use the signpost system (💡 💬 🧩 🔑 ⚠️ 🧭 📚). Personality lives in framing and selection, never in padding. See `references/writing-standards.md` -> "Soul".
7. **Complete, never padded.** Completeness comes from covering every sub-topic, not from more words per sub-topic. Every sentence carries a fact, a number, a mechanism, an example, a decision rule or a warning; anything else is cut. See `references/writing-standards.md` -> "Density".

### Hard formatting bans (every mode, every output)

- **Never use an em dash (—) anywhere in any output.** Not in Notion, not in PDFs, not in chat. Use a comma, a colon, parentheses, or split the sentence. The only exception is verbatim quoted source text, which is preserved exactly.
- No bare URLs. No numbered chapter titles unless there is a real numeric/priority order.

Full rules live in `references/writing-standards.md`. Read it before writing any page.

---

## When to use which mode

This skill has four modes. Pick based on the request.

| Mode | Trigger | What it does |
| --- | --- | --- |
| **Build** (default) | "build / structure / research / deepen this study page", "create a page about X" | Reads inputs, researches, writes the full page, updates the DB row. |
| **Reformat** | "reformat", "clean up the structure", "make this skimmable" | Restructures blocks WITHOUT changing any words. See `references/reformat-mode.md`. |
| **Explain** | "explain this", "ELI5 this concept" | Answers in chat only (does NOT edit the page). Short, plain-language explanation of a selection/concept. |
| **Refresh** | "refresh this page", "update the facts", "is this still current?" | Re-verify only the time-sensitive facts (dated claims, prices, versions, leaders, laws) on an existing page via search, and surgically update just those with `update_content`. Do NOT rewrite the whole page. Update the meta Last Updated date. |

If the request is ambiguous, default to **Build**.

### Page types

Build writes one of three page types, each with its own chapter set in `references/page-types.md`: **Topic** (default), **Book summary**, **Language course**. The database or the request decides the type. These templates replace platform templates (Notion database templates and similar), so the structure is portable.

---

## Build mode - the workflow

Run these steps in order. Do not skip the index confirmation for theory pages unless the user said "just go" / "autonomous".

### 1. Read the target
- Fetch the Notion page the user points to (`notion-fetch` with the URL/ID). Extract every keyword, topic, note, link, and half-finished thought already on it.
- Fetch the parent database/data source to learn the **schema at runtime** (`notion-fetch` on the `collection://` URL). Never assume property names - read them. See `references/notion-operations.md`.
- Fetch the **library home** (the page holding the database) for the library conventions: signpost legend, library language, macro-topics and Drive mirror (`references/notion-operations.md` -> "Library conventions").
- If no page exists yet, the user's prompt text IS the input.

### 2. Classify
- Decide the **page type** (Topic, Book summary, Language course) from `references/page-types.md`.
- Decide **Theory vs Practice** (and whether it's a hybrid). Theory = "why / how to reason"; Practice = "how to do it, step by step". Hybrid pages get two explicit sections. See `references/classification.md`.
- Map the topic to the database's category property values (read them from the schema; don't invent new ones unless asked).

### 3. Propose or complete the index
- **Always run `references/index-completion.md`** when the page has anything on it (an index, keywords, links): separate the core from the domain verticals, compare with an expert reference syllabus (missing, misplaced, redundant, too broad), and search the library for pages that duplicate, overlap or contradict it. Present the amended index (core chapters + verticals) and the conflicts as two compact tables.
- **Empty page:** draft the index (core chapters + verticals, one-line scope each) and a short source list, then run the conflict check on it.
- Present in chat and ask for a quick confirm, UNLESS the user requested autonomous mode, in which case proceed directly.
- Chapters are never numbered unless there is a real numeric/priority order.

### 4. Research (this is what makes it deep)
- **The user's own material first:** notes and links on the page, attachments, uploaded files, and connected file storage (with a Drive mirror, start from the macro-topic folder). Treat it as primary input and link to it. If the user says the material is in a storage they have not connected, say which connector would unlock it.
- Then web search for authoritative, current sources. Prefer primary sources, official docs, standards bodies, academic/industry references.
- Capture **absolute dates** for anything time-sensitive (prices, regulations, versions, leadership, stats).
- Collect: key facts, competing viewpoints, concrete numbers, a few high-quality videos, and the spots where a diagram, image, chart or interactive artifact would teach better than text.
- Full sourcing rules: `references/research-protocol.md`.

### 5. Write the page
- Build with the exact block syntax and architecture in `references/page-architecture.md` and `references/notion-operations.md`.
- Page skeleton (every page, details in `page-architecture.md`):
  - Meta callout (gray): Last Updated, level, reading time, Related Pages.
  - Purpose callout (blue): Page Purpose, Non-scope, Related Pages. **No signpost legend** (it lives on the library home page).
  - Hook paragraph, then the table of contents **inside a collapsed "Contents" toggle**, then a **concept map** (Mermaid) for topic and hub pages.
  - Hubs: child-page cards under `## Deep dives`. The cards ARE the index.
  - `# Main Topic`, a rule, then **core chapters** as real `## H2` headings, domain-agnostic.
  - `## Verticals`: one child page per domain where the topic has specific consequences (`<Topic>: <Domain>`), same skeleton.
  - Closing block in columns: Glossary | Watch + Resources, then Sources.
- **Every chapter carries a visual** (table, columns, diagram, image). Protocols and attacks are told with actors (Alice, Bob, Eve, Mallory) and a sequence diagram.
- **Links inside the words:** the words carrying a claim link to its source, at the point of use.
- **Images without manual work** (`references/media-assets.md`): Mermaid first; otherwise generate the chart and upload it, or find a licensed image and upload it; an interactive HTML embed where changing numbers teaches more; an image slot only as last resort.
- Signposts: 💡 Key idea, 💬 Example, 🧩 Analogy, 🔑 Insight, ⚠️ Watch out, 🧭 Open question, 📚 Go deeper.
- Hard style rules: **no em dashes** in your own writing; bold the label before a colon in bullets; gray=neutral, blue=insight, green=positive outcome.
- Write via `notion-update-page`, **surgical `update_content` / `insert_content` over full `replace_content`**; new pages and verticals in one `create-pages` call each (see `references/notion-operations.md`). Do not delegate writing or diagrams to Notion AI.

### 6. Update the database
- Set/refresh the row's properties from the schema you read: title, category (two when the page spans two macro-topics, for example STEM plus Bitcoin), scope (Theory/Practice), a 1-2 line content description, reading order, page URL, and an editorial page state if the schema has one.
- Link each vertical from its domain hub elsewhere in the library with an inline mention.
- Report any database structure issue you notice (`references/notion-operations.md` -> "Database structure checks"); structural fixes belong to Study Librarian.
- **Never change personal state:** learning status, review dates, read or listened checkboxes, personal ratings, owned formats. Those belong to the user.
- Keep anti-duplication discipline: if a sibling page covers part of this, note the difference in the Non-scope / Related Pages lines rather than repeating content.
- Details: `references/notion-operations.md` → "Database management".

### 7. Consistency sweep (required)
- **Scan the entire output for "—" and remove every one** (replace with comma/colon/parentheses or split the sentence), except inside verbatim quotes.
- Every link is formatted descriptive text, not a bare URL. Examples present for non-obvious concepts. Sources attached to quotes/key data but not over-applied.
- One bullet style per section; headings consistent and not duplicated; tables valid; no stray numbering; layout is lean (columns/toggles/tables used where they help).
- **Cut pass:** reread each chapter and delete every sentence the reader would not miss. Then check coverage: every index item and every keyword from the source is on the page.
- Confirm the page matches the standard skeleton and that the DB row is coherent with reality.
- **Run the full QA rubric in `references/qa-review.md`** and fix anything that fails before presenting.

---

## Agnostic by design

This skill must work for **any topic, any input, any output, any workspace, any user**.

**Input-agnostic.** The input can be a few keywords, a messy note dump, a list of links, a half-written page, or just the user's prompt. Treat whatever is provided as raw material; the workflow is the same.

**Output-agnostic.** The same content model renders to different targets. Decide the target from the request:
- **Notion** (default): write/update the page with the block syntax in `references/page-architecture.md`, then sync the database row.
- **PDF / document**: produce the same lean, compact structure as a clean document. Build it with the relevant document skill (e.g. the `pdf` or `docx` skill) from the same chapter model: meta + purpose block, chapters, summary bullets, content, tables, 2-column layouts where they save space, formatted links, image suggestions, and a sources section. Toggles collapse to clearly labeled sections (or a table of contents) in a PDF.
- The structure, depth, and formatting rules are identical across targets. Only the rendering mechanics differ. See `references/output-targets.md`.

**Workspace-agnostic.** Never hardcode category lists, property names, or database IDs. Always read them from the live schema. If the target database lacks a useful property (e.g. Scope, Reading Order), proceed with what exists and optionally suggest adding it (`notion-update-data-source`), but only with user consent.

**Language.** The library language (declared on the library home page or stated by the user), else the language of existing pages, else **English**. Established technical terms keep their standard form, usually English. An explicit request for one page overrides all of this.

---

## Reference files

Read these as needed; they hold the precise rules so output is identical every time.

- `references/writing-standards.md` - voice, formatting, visual structure, study-page rules.
- `references/page-architecture.md` - the page skeleton, templates, chapter structure, block syntax.
- `references/page-types.md` - chapter sets for Topic, Book summary and Language course pages.
- `references/index-completion.md` - gap analysis and cross-page conflict check for pages that already have an index.
- `references/notion-operations.md` - how to read/write Notion, schema detection, DB management, safe edits.
- `references/research-protocol.md` - source quality, dating, videos, images, depth bar.
- `references/classification.md` - Theory vs Practice vs Real Setup decision rules.
- `references/reformat-mode.md` - strict text-invariant restructuring rules.
- `references/output-targets.md` - how the content model renders to Notion vs PDF/doc.
- `references/media-assets.md` - verified policy for Mermaid, images by URL, generated charts, and videos.
- `references/qa-review.md` - the self-review rubric to run before presenting.
