# SVG Reference

## Full `<defs>` Block

Copy this into every diagram SVG. Remove unused colors to keep file size down.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 540"
     font-family="Inter, system-ui, -apple-system, sans-serif">
  <defs>
    <!-- Glow filters -->
    <filter id="glow-teal" x="-30%" y="-30%" width="160%" height="160%">
      <feGaussianBlur stdDeviation="4" result="blur"/>
      <feFlood flood-color="#2DD4BF" flood-opacity="0.3" result="color"/>
      <feComposite in="color" in2="blur" operator="in" result="glow"/>
      <feMerge><feMergeNode in="glow"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
    <filter id="glow-purple" x="-30%" y="-30%" width="160%" height="160%">
      <feGaussianBlur stdDeviation="4" result="blur"/>
      <feFlood flood-color="#A78BFA" flood-opacity="0.3" result="color"/>
      <feComposite in="color" in2="blur" operator="in" result="glow"/>
      <feMerge><feMergeNode in="glow"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
    <filter id="glow-blue" x="-30%" y="-30%" width="160%" height="160%">
      <feGaussianBlur stdDeviation="4" result="blur"/>
      <feFlood flood-color="#4A90D9" flood-opacity="0.3" result="color"/>
      <feComposite in="color" in2="blur" operator="in" result="glow"/>
      <feMerge><feMergeNode in="glow"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
    <filter id="glow-gray" x="-30%" y="-30%" width="160%" height="160%">
      <feGaussianBlur stdDeviation="3" result="blur"/>
      <feFlood flood-color="#94a3b8" flood-opacity="0.2" result="color"/>
      <feComposite in="color" in2="blur" operator="in" result="glow"/>
      <feMerge><feMergeNode in="glow"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
    <filter id="glow-orange" x="-30%" y="-30%" width="160%" height="160%">
      <feGaussianBlur stdDeviation="4" result="blur"/>
      <feFlood flood-color="#FB923C" flood-opacity="0.3" result="color"/>
      <feComposite in="color" in2="blur" operator="in" result="glow"/>
      <feMerge><feMergeNode in="glow"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>

    <!-- Arrow markers -->
    <marker id="arrow-teal" viewBox="0 0 10 7" refX="9" refY="3.5"
            markerWidth="9" markerHeight="7" orient="auto-start-reverse">
      <path d="M 0 0 L 10 3.5 L 0 7 z" fill="#2DD4BF"/>
    </marker>
    <marker id="arrow-purple" viewBox="0 0 10 7" refX="9" refY="3.5"
            markerWidth="9" markerHeight="7" orient="auto-start-reverse">
      <path d="M 0 0 L 10 3.5 L 0 7 z" fill="#A78BFA"/>
    </marker>
    <marker id="arrow-blue" viewBox="0 0 10 7" refX="9" refY="3.5"
            markerWidth="9" markerHeight="7" orient="auto-start-reverse">
      <path d="M 0 0 L 10 3.5 L 0 7 z" fill="#4A90D9"/>
    </marker>
    <marker id="arrow-gray" viewBox="0 0 10 7" refX="9" refY="3.5"
            markerWidth="9" markerHeight="7" orient="auto-start-reverse">
      <path d="M 0 0 L 10 3.5 L 0 7 z" fill="#64748b"/>
    </marker>
    <marker id="arrow-orange" viewBox="0 0 10 7" refX="9" refY="3.5"
            markerWidth="9" markerHeight="7" orient="auto-start-reverse">
      <path d="M 0 0 L 10 3.5 L 0 7 z" fill="#FB923C"/>
    </marker>

    <!-- Node fill gradients (vertical, top brighter) -->
    <linearGradient id="grad-teal" x1="0" y1="0" x2="0" y2="1">
      <stop offset="0%" stop-color="#2DD4BF" stop-opacity="0.2"/>
      <stop offset="100%" stop-color="#2DD4BF" stop-opacity="0.07"/>
    </linearGradient>
    <linearGradient id="grad-purple" x1="0" y1="0" x2="0" y2="1">
      <stop offset="0%" stop-color="#A78BFA" stop-opacity="0.2"/>
      <stop offset="100%" stop-color="#A78BFA" stop-opacity="0.07"/>
    </linearGradient>
    <linearGradient id="grad-blue" x1="0" y1="0" x2="0" y2="1">
      <stop offset="0%" stop-color="#4A90D9" stop-opacity="0.2"/>
      <stop offset="100%" stop-color="#4A90D9" stop-opacity="0.07"/>
    </linearGradient>
    <linearGradient id="grad-gray" x1="0" y1="0" x2="0" y2="1">
      <stop offset="0%" stop-color="#94a3b8" stop-opacity="0.14"/>
      <stop offset="100%" stop-color="#94a3b8" stop-opacity="0.05"/>
    </linearGradient>
    <linearGradient id="grad-orange" x1="0" y1="0" x2="0" y2="1">
      <stop offset="0%" stop-color="#FB923C" stop-opacity="0.2"/>
      <stop offset="100%" stop-color="#FB923C" stop-opacity="0.07"/>
    </linearGradient>
  </defs>

  <!-- Background (always first) -->
  <rect width="1200" height="540" fill="#0f172a" rx="14"/>

  <!-- Zones, then Edges, then Nodes -->

</svg>
```

## Worked Example

The network schema graph at `presentations/helix-nms-detailed/network-schema-graph.svg` demonstrates every pattern:

- 4 zone backgrounds (External/gray, Hiring Side/teal, Prospect Side/purple, Bridge/blue)
- 7 nodes with glow filters and gradient fills
- 11 edges: solid for direct actions, dashed for passive connections
- Bidirectional edges (two separate paths with opposite arrows)
- Label pills on every edge
- `<tspan>` for mixed-weight text within a single node label

## Common Pitfalls

| Problem | Fix |
|---------|-----|
| `rgba()` in SVG attributes | Use `fill="#hex" fill-opacity="0.3"` as separate attributes |
| Unicode in XML comments | Use ASCII only: `<!-- A to B -->` not `<!-- A -> B -->` |
| Missing XML declaration | Always start with `<?xml version="1.0" encoding="UTF-8"?>` |
| Text not centered in node | Set `text-anchor="middle"` and position text x at rect center, y at rect center + ~4px |
| Edges hidden behind nodes | Draw all `<path>` elements before all `<g>` node groups |
| Font not loading via `<img>` | SVG referenced via `<img>` can't load web fonts; the system font fallback handles this |
| Arrow not visible | Ensure `marker-end="url(#arrow-COLOR)"` matches a defined marker id |
| Label pill too narrow | Measure text width roughly (6px per char at font-size 10) and add 16px padding |

## Sizing Guide

| Diagram complexity | Recommended viewBox | Node count |
|-------------------|---------------------|------------|
| Simple (3-5 nodes) | `0 0 800 400` | 3-5 |
| Medium (6-10 nodes) | `0 0 1200 540` | 6-10 |
| Complex (11+ nodes) | `0 0 1400 700` | 11-15 |

For slides, set `max-height` on the `<img>` tag: 300px for diagram-heavy slides, 380px for diagram-focused slides, 500px for full-slide diagrams.
