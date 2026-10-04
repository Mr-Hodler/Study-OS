---
name: study-os
description: >-
  Builds deep, expert-level study material from rough keywords, notes or an existing index, as pages or as
  a document. Use when the user says: build the study material, structure this study page, turn these notes
  into a study page, complete this index, what is missing from this page, research this topic and write it
  up, summarise this book, book summary, language course or grammar page, make a study PDF about X, deepen or
  expand this page, reformat this page, explain this concept, or points at a page, a database or a document
  for study, research, theory, notes, books or languages. Three page types: topic, book summary, language
  course. Finds gaps in an existing index and conflicts with other pages before writing. Produces dense,
  unpadded material with formatted links (never bare URLs), tables, columns, diagrams, examples, chapters as
  real headings, sources only where they add weight, and a synced database row. Input and output agnostic.
  Never uses em dashes.
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
- If no page exists yet, the user's prompt text IS the input.
- Note whether the page **already has an index** (chapter list, empty headings, title-only toggles). If it does, step 3 runs the index-completion checks.

### 2. Classify
- Decide the **page type** (Topic, Book summary, Language course) from `references/page-types.md`.
- Decide **Theory vs Practice** (and whether it's a hybrid). Theory = "why / how to reason"; Practice = "how to do it, step by step". Hybrid pages get two explicit sections. See `references/classification.md`.
- Map the topic to the database's category property values (read them from the schema; don't invent new ones unless asked).

### 3. Propose or complete the index
- **No index yet:** draft a chapter-level **index of content** (chapter titles + one-line scope each) and a short **source list**.
- **Index already there:** run `references/index-completion.md`: extract it verbatim, compare it with an expert reference syllabus (what is missing, misplaced, redundant, too broad), and search the library for pages that duplicate, overlap or contradict it. Present the amended index and the conflicts as two compact tables.
- Present in chat and ask for a quick confirm, UNLESS the user requested autonomous mode, in which case proceed directly.
- Chapters are never numbered unless there is a real numeric/priority order.

### 4. Research (this is what makes it deep)
- **The user's own material first:** notes and links on the page, attachments, uploaded files, and connected file storage (for example a Google Drive connector: search by topic, read the relevant files). Treat it as primary input and link to it. If the user says the material is in a storage they have not connected, say which connector would unlock it.
- Then web search for authoritative, current sources. Prefer primary sources, official docs, standards bodies, academic/industry references.
- Capture **absolute dates** for anything time-sensitive (prices, regulations, versions, leadership, stats).
- Collect: key facts, competing viewpoints, concrete numbers, a few high-quality videos, and the spots where a diagram, image, chart or interactive artifact would teach better than text.
- Full sourcing rules: `references/research-protocol.md`.

### 5. Write the page
- Build with the exact block syntax and architecture in `references/page-architecture.md` and `references/notion-operations.md`.
- Page skeleton (every page):
  - Meta callout (gray): `Last Updated` + `Related Pages` + **level** (beginner/intermediate/advanced) + **reading time**.
  - Purpose callout (blue): **Page Purpose** + **Non-scope** + signpost legend.
  - Intro hook paragraph.
  - **Sub-pages near the top** (for hubs): the child-page cards under `## Deep dives`. The cards ARE the index; never add a table repeating their titles.
  - `# Main Topic` then a horizontal rule, then `<table_of_contents/>`.
  - Chapters as **real `## H2` headings** (H3 for sub-points), each opening with a one-line hook then substance shaped to the material. Toggles only for minor/appendix detail, never a whole chapter.
  - Use the **signpost system** for soul and scannability: 💡 Key idea, 💬 Example, 🧩 Analogy, 🔑 Insight, ⚠️ Watch out, 🧭 Open question, 📚 Go deeper.
  - **Exploit Notion structure aggressively:** tables for comparisons/matrices/timelines, columns for parallel blocks, callouts for key points. A page of only bullets is under-built.
  - **Real visuals, not placeholders (see `references/media-assets.md`):** Mermaid code blocks for diagrams/schemas (render natively), `![alt](url)` for clean public images with attribution, a generated chart file + image slot, an interactive artifact when manipulating numbers teaches more than reading them, and a short `## Watch` video list. Never use `<image>`/`<embed>` tags.
  - **Image slots must be visible and actionable:** when a real image is needed, drop a yellow 🖼️ callout at the exact spot with **what** to add and a ready **"Search Google for: ..."** query, so the user finds and inserts it in one step.
  - **Per-chapter depth:** hook, 💡 key idea, substance, 💬 numeric example, ⚠️ misconception where one exists, 🧭 open question for meaty topics, 📚 go deeper.
  - A short **Sources** (and optional **Glossary** / **Links**) section at the end of each chapter or the page; cite generously where claims, data, or quotes appear.
- Hard style rules: **no em dashes** in your own writing; bold the label before a colon in bullets; embed links in descriptive text; gray=neutral, blue=insight, green=positive outcome.
- Write the content into Notion via `notion-update-page`. **Prefer surgical `insert_content` / `update_content` over full `replace_content`** to save tokens and avoid dropping preserved blocks; build new pages in one `create-pages` call (see `references/notion-operations.md`).
- For app-only tasks (uploading an image, converting a video to an embed, native database charts, a hand-drawn mind map), leave a **Notion handoff callout** rather than trying to do it via the API (see `references/media-assets.md`). Do not delegate core writing or diagrams to Notion AI.

### 6. Update the database
- Set/refresh the row's properties from the schema you read: title, category, scope (Theory/Practice), a 1-2 line content description, reading order, page URL, and an editorial page state if the schema has one.
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

**Language.** Default output language is **English**. When the target page or its database is already written in another language, match it. An explicit request from the user overrides both.

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
