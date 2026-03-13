---
paths:
  - "presentations/**/*.html"
  - "presentations/**/*.css"
  - "presentations/**/*.js"
  - "presentations/**/*.svg"
---

# Visual Verification Before Completion

Before marking any task as complete, you **must** visually verify changes that affect presentation output.

## Required Steps

1. **Start a local server** if not already running: `python3 -m http.server <port>` from the project root.
2. **Open the affected page** in the browser using `open http://localhost:<port>/presentations/<slug>/index.html` (macOS).
3. **Verify the change** — confirm the expected visual or functional change is present. If working on SVGs, also open the standalone SVG file in the browser.
4. **Fix any issues** found during verification before marking complete.

## When This Applies

- Any HTML, CSS, or JS change that affects presentation output
- Layout, styling, animation, or content changes
- Adding or reordering slides in a Reveal.js deck
- SVG diagram creation or modification
- Any change the user would judge by looking at the result

## When You May Skip

- Changes to non-visual files only (e.g. README, `.gitignore`, rule files, markdown-only notes)
- Dependency or config changes with no visual impact
