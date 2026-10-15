# Document Plan

**Date:** 2026-10-14

This is the **index/hub file** for the memory bank. Every file in `memory-bank/` and key documentation is listed here with its purpose.

## Memory Bank Files

| File | Purpose | Last Updated |
|---|---|---|
| `project-overview.md` | What the project is, its goals, scope, non-goals, key files, and high-level architecture | 2026-10-14 |
| `tech-stack.md` | Languages, frameworks, dependencies, tooling, commands — all verified against actual manifests | 2026-10-14 |
| `current-status.md` | What works, known gaps, blockers, next priorities, recent activity | 2026-10-14 |
| `document-plan.md` | **[This file]** Inventory of all bank/docs files and maintenance rules | 2026-10-14 |
| `changelog.md` | Human-readable change history in Keep-a-Changelog format | 2026-10-14 |
| `conventions.md` | Architecture, patterns, naming rules, and invariants | 2026-10-14 |
| `review-edits/fact-checker-review.md` | Fact-checker validation: verified all quantitative claims against live repo | 2026-10-14 |
| `review-edits/consistency-checker-review.md` | Consistency-checker validation: cross-file agreement and freshness | 2026-10-14 |
| `archive/` | Superseded content — archive, don't delete | 2026-10-14 |
| `pagespeed/error-exploration.md` | PSI diagnosis: doctype & meta description flags are a GitHub Codespaces interstitial artifact, not an `index.html` defect | 2026-10-15 |
| `to-do/personalize_gromb.md` | Handoff checklist for the site personalization task + user answers to blocking questions | 2026-10-15 |

## Root Documentation

| File | Purpose |
|---|---|
| `AGENTS.md` | Project brief for AI agents; the entry point that points to `memory-bank/` and `.agents/rules/` |
| `README.md` | Human-facing readme (English) — setup instructions for 4Geeks template |
| `README.cn.md` | Human-facing readme (Chinese) |
| `README.es.md` | Human-facing readme (Spanish) |
| `learn.json` | Template metadata for 4Geeks Academy |
| `memory-bank-generator-prompt.md` | The prompt used to generate this memory bank — an init instruction for AI agents |
| `assets/content.md` | Human-readable content source: all placeholder text extracted from `index.html` by section, for editing and autopopulation — now mirrors the **jazz dance instructor** site for gromb | 2026-10-15 |
| `assets/gromb-bio.md` | Brief professional bio for gromb (SF jazz dance instructor, Blues & Balboa, they/them); source of truth for hero/About/JSON-LD copy | 2026-10-15 |
| `styles.css` | Custom stylesheet complementing Tailwind — 7 features: design tokens, smooth scroll + navbar offset, masonry gallery, image hover, timeline polish, print styles, shimmer placeholders |

## Agent Configuration

| File | Purpose |
|---|---|
| `.agents/README.md` | Overview of `.agents/` directory structure |
| `.agents/rules/semantic-html.md` | Rule: use semantic elements, no div-only structure |
| `.agents/rules/layout.md` | Rule: Tailwind CSS, Flexbox, no floats |
| `.agents/rules/accessibility.md` | Rule: ARIA labels, alt text, keyboard nav |

## Maintenance Rules

1. **Single source of truth** — each fact lives in exactly one file; others link to it.
2. **Evidence-only** — every claim traces to a real file, manifest, or command output. Mark unverifiable items with ❓.
3. **Date everything** — ISO-8601 date on every entry/snapshot.
4. **Archive, don't delete** — move superseded content to `archive/` with a one-line note.
5. **One topic per file** — if a file straddles two concerns, split it and update this plan.
6. **Update this file** whenever a file is added or removed from the bank.
