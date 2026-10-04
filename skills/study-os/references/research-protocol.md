# Research Protocol

This is what separates Study OS from shallow AI writing. A page is not done until it is researched to expert depth with real, dated sources.

## Depth bar

- Cover the topic **A to Z**: definitions, why it matters, how to reason about it, the key frameworks, the trade-offs, the edge cases, and the current state of the art.
- Include the **full set of arguments** a knowledgeable person would expect. If an expert would ask "but what about X?", X must be addressed.
- Prioritize **insight and completeness** over word count. Dense, not padded.
- Present competing viewpoints fairly where the topic is contested; note the empirical disputes.
- **Deep-dive pages aim at real competence.** A reader should finish genuinely knowledgeable: the mechanism and the intuition behind it, why it works, the trade-offs, concrete numbers, named real examples, edge cases, and the common misconceptions. Use several diagrams and tables, not one. Cover every sub-topic the parent page implies; if a keyword from the source belongs here, it must appear.
- Depth without padding: add information, structure, or a visual, never filler sentences.

## The user's own material first

- Read what the user already has before searching the web: notes, links and attachments on the page, uploaded files, and files in connected storage (a Google Drive or similar connector: search by topic and title, read the matching files).
- Their material sets the angle and the vocabulary; the web fills the gaps and verifies the claims. Link to their files where they back a chapter.
- If the user mentions material in a storage that is not connected, say which connector would unlock it and continue with what is available.

## Sourcing rules

- Use web search to gather **authoritative, current** sources. Order of preference: primary sources and official documentation > standards bodies and peer-reviewed/industry references > reputable secondary analysis. Avoid low-quality or SEO-spam pages.
- **Always attach absolute dates** to anything time-sensitive: prices, regulations, software versions, market figures, leadership, "latest" claims. Write the date in the citation (e.g. "as of May 2026").
- For present-day facts (who holds a role, what something costs, current law/version), **search - do not rely on memory.** Facts drift.
- Embed every source as a hyperlink inside descriptive text. **No bare URLs.**
- Keep a short **Sources** section per chapter or at the page end. Optionally add a **Glossary** and a **Links** section.

## Media and visuals

- Surface 1–3 **high-quality videos** (lectures, talks, official walkthroughs) when they genuinely add value, embedded as descriptive links.
- Where an **image** would aid learning and Mermaid cannot draw it, place an image slot callout with a ready Google search query (`page-architecture.md`). Suggest the specific visual; never random stock images.
- Prefer a Mermaid diagram or a table over prose when explaining a process or system.
- When the learning is in manipulating numbers (a cost model, compounding, a sizing calculator), build an interactive artifact and link it from the page (`media-assets.md`).

## Theory vs Practice sourcing

- **Theory:** synthesize and explain in your own structured words, with sources backing claims. Reusable and evergreen.
- **Practice:** link to the best official guide rather than rewriting it, especially for install/operational/security steps or anything that must stay current. Add only the connective tissue and judgment the official guide lacks.

## Uncertainty

- When a fact is genuinely uncertain or sources conflict, state it plainly:
  `Uncertainty: [what is unclear] / Reduce via: [what source or test would resolve it]`
- Never fabricate a statistic, a quote, or a citation. If you cannot verify it, say so.

## Before writing

- For theory/educational pages, draft the **index of content** (chapters + one-line scope) and the intended **source list**, and confirm with the user, unless they asked for autonomous mode. This prevents wasted depth on the wrong structure.
- If the page already has an index, run `index-completion.md` instead of drafting from scratch.
