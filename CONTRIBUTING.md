# Contributing to Study OS

Thanks for improving Study OS. This is a skill/plugin, so most contributions are edits to Markdown rules, not code.

## What lives where

- `skills/study-os/SKILL.md` - the orchestrator. Change this for workflow, modes, or triggers.
- `skills/study-os/references/*.md` - the rule library. Change these for writing standards, page architecture, Notion operations, research protocol, classification, reformat behavior, or output targets.
- `.claude-plugin/` - plugin and marketplace manifests. Bump versions here on release.

## Ground rules for edits

These mirror what the skill enforces on its own output, so the repo stays consistent with what it preaches:

- **No em dashes (—)** anywhere in docs or skill text. Use a comma, a colon, parentheses, or split the sentence.
- **No bare URLs.** Embed links in descriptive text.
- Keep rules **dense and specific**. Prefer a concrete rule over a vague principle.
- When you discover that a Notion block syntax behaves differently in practice, update `page-architecture.md` to match reality and note it.

## Proposing changes

1. Fork and branch from `main`.
2. Make focused edits with a clear commit message.
3. If behavior changes, add an entry under "Unreleased" in `CHANGELOG.md`.
4. Open a pull request describing the motivation and any before/after examples.

## Versioning

Semantic Versioning. Bump the version in `CHANGELOG.md`, `.claude-plugin/plugin.json`, and `.claude-plugin/marketplace.json` together on release.

## Testing a change

Install the plugin locally and run the skill against a scratch Notion page:

```
/plugin marketplace add /path/to/Study-OS-Repo
/plugin install study-os@study-os
```

Then point it at a test page and confirm the output matches the standards in `references/`.
