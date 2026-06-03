# Changelog

All notable changes to Study OS are documented here. The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.10.0] - 2026-06-02

### Added
- **Analogy signpost (🧩).** For complex or technical topics the skill now adds analogies (a familiar mental model), not just examples, and uses a dedicated 🧩 signpost. Updated `writing-standards.md` and `page-architecture.md`.

## [1.9.0] - 2026-06-02

### Added
- **Actionable image slots:** when a page needs a real image, the skill now drops a visible yellow callout at the exact spot that says what to add and includes a ready **"Search Google for: ..."** query, so the user finds and inserts the image in one step. Updated `media-assets.md`, `page-architecture.md`, and `SKILL.md`.

### Notes
- Optional editorial database property **Page state** (Draft / To expand / Needs edits / Complete) is supported by the database-management rules, distinct from the learning `Status`.

## [1.8.0] - 2026-06-02

### Added
- **Study Librarian**, a second skill in the plugin. It curates the study library at the collection level. Modes: **Audit** (consistency + gaps), **Find** (where is X / what's missing), **Map** (index + Mermaid graph), **Organize** (metadata + prerequisite/related graph), **Scaffold** (turn a study plan into a stub structure for Study OS to fill), **Dedupe** (overlaps and merges).
- Reference files for it: `library-operations.md`, `audit-checklist.md`. Packaged as `study-librarian.skill`.
- README expanded with per-skill use cases and concrete examples, plus an Author section.

### Scope boundary
- Study Librarian manages the **material and its organization only**. It never changes the user's learning state (`Status`, `Next review`), never writes deep page content (that is Study OS), and runs no quizzes or spaced repetition.

### Changed
- Plugin, marketplace, and README updated to describe the two skills. Cover redesigned (the monogram no longer reads as a face).

## [1.7.0] - 2026-06-02

### Added
- New chapters across the AI 101 deep dives: **edge / on-device & hybrid** (Part 5), **embeddings & vector search** (Part 3), and **AGI & timelines** (Part 8).
- **Repository cover image** (`assets/cover.svg` + `assets/cover.png`) for the public repo and GitHub social preview, shown at the top of the README.

### Housekeeping
- Generated study assets (charts/diagrams the skill makes for a page) are now excluded from the repo via `.gitignore`; they belong in the outputs folder, not in source control. Removed two stray chart PNGs from the repo root.

## [1.6.0] - 2026-06-02

### Added
- **Refresh mode:** re-verify only the time-sensitive facts on an existing page and surgically update just those, for evergreen maintenance without a full rewrite.
- **Knowledge-graph linking:** a `Prerequisites` / `Unlocks` self-relation on the Study Index, plus a documented standard for Related lines and inline page mentions, so pages connect into a web.
- **Spaced-repetition review:** a daily scheduled task that lists Study Index pages due for review (uses the new `Status` + `Next review` properties).
- **Real asset generation:** the skill now generates chart images (matplotlib) as files and drops an image slot at the right spot. Shipped two example charts (scaling laws, bias-variance).
- **Three new AI 101 deep dives:** Part 7 (AI Safety & Alignment), Part 8 (Multimodal, World Models & Robotics), Part 9 (Building AI Products / Founder's Playbook).

## [1.5.0] - 2026-06-02

### Fixed
- **External images render unreliably** (Wikimedia and many hosts block hotlinking, showing a blank box). The skill now defaults to Mermaid or a generated-file image slot, and only embeds a URL from a host known to allow hotlinking. Replaced the non-rendering perceptron image with a Mermaid diagram.
- **Duplicate sub-page index removed:** the child-page cards ARE the index; the skill no longer adds a redundant title table next to them.
- Avoid dotted-domain text inside link labels (Notion auto-links it into a broken double-link).

### Changed
- **Higher depth bar** (`research-protocol.md`): deep-dive pages now aim at real competence (mechanism, intuition, trade-offs, numbers, edge cases, misconceptions), with several diagrams and tables, and must cover every keyword the parent page implies.
- All six AI 101 deep-dive sub-pages substantially expanded, adding the previously missing topics: Quantum AI, knowledge graphs, LLM security (attacks and defenses at personal/product/company level), decoding and sampling, Mixture of Experts, model-based RL and reward hacking, training parallelism, inference prefill/decode, the compute supply chain, and AI geopolitics.

## [1.4.0] - 2026-06-01

### Added
- **Edit-efficiency rule** (`notion-operations.md`): prefer surgical `insert_content` / `update_content` over full `replace_content`, and write new pages in one `create-pages` call, to save tokens and avoid dropping preserved blocks.
- **Notion handoff pattern** (`media-assets.md`): for app-only tasks (image upload, video embed, native database charts, hand-drawn mind map), emit a precise handoff callout with an optional ready-to-paste prompt, instead of routing core writing or diagrams through Notion AI.

### Notes
- Mermaid remains the default for diagrams: cheap, native, deterministic, and fully under the skill's control.

## [1.3.0] - 2026-06-01

### Added
- **Verified media policy** (`media-assets.md`): Mermaid code blocks for diagrams/schemas (render natively in Notion), `![alt](url)` images by clean public URL with attribution, generated chart files plus image slots, and curated `## Watch` video lists. Confirmed via live testing that `<image>`/`<embed>` tags do NOT work.
- **QA self-review rubric** (`qa-review.md`) that the skill runs before presenting a page.
- **Per-chapter depth**: hook, key idea, numeric example, ⚠️ misconception, 🧭 open question, and page-level level + reading time in the meta.
- **Study Index database**: optional `Status` (To learn / Learning / Reviewed / Mastered) and `Next review` (date) properties for a lightweight spaced-repetition workflow.

### Changed
- `page-architecture.md`, `writing-standards.md`, and `SKILL.md` updated to require real visuals over placeholders, per-chapter depth, and the QA pass.

## [1.2.0] - 2026-05-31

### Added
- **Sub-pages index at the top** of hub pages (a `## Deep dives` table plus the live page cards), so the map is the first thing a reader sees.
- **Mandatory use of Notion structure:** tables for comparisons, matrices, and timelines; columns for parallel blocks; ASCII flows in code blocks for simple schemas.
- **Image slots:** an explicit 🖼️ callout (what / why / source) placed exactly where a visual belongs, since the skill cannot upload images itself.
- Guidance to cite more generously and to deepen content.

### Changed
- Updated `page-architecture.md`, `writing-standards.md`, and `SKILL.md` with the above; rebuilt the page template around an index-first, table-and-column-rich layout.

## [1.1.0] - 2026-05-30

### Changed
- **Chapters are now real headings (H1/H2/H3), not toggles.** Toggles are reserved for minor or appendix content only. A page is no longer a wall of collapsed sections.
- **Added a "soul" layer** so pages read like an expert talking to a smart peer, not a generated template: hook openings, structure varied to fit the material, and a consistent signpost system (💡 key idea, 💬 example, 🔑 insight, ⚠️ watch out, 📚 go deeper).
- Updated `writing-standards.md`, `page-architecture.md`, and `SKILL.md` to match; reworked the page template around headings and signposts.

## [1.0.0] - 2026-05-30

### Added
- Initial release of the **Study OS** skill and installable plugin.
- `SKILL.md` orchestrator with three modes: **Build**, **Reformat**, **Explain**.
- Reference library:
  - `writing-standards.md` - voice, formatting, visual structure, study-page rules.
  - `page-architecture.md` - page skeleton and verified Notion block syntax (toggles use a bold `<summary>`).
  - `notion-operations.md` - read/write Notion, runtime schema detection, database management, safe edits.
  - `research-protocol.md` - source quality, absolute dating, videos, image suggestions, depth bar.
  - `classification.md` - Theory vs Practice vs Real Setup decision rules.
  - `reformat-mode.md` - strict text-invariant restructuring.
  - `output-targets.md` - one content model rendered to Notion or PDF/doc.
- Plugin packaging: `.claude-plugin/plugin.json` and `.claude-plugin/marketplace.json` for marketplace install.
- Repo scaffolding: README, LICENSE (MIT), `.gitignore`, CHANGELOG, CONTRIBUTING.
- Distributable `study-os.skill` package for one-click install.

### Design rules baked in
- Input-agnostic (keywords, notes, dumps, or an existing page) and output-agnostic (Notion or PDF/doc).
- Workspace-agnostic: no hardcoded categories, property names, or database IDs; the schema is read at runtime.
- Sources cited only where they add weight (quotes, data, key/contested claims), never thesis-style.
- Formatted links only, never bare URLs.
- Global ban on the em dash in any generated output.
- English output by default.

[1.0.0]: https://github.com/Mr-Hodler/Study-OS/releases/tag/v1.0.0
