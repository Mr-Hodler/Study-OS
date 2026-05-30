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

This repo is a self-contained Claude plugin (and a one-plugin marketplace), so it installs directly.

```
Study-OS-Repo/                           # repo root = the plugin AND the marketplace
├── .claude-plugin/
│   ├── plugin.json                      # plugin manifest (name, version, metadata)
│   └── marketplace.json                 # marketplace manifest listing this plugin
├── README.md
├── CHANGELOG.md                         # version history (Keep a Changelog)
├── CONTRIBUTING.md                      # how to propose changes
├── LICENSE                              # MIT
├── .gitignore
├── study-os.skill                       # packaged skill for one-click install
└── skills/
    └── study-os/
        ├── SKILL.md                     # orchestrator: triggers, modes, workflow
        └── references/
            ├── writing-standards.md     # voice, formatting, visual structure
            ├── page-architecture.md     # page skeleton + verified Notion block syntax
            ├── notion-operations.md     # read/write Notion, schema detection, DB mgmt
            ├── research-protocol.md     # source quality, dating, videos, images, depth
            ├── classification.md        # Theory vs Practice vs Real Setup
            ├── reformat-mode.md         # strict text-invariant restructuring
            └── output-targets.md        # how the content model renders to Notion vs PDF/doc
```

## Setup

Connect the **Notion connector** before first use: the skill reads the source page, detects the database schema, and writes back. For PDF/doc output a document tool is also used. No configuration files are needed; the skill adapts to whatever workspace and schema it finds.

## Install

Pick one of the three options below.

### Option A - one-click `.skill` (Cowork)

Open `study-os.skill` and use **Save skill**. This installs the skill directly without touching a marketplace.

### Option B - Claude Code (or Cowork) via marketplace

```
/plugin marketplace add Mr-Hodler/Study-OS
/plugin install study-os@study-os
```

The first command registers this repo as a marketplace; the second installs the `study-os` plugin from it. After install, the skill is discovered automatically.

### Option C - manual / local

Clone the repo and add it as a local marketplace, or drop the `skills/study-os/` folder into your skills directory so `SKILL.md` is discoverable:

```
/plugin marketplace add /path/to/Study-OS-Repo
/plugin install study-os@study-os
```

### Triggers

The skill activates on phrases like "build the study page", "structure this study page", "research this topic in Notion", "make a study PDF about X", "reformat this page", or "explain this concept".

## Usage

```
Open <Notion page URL> and build the full study material.
Research <topic> and write it up as a study page under <database>.
Deepen this page, chapter by chapter, with sources.
Reformat this page for skimmability without changing the words.
Explain <concept> simply.
```

For theory pages the skill proposes a chapter index and source list first, then writes; say "autonomous" to skip the confirmation.

## Versioning and contributing

Version history lives in [CHANGELOG.md](CHANGELOG.md). To propose changes, see [CONTRIBUTING.md](CONTRIBUTING.md). The project follows [Semantic Versioning](https://semver.org/).

## License

MIT. See [LICENSE](LICENSE). Copyright (c) 2026 Aron Clementi.
