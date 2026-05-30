# Changelog

All notable changes to Study OS are documented here. The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

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
