# Study OS

A portable skill that turns sparse inputs (keywords, topics, dumped notes) into **deep, expert-level, consistently structured study and research pages in Notion**, and keeps the underlying study **database** clean. It also handles reformatting and quick explanations.

Built to fix a common problem: generic AI writing stays shallow and high-level. Study OS researches, goes chapter by chapter, cites dated sources, and lays content out for fast reading and long-term reuse. Every page comes out with the same architecture and the same rigor, regardless of topic.

## What it does

- **Build** - reads a Notion page (or your prompt), classifies it (Theory vs Practice), proposes a chapter index, **researches with real dated sources, videos, and image suggestions**, writes the full page in a fixed clean structure, then updates the database row.
- **Reformat** - restructures an existing page for skimmability **without changing a single word**.
- **Explain** - answers a concept in plain language in chat, without editing the page.

## Design principles

- **Depth with structure.** Concise never means shallow. Bullets to structure claims; short paragraphs only for complex points; tables, columns, and diagrams where they help.
- **Sources are mandatory** for theory material: authoritative, dated, embedded as hyperlinks. No bare URLs.
- **Consistency is the product.** The same activity type always yields the same shape.
- **Agnostic by design.** No hardcoded categories, property names, or database IDs. The skill reads any Notion schema at runtime, so anyone can use it for any subject in any workspace.

## Repository layout

```
Study-OS-Repo/
├── README.md
├── LICENSE
├── .gitignore
└── skills/
    └── study-os/
        ├── SKILL.md                      # orchestrator: triggers, modes, workflow
        └── references/
            ├── writing-standards.md      # voice, formatting, visual structure
            ├── page-architecture.md      # page skeleton + exact Notion block syntax
            ├── notion-operations.md      # read/write Notion, schema detection, DB mgmt
            ├── research-protocol.md       # source quality, dating, videos, images, depth
            ├── classification.md         # Theory vs Practice vs Real Setup
            └── reformat-mode.md          # strict text-invariant restructuring
```

## Install

### Cowork / Claude desktop
Place the `skills/study-os/` folder into your Cowork skills directory (or add this repo as a plugin/marketplace source). Connect the Notion connector. The skill triggers on phrases like "build the study page", "structure this study page", "research this topic in Notion", "reformat this page", or "explain this concept".

### Claude Code
Add `skills/study-os/` under your project or user skills directory so `SKILL.md` is discoverable. Ensure a Notion MCP connector is configured.

## Usage

```
Open <Notion page URL> and build the full study material.
Research <topic> and write it up as a study page under <database>.
Deepen this page, chapter by chapter, with sources.
Reformat this page for skimmability without changing the words.
Explain <concept> simply.
```

For theory pages the skill proposes a chapter index and source list first, then writes; say "autonomous" to skip the confirmation.

## License

MIT. See [LICENSE](LICENSE).
