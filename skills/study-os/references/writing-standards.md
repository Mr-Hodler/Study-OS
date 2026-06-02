# Writing Standards

These are the non-negotiable rules for voice, formatting, and visual structure. They are derived from a working Notion study system and generalized so any user can apply them. Read this before writing any page.

## Voice

- Methodical, data-driven, evidence-based. Active voice. Maximum information density.
- Short paragraphs with clear hierarchy. No filler, no redundant phrases, no courtesy padding.
- Address the core request immediately. Every word serves a purpose.
- Analytical, but creative when it helps. Suggest improvements; say when something is wrong and offer an out-of-the-box alternative.
- **Concise is not shallow.** Depth, completeness, and insight are required. Avoid generic, low-quality writing at all costs.

## Soul: make pages feel alive

A correct page that reads like a generated template is a failure. Pages must have a point of view and a human rhythm. Rules:

- **Open with a hook, not boilerplate.** The first line of a chapter should say why this matters or frame a tension, then deliver the substance. Avoid "This chapter covers..." openings.
- **Vary the structure.** Do not repeat an identical "Summary / Content" skeleton in every chapter. Let the shape follow the material: a comparison becomes a table, a process becomes numbered steps, a debate becomes two short positions, a definition-heavy topic becomes tight bullets.
- **Use a consistent signpost system** so readers know what they are looking at. Recommended icons, used as inline bold labels or small callouts:
  - 💡 **Key idea** - the core insight in one or two lines.
  - 💬 **Example** - a concrete, real example or mini-scenario.
  - 📚 **Go deeper** - sources and the deep-dive sub-page.
  - 🔑 **Insight / rule of thumb** - a sharp takeaway worth remembering.
  - ⚠️ **Watch out** - a common mistake, risk, or misconception.
- **Write like an expert talking to a smart peer**, not an encyclopedia. Confident, concrete, occasionally opinionated where the field has a clear consensus. Name the debate where it is genuinely contested.
- **Concrete beats abstract.** Prefer a real number, a named tool, a dated event, or a worked example over a generic statement.
- This soul layer never excuses padding. Stay dense; personality lives in framing and selection, not in extra words.

## Visual structure

- Open each page with a **callout block (blue background)** stating purpose and context.
- Put a **horizontal rule** after the H1 to separate major sections.
- **Never use an em dash (—) anywhere, in any output, in any mode.** Not in Notion pages, not in PDFs/documents, not in chat. Replace with a comma, a colon, parentheses, or split into two sentences. The only exception is verbatim quoted source text, which is preserved exactly; do not introduce em dashes of your own.
- Heading hierarchy is strict: **H1** = main topic, **H2** = subsections, **H3** = details.
- **Do not number titles or chapters** unless the items have a real numeric/priority order.
- Embed hyperlinks inside descriptive text. **No bare URLs.** Also avoid putting a dotted domain (e.g. "Distill.pub", "arxiv.org") in the visible link text: Notion auto-links it and creates a broken double-link. Use plain words like "Distill" or "the arXiv paper".
- Cite sources whenever referencing official data, statistics, or academic/industry material.
- Apply color coding consistently: **gray** = neutral info, **blue** = insight, **green** = positive outcome/recommended practice.
- Keep similar content types (frameworks, processes, analyses) in the **same format** every time.

## Tables vs bullets vs columns vs diagrams (decision rule)

- **Table** - comparing 3+ options or 3+ dimensions, or when the reader scans values across rows/columns.
- **Bullet list** - principles, checklists, narrative guidance.
- **Diagram / flowchart** - when the goal is to explain a process, sequence, or system interaction.
- **2 columns** - to save space when a section has only a little content (a short heading + 2–6 bullets) and it splits cleanly without changing words. Do not split a single logical sequence across columns. Limit to 2 columns unless 3+ is already intentional.

## Bullet formatting

