# Changelog

All notable changes to this project's documentation and codebase.

**Format:** [Keep a Changelog](https://keepachangelog.com/en/1.1.0/)  
**Date format:** ISO-8601 (YYYY-MM-DD)

---

## [Unreleased]

### Added

- `assets/gromb-bio.md` — brief professional bio for gromb, San Francisco jazz dance instructor specializing in Blues & Balboa (they/them), with confirmed facts (name, pronouns, SF, Home Scenes Oakland/DC/Triangle NC/SF) and editable placeholders for TBD details — 2026-10-15
- `memory-bank/to-do/personalize_gromb.md` — handoff/handover to-do for the site personalization task; records user answers to blocking questions — 2026-10-15
- `styles.css` — custom stylesheet with 7 features: design tokens (CSS custom properties), smooth scroll + fixed-navbar anchor offset (`scroll-padding-top: 3.75rem`), CSS-only masonry gallery grid, card image hover (zoom + brightness), timeline polish (gradient line, hover-glow dots), `@media print` stylesheet, shimmer placeholder animation — 2026-10-14
- `assets/content.md` — human-readable content source: all placeholder text extracted from `index.html` by section, with placeholder→mapping tables — 2026-10-14

### Changed

- `index.html` — **personalized from artist portfolio → jazz dance instructor site for gromb** (San Francisco, they/them). Updated `<title>`, meta description/keywords, Open Graph & Twitter Card, JSON-LD (Person: Dance Instructor, knowsAbout Blues/Balboa/Lindy Hop); nav `Upcoming Shows → Upcoming Events`; hero tagline `Jazz Dance Instructor · San Francisco`; About Me paragraphs (dance journey + philosophy); `#shows` → `#events` with workshop/class/social card placeholders; footer name. **Career timeline → Dance Lineage timeline**: 2016 Lindy Hop (Home Scenes Oakland + SF), 2018 Blues (DC), 2022 Balboa (Triangle NC); kept the template's tag-pill system for Home Scenes and accolade tags; date placeholders remain — 2026-10-15
- `assets/content.md` — content source sheet rewritten to mirror the instructor site: PAGE HEAD / JSON-LD / HERO / ABOUT / DANCE LINEAGE / EVENTS / FOOTER + Quick-Edit updated with gromb's confirmed facts; Home Scenes + accolade-tag structure documented for lineage entries — 2026-10-15
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
