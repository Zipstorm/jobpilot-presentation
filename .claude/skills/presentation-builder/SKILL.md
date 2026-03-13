---
name: presentation-builder
description: Scaffold a new Reveal.js presentation in this multi-presentation repository. Use when the user wants to create a new presentation, add a new deck, or start a new set of slides.
---

# Presentation Builder

## Workflow

Follow these steps to create a new presentation:

### 1. Gather Info

Determine from the user:
- **Slug** (kebab-case folder name, e.g. `product-roadmap`)
- **Title**
- **Description** (one line)
- **Authors**
- **Date** (YYYY-MM-DD, default to today)
- **Tags** (optional list for the hub card)

### 2. Create Folder and Files

Create `presentations/<slug>/` with two files:

#### `index.html`

Use this template, filling in the title:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>TITLE</title>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@5.1.0/dist/reveal.css">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reveal.js@5.1.0/dist/theme/black.css" id="theme">
  <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap">
  <style>
    :root {
      --seekout-blue: #4A90D9;
      --seekout-teal: #2DD4BF;
      --accent-purple: #A78BFA;
      --accent-orange: #FB923C;
      --bg-dark: #0f172a;
      --bg-card: rgba(255, 255, 255, 0.05);
      --text-muted: #94a3b8;
    }

    .reveal {
      font-family: 'Inter', system-ui, -apple-system, sans-serif;
      font-size: 32px;
      color: #e2e8f0;
    }

    .reveal .slides { text-align: left; }
    .reveal .slides section { padding: 40px 60px; }

    .reveal h1, .reveal h2, .reveal h3 {
      font-family: 'Inter', system-ui, sans-serif;
      font-weight: 700;
      text-transform: none;
      letter-spacing: -0.02em;
      color: #f1f5f9;
    }

    .reveal h1 { font-size: 2.4em; line-height: 1.1; }
    .reveal h2 { font-size: 1.6em; margin-bottom: 0.6em; line-height: 1.2; }
    .reveal h3 { font-size: 1.1em; color: var(--seekout-teal); margin-bottom: 0.4em; }

    .reveal p, .reveal li {
      font-size: 0.72em;
      line-height: 1.6;
      color: #cbd5e1;
    }

    .reveal ul { list-style: none; padding-left: 0; }

    .reveal ul li {
      position: relative;
      padding-left: 1.4em;
      margin-bottom: 0.5em;
    }

    .reveal ul li::before {
      content: '\2192';
      position: absolute;
      left: 0;
      color: var(--seekout-teal);
      font-weight: 600;
    }

    .reveal .highlight { color: var(--seekout-teal); font-weight: 600; }
    .reveal .highlight-blue { color: var(--seekout-blue); font-weight: 600; }

    .reveal .title-slide h1 {
      font-size: 2.8em;
      background: linear-gradient(135deg, #f1f5f9, var(--seekout-teal));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .reveal .title-slide .meta {
      font-size: 0.55em;
      color: var(--text-muted);
      margin-top: 1.5em;
    }
  </style>
</head>
<body>
  <div class="reveal">
    <div class="slides">

      <!-- TITLE SLIDE -->
      <section class="title-slide" data-background-color="#0f172a">
        <h1>TITLE</h1>
        <div class="meta">
          <p><strong style="color: #e2e8f0;">AUTHORS</strong></p>
          <p>DATE</p>
        </div>
      </section>

      <!-- Add slides here -->

    </div>
  </div>

  <script src="https://cdn.jsdelivr.net/npm/reveal.js@5.1.0/dist/reveal.js"></script>
  <script>
    Reveal.initialize({
      hash: true,
      slideNumber: true,
      width: 1280,
      height: 720,
      margin: 0.04,
      transition: 'slide',
      transitionSpeed: 'default',
      backgroundTransition: 'fade',
      center: true,
      controls: true,
      progress: true,
      history: true,
    });
  </script>
</body>
</html>
```

#### `slides.md`

Create a companion markdown file with the presentation outline:

```markdown
# TITLE

**Date**: YYYY-MM-DD
**By**: AUTHORS

---

## Slide 1: ...

---
```

### 3. Register in Hub

Add an entry to the `presentations` array in the root `index.html`:

```javascript
{
  slug: 'SLUG',
  title: 'TITLE',
  description: 'DESCRIPTION',
  date: 'YYYY-MM-DD',
  authors: 'AUTHORS',
  tags: ['Tag1'],
},
```

### 4. Verify

- Confirm `presentations/<slug>/index.html` exists and is valid HTML
- Confirm `presentations/<slug>/slides.md` exists
- Confirm the registry entry in root `index.html` has the correct slug matching the folder name
