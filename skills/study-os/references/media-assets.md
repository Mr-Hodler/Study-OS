# Media & Assets

How to put real visuals into a study page with as little manual work for the user as possible. The order below is the order of preference: go down the list only when the step above cannot deliver.

## Decision order

| Step | Use | When |
| --- | --- | --- |
| 1 | **Mermaid** code block | Any process, protocol, sequence, hierarchy, decision, concept map. Renders natively, always works. |
| 2 | **Generated image, uploaded** | A precise chart from data (log scales, trends, comparisons), an infographic. Built in the sandbox, uploaded to Notion. |
| 3 | **Existing image, uploaded** | A real photo, hardware shot or canonical figure that exists online under a usable licence. Notion downloads it, so hotlink blocking no longer matters. |
| 4 | **Interactive embed** | When the learning is in changing an input (a cost model, compounding, a cap table, a conjugation drill). |
| 5 | **Image slot** | Only when 1 to 4 are impossible (no licensed image, upload tools unavailable). |

Videos are not images: they go in the Watch list of the closing block.

## 1. Mermaid

Verified types: `flowchart`, `sequenceDiagram`, `stateDiagram-v2`. Others (`mindmap`, `timeline`, `xychart-beta`) depend on the Mermaid version Notion ships: use them only after checking once that they render, otherwise draw the same idea as a flowchart.

Patterns that teach well:
- **Actors in a protocol or attack:** `sequenceDiagram` with Alice, Bob, Eve (eavesdropper), Mallory (active attacker), plus named systems (Bank, Node, Miner).
- **Concept map** for the top of a topic page: `flowchart LR` from the topic to its 4 to 7 parts.
- **Decision:** `flowchart TD` with a question node and labelled branches.
- **Before and after:** two small flowcharts in columns.

Keep each diagram to one idea and under ~12 nodes. Quote labels that contain punctuation.

## 2. Generated image, uploaded

1. Build the asset in the sandbox (matplotlib or plotly for charts; a clean SVG or HTML rendered to PNG for infographics). Label axes, units, the source line and the date. Look at it before uploading: overlapping labels are a defect.
2. `notion-create-file-upload` with the filename. It returns a one-shot `upload_url` and headers.
3. POST the file once as multipart form data (field `file`) to that URL with the returned headers, for example `curl -X POST <upload_url> -H "authorization: ..." -F "file=@chart.png;type=image/png"`.
4. Place it **immediately** (uploads expire if not attached within the window): `<image source="file-upload://ID">Caption with source and date</image>`.
5. If the library has a Drive mirror (`notion-operations.md` -> "Library conventions"), also save the file in the page's Drive folder so the asset exists outside Notion.

## 3. Existing image, uploaded

When a real image is the right call (a photo of a Willow chip, a historical figure, an official diagram):
1. Find a direct file URL with a clear licence (Wikimedia Commons file URLs, official press kits, papers under CC licences). Note the licence and author.
2. `notion-create-attachment` with `source_url` and a filename. Notion downloads the file itself, so the hotlink problem of plain `![]()` embeds disappears. Redirecting URLs fail: use the final direct file URL.
3. Place it with the returned source and a caption that carries attribution: `<image source="file-upload://ID">Google Willow chip. Photo: Google, press kit</image>`.
4. Never invent a URL. If the licence is unclear, recreate the idea (Mermaid or a generated image) instead of copying.

A plain `![caption](https://url)` embed is acceptable only for hosts known to allow hotlinking; it is a fallback, not the default.

## 4. Interactive embed

Some things are learned by changing an input and watching the output. Build a small self-contained HTML tool (inline CSS and JS, no external calls), upload it with `notion-create-attachment` (`content` + a `.html` filename) and place it with `<embed source="file-upload://ID" />` at the exact spot. Rules: one tool per real need, never decoration; the page must make sense without it; numbers in the tool match the numbers on the page. Without upload tools, put the model in a table with the formula written out.

## 5. Image slot (last resort)

```
<callout icon="🖼️" color="yellow_bg">
**Image to add here.**
**What:** [precise description]
**Search Google for:** "[specific query]" (Google Images)
**Why:** [what it clarifies]
</callout>
```
One slot per image, at the exact spot. Say in the report why steps 1 to 4 were not possible.

## Videos

The Watch list in the closing block: 1 to 3 genuinely high-quality videos (lectures, official talks, top explainers) as descriptive links. When a video is central to a chapter, try `<video source="https://www.youtube.com/watch?v=...">Caption</video>` at that spot and re-fetch to check it became a player; if not, keep the link.

## Hard rules

- A diagram that can be Mermaid is Mermaid.
- Every image has a caption with source or "Generated from [sources], [date]".
- Never invent an image URL or a licence.
- Do not route diagrams or writing through Notion AI: it is not reachable through the connector and reintroduces generic output.
