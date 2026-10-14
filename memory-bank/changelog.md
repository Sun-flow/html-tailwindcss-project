# Changelog

All notable changes to this project's documentation and codebase.

**Format:** [Keep a Changelog](https://keepachangelog.com/en/1.1.0/)  
**Date format:** ISO-8601 (YYYY-MM-DD)

---

## [Unreleased]

### Added

- `styles.css` — custom stylesheet with 7 features: design tokens (CSS custom properties), smooth scroll + fixed-navbar anchor offset (`scroll-padding-top: 3.75rem`), CSS-only masonry gallery grid, card image hover (zoom + brightness), timeline polish (gradient line, hover-glow dots), `@media print` stylesheet, shimmer placeholder animation — 2026-10-14
- `assets/content.md` — human-readable content source: all placeholder text extracted from `index.html` by section, with placeholder→mapping tables — 2026-10-14
- `index.html` — portfolio template page with hero, about me, career timeline, and upcoming shows sections — 2026-10-14
- Memory bank initialized with core files: `project-overview.md`, `tech-stack.md`, `current-status.md`, `document-plan.md`, `changelog.md`, `conventions.md`, `archive/` — 2026-10-14
- `memory-bank-generator-prompt.md` added to repo root — 2026-10-14

### Changed

- `index.html` — UI refinements, all browser-verified: timeline dots realigned onto the center line (`.group`/`md:group-odd`/`md:group-even` pattern with `translate-x-1/2` for left/right halves); anchor offset tuned to exactly the fixed navbar height (60px) so targets land flush below the bar with no previous-section peek; section vertical padding trimmed (`#about` `pt-2 pb-6`, `#career` & `#shows` `py-6`); `shimmer` + `card-image-wrapper` classes applied to hero/about/show images — 2026-10-14

---

## [0.1.0] — 2026-10-14

### Added

- Initial project scaffold from 4Geeks Academy HTML Hello template (`c2914d1`)
- Flask dev server (`server.py`) with 404 fallback
- `README.md`, `README.cn.md`, `README.es.md` — multilingual documentation
- `learn.json` — template metadata
- `.vscode/settings.json` — Prettier formatter config, Markdown preview association
- `AGENTS.md` — project brief for AI agents
- `.agents/rules/semantic-html.md` — semantic element rule
- `.agents/rules/layout.md` — Tailwind/Flexbox rule
- `.agents/rules/accessibility.md` — ARIA/alt-text/keyboard rule
- `.agents/README.md` — agent directory overview
- Initial git history (2 commits on `main`)

[Unreleased]: https://github.com/your-org/artist-portfolio/compare/v0.1.0...HEAD
[0.1.0]: https://github.com/your-org/artist-portfolio/releases/tag/v0.1.0
