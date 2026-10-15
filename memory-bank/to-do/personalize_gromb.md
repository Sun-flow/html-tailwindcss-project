# To-Do / Handoff — Personalize Site for [Gromb], Jazz Dance Instructor

**Created:** 2026-10-15
**Status:** In progress
**Owner:** AI agent + user
**Purpose:** This file is the **handoff contract** for the current task. If work is interrupted, a future agent reads the checkboxes below, resumes the next unchecked item, and updates statuses as it goes. See `memory-bank/common-tasks.md` (if it exists) for recurring guidance.

> **How to use:** each item has a `[ ]`/`[x]` checkbox, a one-line goal, and the exact files involved. Mark `[x]` **only** after the item is actually done and verified (see "Verification" under each item).

---

## Task Summary (one paragraph)

Transform the placeholder **artist portfolio** (`index.html`, `assets/content.md`) into the **professional website for [Gromb]**, a Bay Area Jazz dance instructor who specializes in teaching **Blues** and **Balboa** and works **events** (rather than an artist playing shows). This includes:

1. a new brief bio in `assets/`,
2. re-framing all site language from "artist/shows/gallery" to "dance instructor/events/classes",
3. re-purposing the Career section into a timeline of **dance lineage milestones** (2016 Lindy Hop → 2018 Blues → 2022 Balboa), each carrying a **Home Scene** marker plus a **tags** list for accolades/achievements (keeping the existing tag-pill system from the template).

All work must honor repo conventions: semantic HTML (`.agents/rules/semantic-html.md`), Tailwind utility classes, a11y (`.agents/rules/accessibility.md`), evidence-driven memory-bank updates (`memory-bank/conventions.md`).

---

## Item 1 — Sync local `main` with `origin/main`
- [x] Goal: pull the latest remote history before editing.
- Files: `(none — git)`
- Steps:
  - `git pull --ff-only origin main` (local was 1 commit behind at start: `efccab5` vs `origin/main`).
- Verification: `git status` shows "up to date with origin/main"; working tree clean.

## Item 2 — Create Gromb's bio in `assets/`
- [x] Goal: produce a **brief, professional bio** for gromb, SF jazz dance instructor specializing in **Blues** and **Balboa**, who works dance **events**.
- Files: **create** `assets/gromb-bio.md`
- Content to include (draft, to be refined while writing):
  - Role: Jazz dance instructor based in the Bay Area; teaches Blues and Balboa.
  - Focus: teaches at workshops/events (interchangeable "classes & events" vocabulary — **no** "shows/gallery/paintings").
  - Footprint: dance community — home scenes, traveling events, social dancing.
  - Add clearly-marked `[editable]` placeholders for facts only the real Gromb knows (pronouns, years teaching, event list, social links, city specifics).
- Verification: file exists; reads as a coherent dance-instructor bio (not artist language); follows lowercase-hyphen naming (`gromb-bio.md`).

---

## Item 3 — Adapt `index.html` language to a dance instructor working events
- [x] Goal: replace every "artist / artwork / exhibition / shows / gallery" phrasing with dancer/instructor/events/classes phrasing, mirroring gromb's bio.
- Files: **edit** `index.html`
- Specific edits (all done 2026-10-15):
  - [x] `<title>` → `gromb — Jazz Dance Instructor`
  - [x] `<meta name="description">` → instructor + Blues/Balboa + events; drop "contemporary art"
  - [x] `<meta name="keywords">` → dance terms
  - [x] `og:*` + `twitter:*` title/description → instructor phrasing
  - [x] JSON-LD `Person` → `jobTitle: Dance Instructor`; `knowsAbout: Jazz dance, Blues, Balboa, Lindy Hop`
  - [x] Navbar: `Upcoming Shows` → `Upcoming Events`; `Career` → `Dance Lineage`
  - [x] Hero: `h1` name `gromb`, tagline `Jazz Dance Instructor · San Francisco`, statement = dance version
  - [x] About section: 3 paragraphs from the bio (confirmed facts)
  - [x] Career section ↔ Item 4 (lineage timeline + Home Scenes + tags) — done
  - [x] Shows section → **Events** section (`#shows` → `#events`): event/class/workshop cards
  - [x] Footer: copyright `gromb` + social placeholders kept
  - [x] Comments reworded to instructor/event guidance
- Keep: **one `<h1>`**, semantic tags, one `<time>` per timeline entry, `aria-label`s, tag-pill `<ul>` system, Tailwind classes, `styles.css` classes (timeline, shimmer).
- Verification: open page in browser; no "artist/shows/gallery/opening reception" wording remains; sections render.

---

## Item 4 — Career section → dance lineage timeline + Home Scenes + accolades tags
- [x] Goal: convert the timeline to **dance lineage milestones**: 2016 Lindy Hop → 2018 Blues → 2022 Balboa, each with **Home Scene** list and **accolade** tag pills.
- Files: **edit** `index.html` (`#career`) and **edit** `assets/content.md` (`## CAREER SECTION`)
- Structure per timeline entry (keep the existing `<article>`/`timeline-dot`/`<time>` markup):
  - `<time>` = the year (2016, 2018, 2022)
  - Heading = the discipline learned (e.g. "Lindy Hop"), not an exhibition title
  - Paragraph = how/where the journey began (home scene, mentor/class, event)
  - **Home Scene** = a labeled field ("Home Scene: [City/Studio]") — user said *"Replace the descriptions with a list of 'Home Scenes'"*, i.e. Home Scenes become prominent per-milestone markers
  - Tags `<ul>` = accolades/achievements (mimic how award/residency/solo-exhibition tags worked): e.g. for 2016 "First social dance", "Home Scene: SF"; 2018 "Blues focus", "Home Scene: Oakland"; 2022 "Balboa focus", "Home Scene: Bay Area" — use placeholder-pill style until we have real facts (mark unknown facts with bracketed editable placeholders).
  - Add 1–2 blank template entries with `[editable]` guidance so Gromb can add more years.
