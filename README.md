# markdown-styles

Typora-like CSS for **VS Code / Cursor** Markdown preview, loadable via `markdown.styles` (local path or [jsDelivr](https://cdn.jsdelivr.net/gh/dbatche/markdown-styles@main/markdown-preview-enhanced.css)).

## Mermaid troubleshooting

**Symptom A — diagram renders but looks wrong (clipped, wrong size, boxed)**

- The stylesheet now includes rules for `.mermaid` / `.mermaid svg`. Reload the preview after updating the CSS.

**Symptom B — you still see a grey fenced code block with `graph TD` / `flowchart` text (no diagram)**

- That means **Mermaid did not run** in that webview. Custom CSS does not execute or block JavaScript; something else is wrong.
- **Isolate:** Temporarily clear `markdown.styles` and open the **same** preview (same window vs second window). If the diagram appears without your CSS, note it — but usually this test is about **which preview** is open, not the stylesheet.
- **Check:** Same workspace and settings profile in both windows; `markdown.styles` uses a URL or path the webview can load (broken or blocked CSS should not stop Mermaid, but verify the URL loads).
- **Check:** Built-in Mermaid vs **Markdown Preview Mermaid** extension — both enabled consistently.
- **Last resort:** Export the diagram as PNG/SVG and use `![alt](file.png)` so rendering does not depend on Mermaid in the preview.

## Editing

Change `markdown-preview-enhanced.css`, commit, push; jsDelivr `@main` picks up after cache TTL (or pin a commit hash in the URL for immediate updates).
