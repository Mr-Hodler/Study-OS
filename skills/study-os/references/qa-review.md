# QA Self-Review

Run this pass before presenting any page. It is the final gate; do not skip it. Fix anything that fails, then re-fetch the page to confirm it rendered.

## Depth and substance
- [ ] Every chapter has a 💡 key idea and at least one concrete, often numeric, example.
- [ ] The hard or commonly-misunderstood points are expanded, not glossed.
- [ ] Misconceptions (⚠️) and open questions are surfaced where they exist.
- [ ] Protocols, attacks and flows are told with actors (Alice, Bob, Eve, Mallory) and drawn.
- [ ] No generic, encyclopedia-flavored filler. Personality lives in framing, not padding.

## Density and coverage
- [ ] Cut pass done: every sentence carries a fact, number, mechanism, example, decision rule or warning.
- [ ] No banned filler phrases, no recap paragraphs, no idea stated twice.
- [ ] Every index item, every keyword from the source, and every note the user wrote is covered on the page.
- [ ] Gaps and conflicts were checked against the library (`index-completion.md`) and the conflicts were reported or fixed on this page.
- [ ] The page type's chapter set is complete (`page-types.md`).

## Structure
- [ ] No signpost legend on the page (it lives on the library home page).
- [ ] The table of contents sits inside a collapsed "Contents" toggle, not as a full-width block.
- [ ] Topic and hub pages open with a concept map.
- [ ] Hub sub-pages sit near the top as live cards under `## Deep dives`, with no duplicate title table.
- [ ] Core chapters are domain-agnostic; domain material lives in vertical child pages listed under `## Verticals`.
- [ ] Chapters are real `##` headings, not toggles. Toggles only for minor content.
- [ ] Every chapter longer than three lines has a visual element (table, columns, diagram, image).
- [ ] The closing block is in columns (Glossary | Watch + Resources), Sources below.

## Visuals
- [ ] Diagrams that can be Mermaid ARE Mermaid.
- [ ] Needed images were uploaded (generated or found with a licence), each with a caption and source.
- [ ] Any image slot left is justified in the report.
- [ ] A Watch list exists when good videos add value.

## Sources and accuracy
- [ ] Claims, data, quotes and contested points are linked **in the sentence** where they appear; volatile facts are dated.
- [ ] Links are formatted descriptive text, never bare URLs.
- [ ] No fabricated statistics, quotes or citations. Uncertainty stated plainly where it exists.

## Style
- [ ] Zero em dashes (—) anywhere except verbatim quotes. Scan and remove.
- [ ] Signposts used consistently: 💡 💬 🧩 🔑 ⚠️ 🧭 📚.
- [ ] Bold label before a colon in bullets; consistent heading hierarchy.
- [ ] Language: the library language; standard technical terms kept in their usual (often English) form.

## Database and metadata
- [ ] The database row is updated: title, categories (two when the page spans two macro-topics), scope, description, editorial page state if present.
- [ ] Personal state untouched: learning status, review dates, done/read/listened, ratings, owned formats.
- [ ] Page meta shows Last Updated, level, and reading time.
- [ ] Non-scope and Related lines prevent overlap with sibling pages; verticals are linked from their domain hub.

## Final
- [ ] Re-fetched the page and confirmed tables, columns, Mermaid, images and page cards rendered as intended.