- Verification: 3+ lineage entries render with year, title, desc, Home Scene, and tag pills; tag-pill system visually consistent with the old award/residency tags.

---

## Item 5 — Adapt `assets/content.md` to match the instructor site
- [x] Goal: keep the content source sheet in sync with `index.html` changes.
- Files: **edit** `assets/content.md`
- Steps:
  - Rewrite header instructions + every section (PAGE HEAD, JSON-LD, HERO, ABOUT, CAREER, EVENTS, FOOTER) with dance-instructor fields and values.
  - CAREER section: document the lineage structure (Year / Milestone / Description / **Home Scene** / Accolade tags) with the 2016/2018/2022 rows.
  - Replace "SHOWS/EXHIBITIONS" section with "EVENTS" (workshops, classes, socials) — keep the same card field table.
  - Update the Quick-Edit Summary placeholder counts (Artist→Gromb, medium art form→dance, shows→events).
- Verification: every heading that exists in `index.html` has a matching row/table in `content.md`; no artist-only terms remain.

---

## Item 6 — Update memory bank (changelog, document-plan, current-status)
- [x] Goal: keep the persistent memory bank evidence-true.
- Files: **edit** `memory-bank/changelog.md`, `memory-bank/document-plan.md`, `memory-bank/current-status.md`
- Steps:
  - `changelog.md`: add `[Added]` entries (`assets/gromb-bio.md`, this to-do file) and `[Changed]` entries (`index.html`, `assets/content.md`) with today's date 2026-10-15; archive or note the "artist template" framing if superseded.
  - `document-plan.md`: register `assets/gromb-bio.md` and `memory-bank/to-do/personalize_gromb.md` in tables; note `index.html`/`content.md` purpose changed from artist→instructor.
  - `current-status.md`: update What Works / Next Priorities / Recent Activity rows to reflect personalization; resolve "Fill in artist-specific content" gap.
- Verification: grep the three files for "Gromb" / "dance instructor"; all dates `2026-10-15`.

---

## Item 7 — Browser-verify, then commit
- [x] Goal: confirm the page renders clean and the site is committed on `main`.
- Steps:
  - Run `python3 server.py` (background), open `http://127.0.0.1:3000` in the browser; check hero/about/career/events sections + responsive (mobile notch).
  - Fix any obvious layout/ACSS issues found.
  - `git add -A && git commit -m "..."` (descriptive, e.g. `feat: personalize site for Gromb, jazz dance instructor`).
  - `git push origin main`.
- Verification: browser shows instructor site; `git status` clean; commit message follows `feat/docs:` convention.

---

## Open questions for the human (blockers if unanswered)

| # | Question | Why it matters | Answer (2026-10-15) |
|---|---|---|---|
| 1 | Real name spelling: **Gromb**? A stage/handle? Legal name? | Used in `h1`, title, JSON-LD, footer. | `gromb` — fine for now, **lower case** ✅ |
| 2 | Pronouns + short location? | Bio + tagline + JSON-LD. | `they/them`, `San Francisco` ✅ |
| 3 | Real "Home Scenes" per milestone? | Required by user for the lineage timeline. | `Oakland`, `DC`, `Triangle NC`, `SF` ✅ — assigned across milestones as editable (see Item 4) |
| 4 | Real accolades for each year? | Fills the tags pills. | keep as placeholder for now ⏸ |
| 5 | Social/contact links? | Hero/about/footer/JSON-LD. | will give later ⏸ keep placeholders |
| 6 | Event names/dates for the Events section? | Events cards. | keep as editable placeholder ⏸ |

> If an item stalls on an unanswered question, mark it `[ ]` with a note "blocked on Q#", leave placeholders in the file, and proceed to the next item that isn't blocked.

---

## Progress Log

- **2026-10-15** — Handoff doc created (all 7 items).
- **2026-10-15** — Item 1 done: pulled `origin/main` (fast-forward `efccab5..c9a6252`, added `pagespeed artist portfolio.png`).
- **2026-10-15** — User answered Q1–Q6 (see table above). Key facts: `gromb` (lowercase), `they/them`, `San Francisco`, Home Scenes `Oakland / DC / Triangle NC / SF`; accolades, socials, events = placeholders for now.
- **2026-10-15** — Item 2: `assets/gromb-bio.md` created, then refreshed with confirmed facts (gromb/they-them/SF + Home Scenes).
- **2026-10-15** — Items 3 & 4 done: `index.html` fully re-framed → instructor; Career → **Dance Lineage** timeline (2016 Lindy/Oakland+SF, 2018 Blues/DC, 2022 Balboa/Triangle NC) with Home Scene lists + accolade tag pills; `#shows` → `#events` (Upcoming Events); footer `gromb`.
- **2026-10-15** — Item 5 done: `assets/content.md` rewritten (HEAD/JSON-LD/HERO/ABOUT/DANCE LINEAGE/EVENTS/FOOTER + Quick-Edit) to mirror the instructor site.
- **2026-10-15** — Item 6 done: `changelog.md`, `document-plan.md`, `current-status.md` updated (gromb rows, dates 2026-10-15).
- **2026-10-15** — Item 7 done: browser-verified (`gromb — Jazz Dance Instructor` title; hero/about/lineage/events render; no horizontal overflow at 375px; nav anchors land flush); committed + pushed to `main`.