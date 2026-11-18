# Notion Operations

How to read, write and manage Notion safely and agnostically. Tool names follow the Notion connector; the server prefix varies, so match on the operation (fetch, search, create-pages, update-page, update-data-source, create-file-upload, create-attachment).

## Read first, always

1. **Fetch the page** the user points to. Every keyword, note, link and child page on it is input.
2. **Fetch the parent database**, then its `collection://` data source: property names, option values and the SQLite table come from there. **Never hardcode them.**
3. **Fetch the library home** (the page that contains the study database) once per session: it carries the library conventions below.
4. If a database has several data sources, pick the right one.

## Library conventions

Some rules belong to the whole library, not to one page. They live once, on the library home page, in a toggle named "Legend and conventions" (create it if missing, with the user's consent):

- **Signpost legend:** the emoji and their meaning. Pages use the signposts without repeating the legend.
- **Library language:** the language study pages are written in. Established technical terms stay in their standard form (usually English: qubit, hash, smart contract, signature, mempool) even when the page is in another language. If the home page does not say, follow the user's stated preference, then the language of existing pages, then English.
- **Macro-topics:** the category options of the study database. They are the single taxonomy for Notion and for file storage.
- **Drive mirror (optional):** one folder per macro-topic in the user's study folder, named like the category (a numeric prefix such as `22_` is allowed and ignored when matching). A table on the home page maps category to folder when names differ. Per-page subfolders are created on demand, named like the page, and hold the page's own material and generated assets.

Study OS reads these conventions; Study Librarian owns and maintains them.

## Schema detection (agnostic)

Map the page to whatever properties exist. Typical study schemas include some of:
- a **title**; a **category** multi-select (reuse its options); a **scope** select (Theory / Practice); a short **content description**; a **reading order** number; a **prerequisites** self-relation; an editorial **page state**.
- **Personal state** (never written): learning status, review dates, done or read checkboxes, personal ratings, owned formats.
- **System or read-only** properties (last edited time, created by): never written.

A page with two natures takes two categories (for example a STEM topic with a Bitcoin vertical: the STEM category plus the Bitcoin category). Never invent an option; propose it to the user, and to Study Librarian for the taxonomy.

If a useful property is missing, proceed with what exists. Add or change properties (`notion-update-data-source`) only with explicit consent.

## Writing content

`notion-update-page`:
- `update_content`: search-and-replace exact snippets from a fresh fetch. Best for targeted edits.
- `insert_content`: append, or prepend with `position: start`.
- `replace_content`: the whole body. **Danger:** child pages and databases not included as `<page url="...">` / `<database url="...">` tags are flagged for deletion. Include every one, never set `allow_deleting_content` without the user's consent.

New pages: one `notion-create-pages` call with the full body. Under a database, use its data source as parent and set the properties from the schema. A vertical or deep dive is a child page of its core page (parent `page_id`); it is not a database row.

Use the block syntax in `page-architecture.md`. If a fetch shows a syntax you have not seen, mirror it.

## Edit efficiency

- **New page:** a single create call, never empty-then-rebuild.
- **Existing page, small change:** `update_content`. Re-sending a whole page wastes tokens and is where child pages get lost.
- **`replace_content`** only for a genuine restructure, with every `<page>` and file tag preserved.
- **Moving content into a new child page:** create the child page first, then remove the moved blocks from the parent with `update_content`, then re-fetch both.
- Child pages created through the API appear at the bottom of the parent. To show the card where it belongs, move the `<page url>` tag with one `update_content` that deletes it at the bottom and inserts it in place (same call, so it is a move, not a deletion).
- **After a `<page>` card**, start the next block with a heading or a paragraph, never a bare list item.

## Database management

After the content is written, update the row from the live schema: title, category, scope, a 1 to 2 line content description, reading order coherent with siblings, page URL if tracked, editorial page state, prerequisites. Formats: checkboxes `"__YES__"` / `"__NO__"`; numbers as numbers; properties named `id` or `url` prefixed `userDefined:`; dates as `date:{prop}:start`.

Anti-duplication: if a sibling covers part of the topic, record the split in Non-scope and Related, never copy the content.

## Database structure checks

When a database is touched for the first time in a session, glance at its structure and report (do not fix without consent):
- options that mix two concepts in one tag (a topic and a technology, a topic and a type);
- a type used as a category (for example "Guide" as a category when a Scope property exists);
- redundant properties (a Page URL property on rows that are pages; two checkboxes meaning the same state);
- select properties with a single option;
- untitled or empty rows;
- macro-topics without a matching Drive folder, or folders without a category.

Structural fixes belong to Study Librarian (Organize).

## Knowledge graph linking

- **Related** lines in the purpose callout for siblings.
- **Prerequisites** relation for ordered dependencies.
- **Inline mentions** wherever a page refers to a concept owned elsewhere.
- **Verticals** linked from both sides: the core lists the vertical card; the domain hub mentions the vertical.

## Safe-edit checklist

- Fetched page, schema and library home before writing?
- Every child page preserved on any replace?
- Property names verbatim from the live schema; personal state untouched?
- Re-fetched after large edits to verify rendering?
