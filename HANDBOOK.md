# Study OS Handbook

`README.md` presents the system to someone discovering it. This file is the operating manual: open it when you are about to run one of the two skills and want to know what it will actually do, what it needs from you first, and what it will hand back. Both entries carry the same fields in the same order, so you only learn the shape once; a **Known wrinkle** line appears only where a skill's own files disagree with each other. The `SKILL.md` under `skills/<name>/` remains the full spec, and the `references/` folders hold the rules it enforces.

---

## The two skills

| Skill | Question | Unit of work | Modes | What it writes |
|---|---|---|---|---|
| `study-os` | What does this one topic look like written up properly, researched and sourced? | one page | Build (default) · Reformat · Explain · Refresh | the page body (chapters, tables, diagrams, sources) and that page's own database row |
| `study-librarian` | Is the collection coherent, and where in it does this topic live? | the database as a collection | Audit (default) · Find · Map · Organize · Scaffold · Dedupe | metadata, the prerequisite and related graph, the index page, hub and stub pages |

**The test.** If the change lands inside a page's chapters, it is `study-os`; if it lands between pages, in the metadata, the links, the index or the stubs, it is `study-librarian`.

The split is not by where the work happens. Both point at the same Notion database, both read its schema at runtime the same way, both create pages. It is by what gets written. `study-librarian` edits properties, Related and Non-scope lines and inline page mentions inside page bodies, and in Scaffold and Map modes it creates whole pages; what it never writes is a chapter. `study-os` writes chapters and syncs the one row belonging to the page it just built; what it never does is reason about the collection. They touch the same knowledge graph at two different scopes: `study-os` connects the page it is finishing, `study-librarian` maintains connectedness across every page and reports the ones with no links in or out. Only `study-os` researches: the Librarian's Find mode searches the library, not the web, and its gap list is judgement over the existing category structure.

---

## `study-os`

**Question.** What does this one topic look like written up properly: researched to expert depth, chapter by chapter, with dated sources and the architecture every page gets?

**Reach for it when**
- A Notion page holds keywords, links and half-finished thoughts, and you want the real page (Build).
- You have nothing but a topic and a prompt, and want a page created under the database (Build).
- A `study-librarian` stub is sitting there waiting to be filled (Build).
- The words are fine and the layout is a wall of text (Reformat).
- Time-sensitive facts on an existing page have aged: prices, versions, laws, who holds a role (Refresh).
- You want the concept explained in chat with nothing written (Explain).

**Not for** anything about the collection rather than the page, which is `study-librarian`: auditing consistency across pages, finding where a topic already lives, bulk metadata, the prerequisite graph, the index page, duplicates, or turning a curriculum into a skeleton. **Not for** a Real Setup page (how *your* system is configured today): `classification.md` places that outside the study library entirely, in a separate ops space, and says to reference where it lives instead. **Not for** the four app-only jobs (uploading an image, converting a video link into a player embed, native database charts, a hand-drawn mind map); it leaves a precise handoff callout rather than attempting them through the API. **Not** a wrapper around Notion AI: `media-assets.md` forbids routing core writing or diagrams there, because that reintroduces the shallow, inconsistent output this skill exists to replace.

**Needs.** Required: a target, which is a Notion page URL or ID, a database to create under, or nothing at all, in which case your prompt text *is* the input; the Notion connector, since the schema is read at runtime and never assumed; and, for theory pages, your confirmation of the proposed chapter index and source list before writing, unless you say "autonomous" or "just go". Reformat and Refresh need an existing page. Better with: whatever raw material is already there, because keywords, dumped notes and half-finished thoughts are treated as input rather than as something to overwrite; an explicit target when it is not Notion ("as a PDF", "printable"); and a schema carrying category, scope, reading order, content description and page URL, though it proceeds with whatever exists and adds a property only with your consent. Upstream, the one artefact it consumes is a stub page scaffolded by `study-librarian`.

**Returns.** Notion is the default target: the page written or updated in place against a fixed skeleton. Gray meta callout (Last Updated, Related Pages, level, reading time), blue purpose callout (Page Purpose, Non-scope, the signpost legend), an intro hook, for hubs a `## Deep dives` sub-page index near the top, then `# Topic`, a horizontal rule, a table of contents, chapters as real `## H2` headings, and page-level `## Glossary`, `## Resources` and `## Sources`. The database row is then synced: title, category from the existing options, scope, a one or two line content description, reading order, page URL, done, and where the schema has them Status and Next review. Alongside the page: Mermaid diagrams inline, yellow image-slot callouts at the exact spot each visual belongs, any chart it generated as a PNG or SVG file for you to drag in, a short `## Watch` list of one to three videos, and handoff callouts for the app-only tasks. The PDF or document target renders the same content model through the `pdf` or `docx` skill, with toggles collapsing into clearly labeled sections or a table of contents. Explain mode returns chat only and edits nothing.

