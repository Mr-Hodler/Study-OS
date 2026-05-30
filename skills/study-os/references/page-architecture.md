# Page Architecture

The fixed skeleton every Study OS page follows, plus the exact Notion-flavored Markdown block syntax to produce it. Consistency here is the whole point: a reader should recognize the structure instantly across topics.

## The skeleton (in order)

1. **Meta callout** (gray background): `Last Updated` + `Related Pages`.
2. **Purpose callout** (blue background): `Page Purpose`, `Non-scope`, `Related Pages`.
3. Optional `Sub Pages` list and `Other Sources` list.
4. Optional `Key Insight` / `Note` / `Warning` callouts where relevant.
5. `# Main Topic` followed by a horizontal rule `---`.
6. **Chapters** as toggle headings, each: `Chapter - Title` → `Summary` bullets → `Content` → chapter `Sources` / `Links` / `Glossary`.
7. Page-level `Sources` (+ optional `Glossary`) at the end if not per-chapter.

## Block syntax (Notion-flavored Markdown)

Verified against live Notion content. Use exactly these forms. When unsure, fetch a known well-formatted page and mirror its syntax rather than guessing.

### Callouts
```
<callout icon="💡" color="blue_bg">
	**Page Purpose:** What this page contains and why it exists.
	**Non-scope:** What this page deliberately does not cover.
	**Related Pages:**
	- <mention-page url="https://www.notion.so/PAGE_ID"/> – relationship and difference
</callout>
```
Common colors: `gray_bg` (neutral/meta), `blue_bg` (insight/purpose), `green_bg` (positive). Use `icon` optionally.

### Meta callout
```
<callout color="gray_bg">
	**Last Updated:** <mention-date start="2026-05-30"/>
	**Related Pages:** <mention-page url="..."/>
</callout>
```

### Headings + rule
```
# Main Topic
---
## Subsection
### Detail
```

### Chapter as toggle
A chapter is a collapsible toggle. Verified rendering: put the chapter title in the `<summary>` as **bold text** (a `###` inside `<summary>` does not render as a heading reliably). Indent the chapter body one level inside the toggle:
```
<details>
<summary>**Chapter - Title**</summary>

	**Summary**
	- one-line takeaway
	- one-line takeaway

	**Content**
	- structured claim
	- structured claim

	**Sources**
	- [Descriptive title, Mar 2026](https://example.com)
</details>
```
Avoid `->` arrow notation inside Notion text; the `>` gets escaped. Write "then" or use a real diagram instead.

### Tables
```
<table fit-page-width="true" header-row="true">
<tr><td>Dimension</td><td>Option A</td><td>Option B</td></tr>
<tr><td>**Cost**</td><td>...</td><td>...</td></tr>
</table>
```

### Columns (space-saving, 2 parallel short blocks)
```
<columns>
	<column>
		### Pros
		- ...
	</column>
	<column>
		### Cons
		- ...
	</column>
</columns>
```

### Mentions, links, TOC
- Page mention: `<mention-page url="https://www.notion.so/PAGE_ID"/>`
- Date mention: `<mention-date start="2026-05-30"/>`
- Linked child page block: `<page url="https://www.notion.so/PAGE_ID">Title</page>`
- Table of contents: `<table_of_contents color="gray"/>`
- Inline link in descriptive text: `[descriptive text](https://example.com)` - never a bare URL.

### Code blocks
Use fenced code with a language hint for commands/snippets:
```
​```python
print("hello")
​```
```

## Standard page template (fill the brackets)

```
<callout color="gray_bg">
	**Last Updated:** <mention-date start="YYYY-MM-DD"/>
	**Related Pages:** <mention-page url="..."/>
</callout>

<callout icon="💡" color="blue_bg">
	**Page Purpose:** [what this page is and why it exists]
	**Non-scope:** [what it deliberately excludes; point to where that lives]
	**Related Pages:**
	- <mention-page url="..."/> – [relationship + difference]
</callout>

# [Main Topic]
---

<details>
<summary>**Chapter - [Title]**</summary>

**Summary**
- [takeaway]

**Content**
- [dense, expert-level structured content]
- [short paragraph only when a complex point needs full explanation]

> Image suggestion: [what diagram/image would help here]

**Sources**
- [Title, Month Year](URL)
</details>

<details>
<summary>**Chapter - [Title]**</summary>
...
</details>

## Glossary
- **Term:** definition.

## Sources
- [Title, Month Year](URL)
```

## Notes on chapters

- Prefer chapters when content is long or naturally segmented. For short pages, normal H2 headings are fine; reserve toggle headings for major chapters.
- Do not deep-nest toggles unless the structure already requires it.
- Keep operational timelines/checklists in an appendix; keep the main chapters conceptual for theory pages.
