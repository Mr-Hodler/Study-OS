# Classification: Theory vs Practice vs Real Setup

A single rule to decide *how to write* a page and *where the truth lives*. These are not extra database categories; they are a writing/placement criterion.

## The three levels

| Level | Answers | How it is written | Where it lives |
| --- | --- | --- | --- |
| **Theory** | What it is, why, how to reason | Complete, non-superficial. Sources, tables, columns, schemas, diagrams when they help. | The study library (Theory view) |
| **Practice** | How to do it, step by step, generalizable | Executable. If better official guides exist, link them instead of rewriting. | The study library (Practice view) |
| **Real Setup** | How *your* system is configured today | Real state, decisions, runbooks. Must stay true to reality. | A separate ops/business space, not the study library |

## 10-second test

- Question is **"why / how to think?"** → **Theory**
- Question is **"how do I do it, step by step?"** → **Practice**
- Question is **"how is MY system set up right now?"** → **Real Setup** (out of scope for study pages)

## Hybrid pages

If a topic needs both, keep two explicit sections on the same page:
- **Theory:** concepts and criteria.
- **Practice:** procedure and checklist.

## Anti-duplication

- A practice page does not have to be a sub-page of a theory page.
- If a page contains both, split into the two sections above rather than duplicating a sibling.
- Use the page's **Non-scope** and **Related Pages** lines to point at where overlapping content actually lives.

## Tagging in the database

- Read the database's own category/scope options and apply them.
- In the reference system this was generalized from: practice/how-to content is tagged with a "Guide" category; theory content is not tagged "Guide" even when it includes examples. Apply the equivalent logic to whatever schema is present.

## Examples (mental model)

- **AI** - Theory: "what AI, LLM, agent, evaluation are." Practice: "repeatable vibe-coding workflow." Real Setup: "my AI stack for project X: models, tools, limits, runbook."
- **Web** - Theory: "what the web, DNS, hosting are." Practice: "how to deploy a site, analytics." Real Setup: "my DNS zone, WordPress install, provider, procedures."
