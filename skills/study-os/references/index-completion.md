# Index Completion: gaps and conflicts

When the target page already has an index (a list of chapters, headings with no body, toggles with titles only, a "Deep dives" list, or notes that imply a structure), do not just fill it. An index written before studying the topic is a guess: it usually misses what the reader does not yet know exists, and it often repeats what another page already covers. Run these three checks first, then fill.

## 1. Extract the index as written

- Copy every item verbatim, in the user's order, with any notes under it. These notes are raw material and must end up inside the right chapter, never dropped.
- Keep the user's wording and order unless a gap or conflict below justifies a change.

## 2. Gap analysis (what is missing from the index)

Build the reference syllabus an expert would expect, from 2 or 3 authoritative structures for this subject: a university course outline, a certification body of knowledge, an official exam syllabus (CEFR for languages), the table of contents of the canonical textbook. Then compare item by item:

| Finding | Meaning | Default action |
| --- | --- | --- |
| **Missing, core** | an expert would call the page incomplete without it | add a chapter |
| **Missing, useful** | adds real value for this reader's goal | add, or a section inside a chapter |
| **Misplaced** | comes before its prerequisite | move |
| **Redundant** | two items are the same thing | merge |
| **Out of scope** | belongs to another page | link, do not write |
| **Too broad** | one item hides a whole field | split into a sub-page |

Name the reference syllabus used, so the user can judge the comparison.

## 3. Conflict check (against the rest of the library)

- Search the study database and the workspace for each chapter's key terms (title search plus full-text search). Read the hits.
- Classify each hit:

| Conflict | Example | Action |
| --- | --- | --- |
| **Duplicate** | another page already covers the chapter fully | link to it from this page, write a two-line summary at most |
| **Overlap** | partial coverage elsewhere | decide which page owns it; the other gets a summary plus a link; record it in Non-scope |
| **Contradiction** | different numbers, definitions or claims | verify with sources, write the correct version here, report the other page with the fix |
| **Terminology clash** | the same term defined two ways | align with the library's existing definition unless it is wrong |

- Never edit the other pages from here. Report them; the user or Study Librarian (Dedupe, Organize) fixes them.

## 4. Present, then fill

Show in chat, compact:
- the amended index as a table, `Item | Action (keep / add / move / merge / split / link / drop) | Why (one line)`;
- the conflicts table, `Page | Conflict | Proposed fix`.

Wait for a confirm unless the user asked for autonomous mode. Then write the chapters in the agreed order, absorbing the user's original notes. The gap and conflict tables stay in chat: they are working material, not page content. On the page they survive only as the Non-scope and Related lines.
