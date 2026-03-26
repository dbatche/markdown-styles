# markdown-styles

Typora-like CSS for **VS Code / Cursor** Markdown preview, loadable via `markdown.styles` (local path or [jsDelivr](https://cdn.jsdelivr.net/gh/dbatche/markdown-styles@main/markdown-preview-enhanced.css)).

## Mermaid troubleshooting

**Symptom A — diagram renders but looks wrong (clipped, wrong size, boxed)**

- The stylesheet now includes rules for `.mermaid` / `.mermaid svg`. Reload the preview after updating the CSS.

**Symptom B — you still see a grey fenced code block with `graph TD` / `flowchart` text (no diagram)**

- That means **Mermaid did not run** in that webview. Custom CSS does not execute or block JavaScript; something else is wrong.

### Install the Mermaid extension (Cursor / VS Code)

Some environments only ship **partial** Mermaid support. Install **Markdown Preview Mermaid Support** so fenced ` ```mermaid ` blocks are always handled by the extension:

```powershell
cursor --install-extension bierner.markdown-mermaid
```

Then **reload the window** (`Developer: Reload Window`) and open the Markdown preview again.

### Other checks

- **Isolate:** Temporarily clear `markdown.styles` and open the **same** preview. If the diagram still appears as raw code, the problem is not your stylesheet.
- **Same** workspace and settings profile in both windows; `markdown.styles` URL loads in a browser (jsDelivr).
- **Last resort:** Export the diagram as PNG/SVG and use `![alt](file.png)` so rendering does not depend on Mermaid in the preview.

## Mermaid look (grey, Typora-like)

The stylesheet wraps diagrams in a **light grey panel** (`#f6f8fa`) and softens node/edge colors. In **User** `settings.json`, use the extension’s **neutral** theme (grey tones, not harsh black):

```json
"markdown-mermaid.lightModeTheme": "neutral",
"markdown-mermaid.darkModeTheme": "neutral"
```

## Editing

Change `markdown-preview-enhanced.css`, commit, push; jsDelivr `@main` picks up after cache TTL (or pin a commit hash in the URL for immediate updates).
