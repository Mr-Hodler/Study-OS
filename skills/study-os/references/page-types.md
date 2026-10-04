# Page Types

One skill, three page types. The skeleton in `page-architecture.md` (meta callout, purpose callout, hook, chapters as headings, Glossary / Resources / Sources) applies to all of them. The type decides which chapters exist and what goes in them. These templates replace any platform template (Notion database templates, Confluence blueprints): the structure lives here, so it travels with the skill.

## Choosing the type

| Signal | Type |
| --- | --- |
| A concept, field, technology, method, market | **Topic** (default) |
| A book title, an author, a row in a book database, "riassunto", "summary of" | **Book summary** |
| A language name, "da zero a B2", a CEFR level, grammar, vocabulary, conjugations | **Language course** |

If the database itself is typed (a Book Library, a Languages section), the database decides. A hybrid (a book about a topic the library lacks) is a book summary that links to a topic page, never both in one page.

---

## Topic (default)

Use the standard architecture as written in `page-architecture.md`. Hubs get sub-page cards under `## Deep dives`; deep dives aim at real competence (`research-protocol.md` -> "Depth bar").

---

## Book summary

The goal is not to retell the book. It is to keep what changes how the reader thinks or acts, in a form that can be reread in ten minutes.

**Chapters, in order:**

1. **Card** (a 2-column block or a small table right after the purpose callout): author with one line on why they are credible, year, category, length (pages or audio hours), **In one sentence** (the thesis), **Read it if / Skip it if**.
2. `## The thesis in 60 seconds`: 3 to 5 bullets. The argument, not the table of contents.
3. `## Big ideas`: 3 to 7 ideas, each as an `### H3` with 💡 the idea, the mechanism or evidence the author gives, 💬 the book's own example (or a better real one), 🔑 how to apply it. Organise by idea, not by chapter: ideas are what gets remembered.
4. `## Chapter by chapter`: one table, `Chapter | Core point | Keep`. One line per cell. Long notes on a single chapter go in a toggle under the table.
5. `## Frameworks and models`: every named framework as a Mermaid diagram or a table. Skip the chapter if the book has none.
6. `## Quotes`: at most 5, verbatim, short (one or two sentences), each with chapter or page. Verify every quote with a search; an unverified quote is cut, never paraphrased into quotation marks.
7. `## Apply it`: a checklist of concrete actions. If the user's context is known (role, company, goals), tailor the actions to it.
8. `## Critiques and limits`: what the evidence does not support, what aged badly (dated), the strongest counter-argument, and the book that makes it.
9. `## Related`: other pages and books in the library (`<mention-page>`), plus one counterpoint book.

**Rules specific to books:**
- Summaries are in your own words. Never reproduce passages beyond the short quotes above.
- Sources: the publisher or author page, one serious review or critique, and a research source for any empirical claim the book makes.
- Database row: map author, year, category, language and a one-line description (the thesis) from the live schema. The reader's own state (read, listened, personal rating, owned formats) is **personal state**: never set or change it.

---

## Language course

Structure: one **hub** per language plus one **sub-page per CEFR level** (A1, A2, B1, B2 and above when asked). A whole course on one page is too long to use; Study Librarian Scaffold can create the level stubs.

**Hub chapters:**
1. `## The map`: a table, `Level | Can do (CEFR descriptor, short) | Grammar milestones | Vocabulary size | Guided hours`. Take hours and descriptors from an official source (Council of Europe CEFR, the language's exam body, Cambridge guided learning hours) and date them.
2. `## Deep dives`: the level sub-page cards.
3. `## How this language works`: the 5 to 8 structural facts that explain most of the grammar (gender, cases, verb system, word order, pronunciation rules), each contrasted with the learner's native language.
4. `## Study plan`: a weekly table (skill, minutes, resource) and the official exam per level (for example DELE, Goethe, Cambridge) with what it tests.
5. `## Resources`: a table, `Resource | Type | Level | Why`. Apps, podcasts, graded readers, channels, dictionaries. Formatted links only.

**Level page chapters:**
1. `## Can-do goals`: the CEFR descriptors for this level, as a checklist the learner can tick.
2. `## Grammar`: one `### H3` per point. Rule in one or two lines, a conjugation or declension **table**, 💬 3 example sentences with translation, ⚠️ the typical mistake for a speaker of the learner's native language.
3. `## Vocabulary by theme`: tables `Word | Translation | Example | Note (gender, irregularity, register)`. Frequency first: the words that cover most real text.
4. `## False friends`: a table against the learner's native language. Skip only if there are genuinely none worth knowing.
5. `## Pronunciation`: the sounds that do not exist in the native language, with a minimal pair each and a formatted link to an audio source.
6. `## Phrases for real situations`: tables per situation (travel, work, small talk) at this level.
7. `## Practice`: short exercises; **answers in a toggle** (this is exactly what toggles are for).
8. `## Checkpoint`: a self-test and the matching exam section.

**Rules specific to languages:**
- The learner's native language drives every contrast (false friends, typical mistakes, pronunciation). Read it from the page language or the user's profile; ask only if neither tells you.
- Long reference tables (full conjugations of irregular verbs) go in a toggle under the main table, not in the flow.
- Curiosities belong only if they help memory (an etymology that explains a spelling, a cultural rule that changes register). Otherwise cut them.
