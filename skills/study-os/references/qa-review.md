# QA Self-Review

Run this pass before presenting any page. It is the final gate; do not skip it. Fix anything that fails, then re-fetch the page to confirm it rendered.

## Depth and substance
- [ ] Every chapter has a 💡 key idea and at least one concrete, often numeric, example.
- [ ] The hard or commonly-misunderstood points are expanded, not glossed.
- [ ] Misconceptions (⚠️) and open questions are surfaced where they exist.
- [ ] No generic, encyclopedia-flavored filler. Personality lives in framing, not padding.

## Structure
- [ ] Sub-pages index is near the TOP (table or 2-column), with the live page cards.
- [ ] Chapters are real `##` headings, not toggles. Toggles only for minor/appendix content.
- [ ] The shape varies per chapter (table, columns, steps, two positions) and fits the material.
- [ ] Tables used for comparisons/matrices/timelines; columns for parallel blocks.

## Visuals
- [ ] Diagrams that can be Mermaid ARE Mermaid (not a text placeholder).
- [ ] Any embedded image uses `![alt](url)` with a clean public source and attribution.
- [ ] Where a precise chart is needed, the asset was generated and an image slot marks the spot.
- [ ] A "Watch" list exists when good videos add value.

## Sources and accuracy
- [ ] Claims, data, quotes, and contested points are cited; volatile facts are dated.
- [ ] Links are formatted descriptive text, never bare URLs.
- [ ] No fabricated statistics, quotes, or citations. Uncertainty stated plainly where it exists.

## Style
- [ ] Zero em dashes (—) anywhere except verbatim quotes. Scan and remove.
- [ ] Signposts used consistently: 💡 💬 🔑 ⚠️ 📚.
- [ ] Bold label before a colon in bullets; consistent heading hierarchy.
- [ ] English by default unless the user asked otherwise.

## Database and metadata
- [ ] The Study Index row is updated: title, category, scope, description, and (if present) Status and Next review.
- [ ] Page meta shows Last Updated, level, and reading time.
- [ ] Non-scope and Related lines prevent overlap with sibling pages.

## Final
- [ ] Re-fetched the page and confirmed tables, columns, Mermaid, and page cards rendered as intended.