**How it works.** Build runs seven steps in order: read the target and its schema, classify Theory against Practice (a hybrid gets two explicit sections), propose the index and source list, research, write, sync the row, sweep. Three rules make the output different from a generic write-up of the same topic. **Depth is a bar, not an aspiration**: cover the topic A to Z, and if an expert would ask "but what about X?", X must be addressed, with absolute dates on anything time-sensitive, present-day facts searched rather than recalled, and no fabricated statistic, quote or citation; where sources conflict the page prints `Uncertainty: [what is unclear] / Reduce via: [what would resolve it]` instead of quietly picking a side. **A correct page that reads like a generated template is a failure**: the skeleton is fixed but the shape inside each chapter follows the material (a comparison becomes a table, a debate becomes two short positions, a process becomes steps), chapters open on a hook rather than "This chapter covers", and the signpost system (key idea, example, analogy, insight, watch out, open question, go deeper) carries the personality, which lives in framing and selection and never in extra words. **A diagram that can be Mermaid must be Mermaid**, never a text placeholder: an external image URL is treated as unreliable because many hosts block hotlinking and the block then renders as a blank box, so the fallback is a generated file plus a visible yellow slot carrying a ready "Search Google for: ..." query at the exact spot. Two mechanics sit under all of it. The schema is detected at runtime from the `collection://` data source, so no property name, category option or database ID is ever hardcoded and the skill works in any workspace. And edits are surgical: `insert_content` and `update_content` in preference to `replace_content`, which flags child pages and attachments for deletion unless every one of them is re-included in the new body. The last step is not optional. The full `qa-review.md` rubric runs as a gate before anything is presented, including a scan of the entire output for em dashes, and the page is re-fetched to confirm that tables, columns, Mermaid and page cards actually rendered.

**Feeds.** `study-librarian`: every page it writes becomes a row to audit, map, link and dedupe, and every Non-scope and Related line it sets is a node in the graph the Librarian maintains. The `pdf` and `docx` skills, when the target is a document. And itself, through Refresh, which re-verifies only the dated facts on a page written earlier and updates just those.

**Known wrinkle.** The mode table is introduced as "three modes" and lists four. `output-targets.md` is out of step with the rest of the skill: it says "Chapters are toggle headings", shows a `<details><summary>` block as the Notion form for a chapter, and describes every chapter as "Summary bullets and dense Content". All three contradict `page-architecture.md`, `writing-standards.md` and `qa-review.md`, which require chapters to be real `## H2` headings, reserve toggles for minor or appendix content, and explicitly reject repeating one Summary/Content skeleton per chapter. `page-architecture.md` also ranks an image by URL from Wikimedia second in its order of preference, where `media-assets.md` names Wikimedia as the host that most often renders blank. And the frontmatter claims the skill "manages the underlying study database" and triggers on "add a study entry" and "update my study index", which is `study-librarian` territory.

---

## `study-librarian`

**Question.** Is the collection coherent: where does this topic live, what is missing, orphaned or duplicated, and what does the whole thing look like laid out?

**Reach for it when**
- You cannot remember whether a page exists ("do I have anything on vector databases?") (Find).
- You want the collection checked before or after a run of builds (Audit).
- Metadata has drifted: categories unset, reading order colliding, descriptions stale, prerequisites unlinked (Organize).
- You want one page that maps the library, with the dependency graph and the orphans and gaps named (Map).
- You have a curriculum or a ten-module plan and want the empty structure before any writing happens (Scaffold).
- Two pages have grown into the same ground (Dedupe).

**Not for** writing or deepening the content of a page, which is `study-os`; if a request turns out to be about authoring, the skill says so and points there rather than rewriting chapters itself. **Not for** your learning state: `Status` and `Next review` are read where useful and never changed. **Not for** quizzes, flashcards, spaced repetition or study plans, which are out of scope by name. **Not for** deleting or merging anything without explicit confirmation.

**Needs.** Required: the study database, given as a URL or taken as the one `study-os` already writes to, and the Notion connector, since the schema is read the same way at runtime (fetch the database, then the `collection://<data_source_id>` from its data-source tag). Scaffold needs the plan: a list of modules, an existing outline, or at minimum the subject. Dedupe and any merge need your confirmation before anything is acted on. Better with: a schema carrying Category, Scope, Reading Order, Content description and a Prerequisites self-relation, since a missing one is worked around and only added with consent. Upstream, the material it curates is the set of pages `study-os` wrote.

**Returns.** What you get depends on the mode. Audit and Find return chat and change nothing; Map, Organize and Scaffold write; Dedupe proposes and acts only on confirmation.

