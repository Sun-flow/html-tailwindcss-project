# AGENTS.md — Project Brief

## Mandatory: Read the Memory Bank First

**Before doing any work in this repository, read EVERY file in `memory-bank/`.**  
Your memory resets between sessions; the memory bank is your only persistent link to prior work.

Start with `memory-bank/document-plan.md` → `memory-bank/project-overview.md` → `memory-bank/current-status.md` → `memory-bank/changelog.md` for a ten-second orientation.

## Overview

This is a **portfolio website** for an **artist** to showcase their work.  
Built as a static HTML + CSS site in this repository.

Treat this as a professional client engagement — the site must be polished, performant, and production-ready.

## Core Directives

### 1. Follow Agent Rules

All code must comply with the rules in `memory-bank/` and `.agents/rules/`:

- **`memory-bank/conventions.md`** — Architecture, naming, and invariant conventions.
- **`.agents/rules/semantic-html.md`** — Use proper semantic tags, never div-only structure.
- **`.agents/rules/layout.md`** — Separate CSS file, Flexbox layout, no floats/inline-block for structure.
- **`.agents/rules/accessibility.md`** — ARIA labels, roles, alt text, keyboard navigation.

### 2. SEO & GEO Optimization

Maximize discoverability. This is critical to the artist's success:

- Proper `<head>` meta tags (description, keywords, Open Graph, Twitter Card).
- Semantic heading hierarchy for crawlers.
- Structured data (JSON-LD) where applicable.
- Fast load times (minimal HTTP requests, efficient CSS).
- Mobile-first responsive design.

### 3. Layout Requirements

- Clean, gallery-focused design that puts the artwork front and center.
- Fully responsive — looks great on mobile, tablet, and desktop.
- Accessible to all users including screen readers.

### 4. Tone & Quality

- Code as a **professional marketing agency** — no shortcuts, no placeholders, no "TODO" stubs.
- Every element serves a purpose: visual, functional, or discoverability.
- Assume the client is paying for excellence.

## Stack

- **HTML** — semantic markup
- **CSS** — **Tailwind CSS** (utility-first, via external stylesheet)
- **Layout** — Flexbox utilities, CSS custom properties
- **No JS** — keep it lightweight and maintainable
