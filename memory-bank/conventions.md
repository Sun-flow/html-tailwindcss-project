# Conventions

**Date:** 2026-10-14

> Architecture, patterns, naming rules, and invariants preserved across sessions.

## HTML Conventions

### Semantic Structure (per `.agents/rules/semantic-html.md`)

- Every page must have exactly one `<h1>`, with subsequent headings in logical order (`<h2>` → `<h6>`).
- Use `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<footer>` for page structure — never `<div>`-only.
- Use `<figure>` + `<figcaption>` for images with captions; plain `<img>` for standalone images.
- Use `<ul>` / `<ol>` for lists of any kind (navigation links, gallery items, features).
- Use `<button>` for actions, `<a>` for navigation links.

### Tailwind Usage (per `.agents/rules/layout.md`)

- Apply all styling via Tailwind utility classes in the HTML markup.
- No inline `<style>` blocks — use either Tailwind classes or a linked external stylesheet.
- Extend with CSS custom properties (`--var-name`) in `styles.css` for theme values (colors, spacing, breakpoints) if needed.
- Use Flexbox (`flex`) for layout — never `float` or `display: inline-block` for structural positioning.

### Accessibility (per `.agents/rules/accessibility.md`)

- Add `role` attributes on landmark elements where the semantic HTML tag is ambiguous.
- Use `aria-label` on interactive elements (nav, buttons, search, icon-only links) lacking visible text.
- Every `<img>` must have descriptive `alt` text; use `alt=""` for purely decorative images.
- Maintain keyboard-navigable focus order; use `tabindex` only when necessary (ideally never).
- Use `aria-hidden="true"` on purely decorative SVGs and icons.

## SEO Conventions

- Every page `<head>` must include: `<title>`, `<meta name="description">`, Open Graph (`og:title`, `og:description`, `og:image`, `og:url`), Twitter Card (`twitter:card`, `twitter:title`, `twitter:description`, `twitter:image`).
- Include JSON-LD structured data (at minimum `"@type": "Person"` or `"@type": "WebSite"` as appropriate).
- Heading hierarchy must be logical for crawlers (one `<h1>`, properly nested).

## Naming

- HTML files: lowercase, kebab-case (e.g., `about-me.html`, not `aboutMe.html`).
- CSS files: lowercase, kebab-case.
- Image assets: lowercase, descriptive, hyphen-separated (e.g., `oil-painting-sunset.jpg`).
- Directory names: lowercase, no spaces.

## Invariants

- **No JavaScript runtime dependencies.** The site is pure HTML + CSS. If JS is ever added, it must be progressive enhancement only.
- **No build step.** Tailwind is loaded via CDN; no bundler, transpiler, or preprocessor.
- **Agent-facing vs human-facing separation.** Memory bank files (`memory-bank/`) are for AI agents; they are not documented in the human README. Human docs are in `README*.md` and `learn.json`.
- **Evidence-driven development.** Every claim in the memory bank must trace to a real file, manifest, or command output. Unverifiable items are marked ❓.