- **Audit**: a prioritized report grouped blocker, should-fix, nice-to-have, per page, each finding carrying the page link and a one-line fix, closing with an offer to run Organize on the metadata and link issues and to hand the content gaps to `study-os`.
- **Find**: the matching page links, or a plain statement that nothing covers it, which is a gap, plus an offer to scaffold it.
- **Map**: one overview page built or refreshed, with pages grouped by category and listed in reading order, a Mermaid flowchart of the prerequisite relations, and explicit lists of orphans and gaps. The map page itself is held to the Study OS page standards.
- **Organize**: edits in place to category (from the existing options), scope, reading order coherent across siblings, a sharp one or two line content description and page URL, plus the Prerequisites relation and the Related lines and page mentions inside page bodies.
- **Scaffold**: a hub page (meta callout, purpose and non-scope callout, a `## Deep dives` section for the sub-page cards) and one stub page per planned item, each with a title, a meta callout, a one-line purpose and a `## To be written` note, with category, scope, reading order and prerequisite links already set.
- **Dedupe**: proposals, naming which page to keep and which to merge or archive, or a clean scope split written through Non-scope and Related lines.

**How it works.** Every mode opens the same way: fetch the database, read the live schema, enumerate the rows and their child pages, and build the picture of title, category, scope, reading order, description, URL, prerequisites, related links and which page links to which. Three rules make this different from running a spellcheck across a folder. **A library is a graph, not a pile**: every page must be reachable through a category, a prerequisite or a related link, a page with no links in or out is reported as an orphan, and gaps (the topics a complete library on this subject would be expected to have and does not) are first-class findings reported alongside them rather than an afterthought. **The material and learning boundary is absolute**: it curates the pages and their organization, and `Status` and `Next review` stay untouched even in Organize mode, because they are the user's state and not the library's. **Destructiveness is tiered by mode**: Audit, Find and Map never change page content, Organize edits metadata and links and never chapters, Dedupe and merges require confirmation and preserve child pages and attachments, and every change is re-fetched to verify it applied. Two more things worth knowing. Scaffold and Dedupe are inverses, one growing a planned library and the other collapsing an over-grown one, and Scaffold's stubs are deliberately empty of deep content because the Librarian builds the frame and `study-os` fills it. And `audit-checklist.md` has Audit checking things no Librarian mode is allowed to fix: em dashes outside verbatim quotes, chapters buried in toggles, a missing Sources section, blank image boxes left by failed URL embeds, inconsistent signposts. That is by design. Those findings route to `study-os`.

**Feeds.** `study-os`, in both directions: audit findings become build or deepen jobs, gaps become new pages, and scaffolded stubs are the pages it fills. The typical loop is Scaffold, then `study-os` on each stub, then Audit and Map on the result.

**Known wrinkle.** `README.md` names four modes (Audit, Organize, Map, Dedupe) where `SKILL.md` defines six. Find and Scaffold are missing from that list even though the README's own usage section describes both.

---

## The reference files

The `references/` folders are where the operating rules live. The two `SKILL.md` files carry the workflow and route to them. Open one when you are about to do the thing it governs.

| File | Open it when |
|---|---|
| `study-os/references/writing-standards.md` | Before writing any page. Voice, the soul rules, the signpost system, the em-dash ban, the decision rule between tables, bullets, columns and diagrams, and the Page Purpose / Non-scope / Related discipline. |
| `study-os/references/page-architecture.md` | You are about to emit blocks. The skeleton in order, what a strong chapter contains, and the exact Notion-flavored syntax for callouts, tables, columns, mentions, the table of contents and toggles. |
| `study-os/references/research-protocol.md` | Before the research pass. The depth bar, the source hierarchy, absolute dating, the uncertainty formula, and the index confirmation that precedes writing. |
| `study-os/references/notion-operations.md` | Any read or write against Notion. Schema detection from `collection://`, which write call to use and why `replace_content` is dangerous, the property-writing quirks (checkbox values, the `userDefined:` prefix for properties named `id` or `url`, split date fields), and the knowledge-graph links. |
| `study-os/references/classification.md` | You have to decide how a page is written. Theory against Practice against Real Setup, the ten-second test, hybrid pages, and the anti-duplication rule. |
| `study-os/references/media-assets.md` | A visual is needed. The decision table across Mermaid, image by URL, generated file and video, the image-slot and handoff callout patterns, and the hotlinking reality check. |
| `study-os/references/output-targets.md` | The target is a PDF or a document rather than Notion. The shared content model and the element-by-element mapping. |
| `study-os/references/reformat-mode.md` | Running Reformat. Text invariance, what may and may not change, and the one place the no-em-dash rule yields to it. |
| `study-os/references/qa-review.md` | Before presenting anything. The final gate, run in full. |
| `study-librarian/references/library-operations.md` | Any Librarian mode. Reading the library, metadata hygiene, the two graph layers, deduplication, the map page, and the scaffolding procedure. |
| `study-librarian/references/audit-checklist.md` | Running Audit. The per-page structure, hygiene and metadata checks, the library-level checks, and the report format. |

One thing to know about the split. `study-librarian` states in its own principles that it shares the Study OS writing and structure standards, `library-operations.md` requires the map page to meet them, and `audit-checklist.md` checks items those standards define: em dashes, chapters as real headings, signposts, Non-scope lines. Both of those standards files live under `skills/study-os/references/`, so a Librarian installed on its own does not ship the rules it audits against. Read the Study OS pair alongside it.