- When a bullet uses a colon, **bold the label before the colon**. Example: `**Definition:** ...`.
- Use toggles for supplementary/deep-dive/appendix content that supports but isn't essential to the main flow.
- One idea per block. Prefer several short blocks over a wall of text.

## Examples, deep-dives, and sources discipline

- **Always include concrete examples.** An abstract claim is not learned until it is grounded. Add a worked example, a mini-scenario, or a "for instance" wherever a concept is non-obvious.
- **Deep-dive the hard parts.** When a point is genuinely complex or commonly misunderstood, expand it: the mechanism, the edge cases, the trade-offs, the common mistake. Put long deep-dives in a toggle so the main flow stays lean.
- **Sources only where they add weight.** Cite when you state a direct quote, a statistic, a price/figure, a regulation, an important claim, or a contested point. Do NOT cite every sentence: the page is a sharp study reference, not a thesis with a footnote per line. Keep a short Sources block per chapter or at the end.
- **Quotes and key data** get a source attached and, in Notion, may sit in a callout or quote block to stand out. Keep the quote verbatim.
- **Lean and compact above all.** Prefer the densest structure that stays clear: 2-column blocks for short parallel content, toggles for appendix detail, tables for comparisons, bullets for claims. Cut empty sections and filler.

## Theory vs Practice writing

- **Theory** (evergreen knowledge, deep-dives, conceptual frameworks, study notes, long-form reference): be complete and non-superficial. Include sources, tables, columns, schemas, and diagrams when they help. Confirm an index of content before writing (unless autonomous mode).
- **Practice** (how-to, operational, generalizable procedure): link to the best official external guides instead of rewriting them, especially for install/operational/security details or anything that must stay current.
- **Real Setup** (a specific person's live configuration): not this skill's job by default. Keep it out of study/theory pages; reference where it lives instead.

## Study pages (extra care)

- **Language:** English by default.
- **Terminology:** use only the word **"Chapter"**.
- **Chapter titles:** never numbered ("Chapter - Title", not "Chapter 1 - Title"), unless a real numeric/priority order exists.
- **Chapters are real headings (H2), not toggles.** Use H1 for the page topic, H2 for chapters, H3 for sub-points. Reserve toggles for minor or appendix content only (long tangents, raw data, extended examples). A page that is a wall of collapsed toggles is wrong.
- **Content:** concise and information-dense, while expert-level, deep, detailed, and complete. Include the full set of arguments and necessary information. Prioritize insight and completeness.
- **Structure vs depth:** bullets to structure arguments/claims; short paragraphs (max 5–7 lines) only to fully explain complex points.
- **Meta:** keep a small meta callout at the top with Last Updated + Related Pages.
- **Chapter structure:** an `## H2` heading, a one-line hook, then substance shaped to the material (use the 💡 key idea / 💬 example / 🔑 insight / 📚 go deeper signposts). Do not force every chapter into the same skeleton.
- **Sub-pages index at the top:** if the page has sub-pages, list them index-style near the top (a `## Deep dives` table or 2-column block), not at the bottom.
- **Exploit Notion structure:** use tables for comparisons/matrices/timelines, columns for parallel blocks, callouts for key points, and ASCII flows in code blocks for simple schemas. A page of only bullets is under-built.
- **Sources / Links / Glossary:** keep a short section at the end of each chapter or the page; cite generously where claims, data, or quotes appear.
- **Images:** add an explicit **image slot** callout (🖼️ what / why / source) exactly where a visual belongs. Study OS does not upload images, so tell the user precisely what to add and where.

## Page intro discipline (anti-duplication)

- Always include a **Page Purpose** line (what this page is and why it exists).
- Always include a **Non-scope** line (what this page deliberately does NOT cover) to reduce overlap with sibling pages.
- Always include **Related Pages** with a one-line note on the relationship/difference.

## Memory / preferences

- Layout/formatting preferences belong in these standards, not in ad-hoc notes.
- Personal recurring preferences (style, tone, depth, ways of working) can be captured separately, but never override the rules above unless the user explicitly changes them.
