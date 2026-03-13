---
name: mermaid-to-svg
description: Convert Mermaid diagrams from presentations into polished, hand-crafted SVG files that match the slide deck's dark theme and brand colors. Use when the user wants to replace a Mermaid diagram with a better-looking SVG, improve diagram aesthetics, or create a visual diagram for slides.
---

# Mermaid to SVG Converter

Convert Mermaid diagrams (or conceptual diagrams described in text/images) into polished SVG files styled to match this repository's Reveal.js presentation theme.

## When to Use

- User wants to convert a `<div class="mermaid">` block into a standalone SVG
- User wants a more aesthetic or readable version of a diagram
- User provides a network/flow/hierarchy diagram to visualize for slides
- User shares an image of a diagram and wants an SVG version

## Workflow

### 1. Identify the Source Diagram

Read the Mermaid code from the presentation's `index.html` (inside `<div class="mermaid">` blocks) or from `slides.md` (inside ` ```mermaid ` fences). Parse:

- **Nodes**: names, labels, groupings
- **Edges**: direction, labels, line style (solid `-->`, dashed `-.->`)
- **Subgraphs**: logical groupings that become zone backgrounds

### 2. Plan the Layout

Before writing SVG, decide:

- **Canvas size**: Use `viewBox="0 0 1200 540"` as the default (fits 1280x720 slides with margin)
- **Zones**: Map Mermaid subgraphs to background regions. Assign each zone a brand color
- **Node positions**: Sketch center coordinates for each node. Leave ~150px horizontal and ~80px vertical spacing minimum
- **Edge routing**: Prefer quadratic beziers (`Q`) for short curves, cubic beziers (`C`) for long arcs

### 3. Write the SVG

Create the file at `presentations/<slug>/<diagram-name>.svg`. Follow the structure and patterns in the [SVG reference](svg-reference.md).

**Critical SVG rules:**
- Start with `<?xml version="1.0" encoding="UTF-8"?>`
- Use ASCII-only in comments (no arrows, box-drawing chars, or Unicode symbols)
- Never use `rgba()` in SVG attributes. Use `fill-opacity` / `stroke-opacity` as separate attributes
- Font stack: `font-family="Inter, system-ui, -apple-system, sans-serif"` on the root `<svg>`
- Draw edges BEFORE nodes so nodes visually overlap connection lines

### 4. Update the Presentation

Replace the Mermaid block in `index.html` with an `<img>` tag:

```html
<img src="<diagram-name>.svg" alt="<description>" class="network-img" style="max-height: 380px;">
```

Ensure the `.network-img` CSS class exists in the presentation (it's in the standard template).

### 5. Preview and Iterate

Start a local server (`python3 -m http.server <port>`) and open the SVG in the browser to verify:
- All nodes are visible and labeled
- Edges connect to the correct nodes and don't overlap text
- Labels are readable at slide display size (test at the slide URL, not just the standalone SVG)
- Zone backgrounds are subtle, not distracting

## Design System

### Color Palette

Assign each logical group a color from the brand palette:

| Role | Hex | Use for |
|------|-----|---------|
| Teal | `#2DD4BF` | Primary/hiring-side elements |
| Purple | `#A78BFA` | Secondary/prospect-side elements |
| Blue | `#4A90D9` | Bridge/connecting elements |
| Gray | `#94a3b8` / `#64748b` | External/passive elements |
| Orange | `#FB923C` | Accent/warning (use sparingly) |
| Background | `#0f172a` | SVG background, edge label pill fills |
| Text light | `#e2e8f0` | Node text |
| Text muted | `#cbd5e1` | Secondary node text |

### Node Anatomy

Each node is a `<g>` with a glow filter wrapping a rounded rect + text:

```xml
<g filter="url(#glow-teal)">
  <rect x="X" y="Y" width="W" height="48" rx="10"
        fill="url(#grad-teal)" stroke="#2DD4BF" stroke-opacity="0.45" stroke-width="1.5"/>
  <text x="CX" y="CY" text-anchor="middle" fill="#e2e8f0"
        font-size="13" font-weight="600">Label</text>
</g>
```

- Height: 48px standard
- Corner radius: `rx="10"`
- Fill: use the matching `linearGradient` (top stop-opacity ~0.2, bottom ~0.07)
- Stroke: brand color at ~0.45 opacity
- Text: centered, 13px, weight 600-700

### Edge Anatomy

Each edge has three parts: path, label background pill, label text.

```xml
<!-- Solid edge -->
<path d="M x1,y1 C cx1,cy1 cx2,cy2 x2,y2" fill="none"
      stroke="#4A90D9" stroke-width="1.5" marker-end="url(#arrow-blue)" opacity="0.8"/>
<rect x="LX" y="LY" width="LW" height="20" rx="10"
      fill="#0f172a" stroke="#4A90D9" stroke-opacity="0.3" stroke-width="0.8"/>
<text x="LCX" y="LCY" text-anchor="middle" fill="#4A90D9"
      font-size="10" font-weight="500">label_text</text>

<!-- Dashed edge (for passive/external connections) -->
<path d="..." stroke-dasharray="6 4" .../>
```

- Label pill: height 20px, `rx="10"`, filled with background color `#0f172a`
- Label text: 10px, colored to match the edge
- Dashed edges: use `stroke-dasharray="6 4"` and lower opacity (0.45-0.65)

### Zone Backgrounds

Subgraphs become subtle background regions:

```xml
<rect x="X" y="Y" width="W" height="H" rx="12"
      fill="#COLOR" fill-opacity="0.03"
      stroke="#COLOR" stroke-opacity="0.16" stroke-width="1.5" stroke-dasharray="7 4"/>
<text x="CX" y="TOP+24" text-anchor="middle"
      fill="#COLOR" fill-opacity="0.65" font-size="12" font-weight="700"
      letter-spacing="0.1em">ZONE LABEL</text>
```

### Required `<defs>`

Every SVG needs these in `<defs>`. See [svg-reference.md](svg-reference.md) for the full block. Summary:

- **Glow filters**: one per brand color (`glow-teal`, `glow-purple`, `glow-blue`, `glow-gray`). `feGaussianBlur` + `feFlood` + `feComposite` + `feMerge`.
- **Arrow markers**: one per brand color (`arrow-teal`, etc.). Triangular, `markerWidth="9"`, `orient="auto-start-reverse"`.
- **Gradients**: one per brand color (`grad-teal`, etc.). Vertical linear gradient, top stop-opacity ~0.2, bottom ~0.07.

## Diagram Type Guidelines

### Flowcharts / Hierarchies (`graph TD`)

- Root at top, leaves at bottom
- Use zone backgrounds for each level or logical group
- Edges flow downward; cross-links use dashed curves

### Network Graphs (`graph LR`)

- Actors on the left, objects on the right
- Group by role using zone backgrounds
- Bidirectional edges: two separate curved paths with opposite arrow markers

### Sequence-style Flows

- Arrange actors left-to-right in order of involvement
- Steps flow left-to-right with numbered labels
- Use dashed return paths for responses

## Reference

For the complete SVG `<defs>` block and a full worked example, see [svg-reference.md](svg-reference.md).
