# Media & Assets

How to put real visuals into a study page. These behaviors are verified against Notion through the connector. Use the right tool per media type; do not fall back to a text placeholder when a real visual is possible.

## Decision table

| Need | Use | Notes |
| --- | --- | --- |
| Flowchart, process, sequence, hierarchy, ER, state, timeline, mindmap | **Mermaid code block** | Renders natively in Notion. First choice for schemas and diagrams. |
| Simple data chart (bar, line, pie) | **Mermaid** (`pie`, `xychart-beta`) or a generated image file | Mermaid for quick charts; generated file when precise. |
| A real existing diagram, photo, or figure | **`![alt](public URL)`** | Works with any public image URL. Use Creative Commons or official sources and add attribution. |
| A chart from the user's own data | **Generate a PNG/SVG file** in the sandbox, present it, mark an image slot | The skill cannot upload to Notion or host a public URL, so the user drags the file in. |
| Video | **A "Watch" list of links** | The connector stores a plain URL as a link; the user can convert it to a player by pasting in the app. |
| Comparison / matrix / timeline of values | **Table** | Not an image. See page-architecture. |

## Mermaid (the workhorse)

Put diagrams in a fenced `mermaid` block. Verified to render. Quote node labels to be safe.
```mermaid
flowchart LR
  A["Raw text"] --> B["Tokens"] --> C["Embeddings"] --> D["Transformer"]
```
Useful types: `flowchart`, `sequenceDiagram`, `stateDiagram-v2`, `erDiagram`, `mindmap`, `timeline`, `gantt`, `pie`, `xychart-beta`. Keep diagrams small and legible; one idea per diagram. Arrows (`-->`) are safe inside the block.

## Images by URL

```
![Descriptive alt text](https://upload.wikimedia.org/.../diagram.png)
*Source: [Wikimedia Commons, CC BY-SA](https://commons.wikimedia.org/...)*
```
Rules:
- Only use stable, public, license-clean URLs (Wikimedia Commons, official paper/figure pages, government sources). Never hotlink random or copyrighted images.
- Always add a one-line attribution beneath the image.
- Do NOT use `<image src=...>` or `<embed url=...>` tags: the connector renders them as literal text. Use Markdown `![]()` only.

## Generated assets (charts/infographics the user must upload)

When a precise chart or infographic is needed and no clean public image exists:
1. Generate it in the sandbox (matplotlib/plotly for charts; a clean SVG/HTML for infographics).
2. Save it and present the file to the user.
3. At the exact spot in the page, leave an image slot so they know where it goes:
```
<callout icon="🖼️" color="yellow_bg">
	**Drop image here:** `chart-scaling-laws.png` (just generated, see chat)
	**Shows:** loss vs compute on a log-log scale with the Chinchilla point marked.
</callout>
```

## Videos

Group curated videos in a short section so they are easy to find:
```
## Watch
- [The Illustrated Transformer talk (YouTube)](https://www.youtube.com/watch?v=...)
- [3Blue1Brown, attention explained (YouTube)](https://www.youtube.com/watch?v=...)
```
Pick 1 to 3 genuinely high-quality videos (lectures, official talks, top explainers). Note to the user that pasting the link on its own line in Notion offers a player embed.

## Hard rules

- A diagram that can be Mermaid should be Mermaid, not an image slot.
- Every embedded image carries attribution.
- Never invent an image URL. If unsure it resolves and is license-clean, use Mermaid or an image slot instead.
