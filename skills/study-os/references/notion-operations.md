# Notion Operations

How to read, write, and manage Notion safely and agnostically. The MCP tool names below use the Notion connector; the exact server prefix varies, so match on the operation name (fetch, search, create-pages, update-page, update-data-source).

## Read first, always

1. **Fetch the page** the user points to: `notion-fetch` with the page URL or ID. Read all existing keywords, notes, links, child pages, and structure. This is your input.
2. **Fetch the parent database** to learn the schema: `notion-fetch` on the database URL, then on the `collection://<data_source_id>` shown in the `<data-source url="...">` tag. The response includes the property schema and a SQLite table definition. **Read property names and option values from here. Never hardcode them.**
3. If a database has multiple data sources, pick the right `data_source_id` for the situation.

## Schema detection (agnostic)

Map the page to whatever properties actually exist. Typical study schemas include some of:
- A **title** property (may not be literally named "title" - use the schema).
- A **category / topic** multi-select (read its existing options; reuse them, don't invent).
- A **scope** select (e.g. Theory / Practice).
- A short **content description** text.
- A **reading order** number.
- A **done** checkbox.
- A **page URL** url property.
- System/readonly props (last edited time, owner) - never try to write these.

If a useful property is missing, proceed with what exists. Only add a property via `notion-update-data-source` (DDL `ADD COLUMN`) with explicit user consent.

## Writing content

Use `notion-update-page`:
- `insert_content` - append (or prepend with `position: start`) new blocks. Best for adding chapters to an existing page.
- `update_content` - search-and-replace specific snippets. Fetch the page first to get exact `old_str` to match.
- `replace_content` - replace the whole body. **Danger:** if the page has child pages/databases, they will be flagged for deletion. To preserve them, include them in `new_str` as `<page url="..."/>` / `<database url="..."/>`, or set `allow_deleting_content` deliberately. Prefer `insert_content`/`update_content` over wholesale replace on populated pages.

To create a brand-new study page under the database: `notion-create-pages` with `parent: { data_source_id }`, set `properties` from the schema, and put the body in `content` (do NOT repeat the title in content).

Always use the block syntax in `page-architecture.md`. Do not guess syntax; mirror a known good page if unsure.

## Edit efficiency (save tokens, reduce risk)

- **New page:** write it in a single `create-pages` call. Do not create empty then rebuild.
- **Existing page, small change:** use `update_content` (surgical search-and-replace) or `insert_content`. Re-sending the whole page as `replace_content` wastes tokens and forces you to re-include every preserved block (child pages, file attachments), which is where mistakes happen.
- **Reserve `replace_content`** for a genuine full restructure. When you must use it, include every child page (`<page url=...>`) and attachment (`<file src=...>`) in the new content so nothing is deleted.
- Prefer one well-planned write over several iterative rewrites of the same page.

## Database management

After the page content is written:
1. Set/refresh the row properties using the schema names you read:
   - title, category (from existing options), scope (Theory/Practice), 1–2 line content description, reading order, page URL, done.
   - Checkbox values use `"__YES__"` / `"__NO__"`.
   - Number properties are real numbers, not strings.
   - Properties literally named `id` or `url` must be prefixed `userDefined:` (e.g. `userDefined:URL`).
   - Date properties split into `date:{prop}:start`, optional `date:{prop}:end`, `date:{prop}:is_datetime`.
2. Keep **reading order** coherent with siblings if the property exists.
3. Enforce **anti-duplication**: if a sibling covers part of the topic, record the difference in Non-scope / Related Pages instead of duplicating content.
4. **Learning workflow (if the schema has them):**
   - **Status** (To learn / Learning / Reviewed / Mastered): set when a page is created or studied.
   - **Next review** (date): set a spaced interval after study (Learning -> a few days, Reviewed -> ~2 weeks, toward Mastered -> ~1 month). A daily scheduled task can surface pages due for review.
   - **Prerequisites** (self-relation): link a page to the study items it should be read after, building a prerequisite graph across the library. Mirror this in the page's intro callout ("Read after Part X").

## Knowledge graph linking

Pages should not be islands. Connect them:
- **Related** lines in the purpose callout for sibling/overlapping pages.
- **Prerequisites** relation in the database for ordered dependencies.
- Inline `<mention-page url="..."/>` links wherever one page references a concept that lives in another. A well-linked library is itself a study aid.

## Safe-edit checklist

- Fetched the page and the schema before writing? 
- Preserving existing child pages on any replace?
- Property names taken verbatim from the live schema?
- Not writing to readonly/system properties?
- Re-fetch after large edits to verify the result rendered as intended.
