# Changelog

All notable changes to Study OS are documented here. The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

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
