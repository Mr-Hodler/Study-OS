# Audit Checklist

What the Audit mode checks across the library. Audit is read-only: it reports, it does not fix. Group findings by severity (blocker / should-fix / nice-to-have) and by page.

## Per-page structure
- [ ] Has a meta callout (Last Updated, and level/reading time if used).
- [ ] Has a purpose callout with Page Purpose and Non-scope.
- [ ] Chapters are real headings, not a wall of toggles.
- [ ] Has a Sources section where claims/data/quotes appear; volatile facts are dated.
- [ ] Uses the signpost system consistently (key idea / example / insight / watch out / go deeper).

## Per-page hygiene
- [ ] No em dashes (—) outside verbatim quotes.
- [ ] No bare URLs; links are descriptive text; no dotted-domain link labels.
- [ ] No blank image boxes (failed external image embeds); diagrams use Mermaid where possible.
- [ ] No leftover placeholders, test blocks, or broken links.
- [ ] Headings consistent; one bullet style per section.

## Per-page metadata
- [ ] Category set from existing options; Scope set; Reading Order present and coherent.
- [ ] Content description present and accurate (1 to 2 lines).
- [ ] Page URL set if the schema tracks it.
- (Do not flag or change Status / Next review: out of scope.)

## Library-level
- [ ] No **orphans** (pages with no category and no prerequisite/related link).
- [ ] No **duplicates** or heavy unintended overlap between pages.
- [ ] Reading Order has no gaps or collisions within a category/series.
- [ ] Prerequisite graph is acyclic and matches the "read after" notes in page intros.
- [ ] Hub/index pages link to all current pages; no dead or missing cards.
- [ ] Obvious **gaps**: expected topics for this subject that no page covers.

## Output
- A prioritized, scannable report: blockers first, then should-fix, then nice-to-have, each with the page link and the one-line fix.
- Offer to run **Organize** to fix the metadata/link issues, and to hand content gaps to **Study OS**.
