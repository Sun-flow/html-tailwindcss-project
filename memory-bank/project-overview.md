# Project Overview

**Date:** 2026-10-14

## What This Project Is

An **artist portfolio website** — a polished, production-ready static site built from the [4Geeks Academy HTML Hello](https://github.com/4GeeksAcademy/html-hello) starter template. The site showcases an artist's work in a clean, gallery-focused design with SEO/GEO optimization. It is a professional client engagement, not a tutorial or experiment.

## What This Project Is Not

- ❌ Not a JavaScript application — zero JS runtime dependencies.
- ❌ Not a CMS or dynamic site — purely static HTML + CSS.
- ❌ Not a tutorial or learning scaffold (though the upstream template is); the template was used as a starting point and has been adapted for production use.
- ❌ Not using any CSS preprocessors or build steps.

## Goals

1. Serve a fast, accessible, mobile-first portfolio gallery.
2. Maximize discoverability via semantic HTML, structured data, and Open Graph / Twitter Card meta tags.
3. Provide a professional-grade browsing experience: keyboard-navigable, screen-reader friendly, responsive across all viewports.
4. Keep the stack minimal (HTML + Tailwind CSS + Flask dev server) for easy maintenance and zero build overhead.

## Scope & Boundaries

| Scope | Out of Scope |
|---|---|
| Static HTML pages with semantic markup | Server-side rendering or SSG |
| Tailwind CSS via CDN (utility-first) | Custom CSS build pipeline |
| Flask-based dev server (`server.py`) | Production deployment config |
| SEO meta tags, Open Graph, JSON-LD | Analytics, tracking scripts |
| Accessibility (ARIA, keyboard nav, alt text) | JS-based interactivity |
| `.agents/rules/` — agent behavioral guidelines | Third-party integrations |

## Definition of Done

- ✅ No `div`-only page structure — all sections use semantic elements (`header`, `nav`, `main`, `section`, `article`, `figure`, `footer`).
- ✅ Single `<h1>` per page with logical heading hierarchy.
- ✅ All images have descriptive `alt` text (or `alt=""` if decorative).
- ✅ ARIA labels on interactive elements without visible text.
- ✅ Tailwind utility classes via external stylesheet (no inline `<style>` blocks).
- ✅ Flexbox layout only — no `float` or `inline-block` for structure.
- ✅ Responsive at mobile, tablet, and desktop breakpoints.
- ✅ Open Graph, Twitter Card, and JSON-LD structured data present in `<head>`.

## Key Files

| File | Description |
|---|---|
| `index.html` | Main portfolio page — the primary entry point. Contains hero, about, career, and shows sections. |
| `styles.css` | Custom CSS supplementing Tailwind — 7 features: design tokens, smooth scroll + navbar offset, masonry gallery, image hover, timeline polish, print styles, shimmer placeholders |
| `server.py` | Flask dev server; serves static files, falls back to 404 page; port 3000 |
| `AGENTS.md` | Project brief for AI agents; references `.agents/rules/` |
| `.agents/rules/semantic-html.md` | Agent rule: semantic elements over divs |
| `.agents/rules/layout.md` | Agent rule: Tailwind CSS, Flexbox, no floats |
| `.agents/rules/accessibility.md` | Agent rule: ARIA, alt text, keyboard nav |
| `.vscode/settings.json` | Editor config: Prettier formatter, Markdown preview |
| `learn.json` | Template metadata (4Geeks Academy) |
| `README.md` / `README.cn.md` / `README.es.md` | Multilingual readme (English / Chinese / Spanish) |
| `memory-bank-generator-prompt.md` | The prompt used to generate this memory bank |

## High-Level Architecture

```
User Browser
    │
    ▼
Flask dev server (server.py :3000)
    │
    ▼
Static File Responder
    ├── index.html          ← main page (semantic HTML + Tailwind classes)
    ├── styles.css          ← (optional) custom CSS supplementing Tailwind
    └── assets/             ← images, icons, content.md (content source), any static assets
```

The Flask server runs in debug mode with caching disabled. It serves `index.html` at `/` and falls back to a 404 page with the `rigo-baby.jpeg` image when a file is missing. If `app.py` exists, it runs that as a render script instead.

**Data flow:** No backend — all content is embedded in static HTML. The site is entirely client-side; the server is purely for local development.
