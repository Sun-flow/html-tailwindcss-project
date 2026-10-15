# PageSpeed Insights — Doctype & Meta Description Error Exploration

**Date:** 2026-10-15
**Status:** Diagnosis complete — both flags are a GitHub Codespaces proxy artifact, not a defect in `index.html`
**Scanned URLs:**
- `https://refactored-garbanzo-jjp4449w4wjf5565-3000.app.github.dev/` (Codespaces public forward)
- PSI report 1: `.../uhc91vb6hm` (captured Oct 15, 2026 02:24 AM)
- PSI report 2: `.../i1fg1wufhy` (fresh scan, same flags)

---

## 1. Summary

PageSpeed Insights (PSI) reports two recurring failures for the public Codespaces URL:

| # | Category | Flag | Recurrence |
|---|---|---|---|
| 1 | Best Practices (96) | *"Page lacks the HTML doctype, thus triggering quirks-mode"* | Old scan ✅ and fresh scan ✅ |
| 2 | SEO (90) | *"Document does not have a meta description"* | Old scan ✅ and fresh scan ✅ |

The local file and the page served internally are both correct. **The flags originate from GitHub's port-forwarding interstitial page** ("You are about to access a development port served by someone's codespace"), which PSI's fresh, cookie-less headless browser lands on instead of the portfolio. That GitHub-generated page has no `<!DOCTYPE html>` and no `<meta name="description">`.

---

## 2. Scores (for context)

| Category | Score |
|---|---|
| Performance | 100 (FCP 0.4s, LCP 0.4s, TBT 0ms, CLS 0, SI 0.4s) |
| Accessibility | 95 (1 issue — contrast; **intentionally out of scope** per request, see §7) |
| Best Practices | 96 (1 issue — doctype) |
| SEO | 90 (1 issue — meta description) |
| Agentic Browsing | 2/2 |

---

## 3. Evidence that `index.html` is correct

### 3.1 Served bytes (internal + authenticated external fetch)
Raw head of the document served at `/`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  ...
  <meta name="description" content="Portfolio of [Artist Name], a [medium/art form] artist based in [location]. Explore a curated collection of works, exhibition history, and upcoming shows." />
```

- `<!DOCTYPE html>` present, uppercase, first line (verified via hex dump: `3c21 444f ...`, no BOM).
- Meta description present and **non-empty** (1 match on live URL).
- Full `<head>` includes charset, viewport, keywords, author, Open Graph, Twitter Card, JSON-LD.

### 3.2 Lighthouse audit source logic (positive proof it *should* pass)

**Doctype audit** — `GoogleChrome/lighthouse` `core/audits/dobetterweb/doctype.js`:
Fails **only** when:
- `document.doctype` is `null` → "Document must contain a doctype"
- `documentCompatMode` is quirks/limited-quirks
- `doctype.publicId` or `doctype.systemId` is non-empty
- `doctype.name !== 'html'`

A standard `<!DOCTYPE html>` → `name='html'`, empty `publicId`/`systemId`, `CSS1Compat` → **passes** (score 1). Confirmed by the audit's own unit tests (`doctype-test.js`).

**Meta-description audit** — `core/audits/seo/meta-description.js`:
Fails **only** when the tag is absent, or `content.trim()` is empty. There is **no placeholder detection, no keyword check, no length check**. A non-empty `content` **always passes**. Confirmed by `meta-description-test.js` (`'description text'` → score 1).

### 3.3 Note on bracketed placeholder text (corrected earlier assumption)
Bracketed values like `[Artist Name]` are **valid, non-empty text** to Lighthouse/Google. They are *not* "treated as placeholder." The original "placeholders trigger the failure" explanation was an unverified assumption and is **retracted**; evidence-driven verification (above) supersedes it.

---

## 4. Root cause: GitHub Codespaces interstitial

Fetching the public URL from a fresh, cookie-less client (simulating PSI) returns **GitHub's warning page**, not the portfolio:

> **"You are about to access a development port served by someone's codespace** … Only continue to visit the website if you trust whoever sent you the link."

As HTML, that page:
- has **no `<!DOCTYPE html>`** → triggers the doctype flag (quirks-mode)
- has **no `<meta name="description">`** → triggers the SEO flag

### Mechanism
- GitHub forwards visitors through this interstitial **once per session**, then sets a cookie (`set-cookie: .Tunnels.Relay.WebForwarding.Cookies=...; Partitioned`).
- A human clicks **Continue** in a browser and thereafter sees the real site.
- **PSI runs a fresh headless browser on every scan with no cookies** → it always lands on the interstitial, never the portfolio → both audits fail on *every* run, old or new.

### Corroborating headers
```
set-cookie: .Tunnels.Relay.WebForwarding.Cookies=...; Partitioned
x-robots-tag: noindex, nofollow
```

> Note: `gh codespace ports` lists port 3000 as **public**, yet the interstitial still appears for cold sessions. The `noindex` header is injected by the forward regardless.

---

## 5. Are there other pages in the repo that would be flagged?

**No real pages.** Enumerated:

| Page | Source | Doctype | Meta description | Flagged? |
|---|---|---|---|---|
| `index.html` | repo, the **only** `.html` file (confirmed via `git ls-files` + `find`) | ✅ `<!DOCTYPE html>` | ✅ present, non-empty | **No** (was never the scanned doc) |
| Flask 404 page | auto-generated in `server.py:33` (bare ~100-byte string) | ⚠️ lowercase `<!doctype html>` (no `<html>`/`<head>`) | ❌ none | Would trip both audits **if** a dead route were scanned, but it has zero SEO value — intentionally out of scope (see previous 404 discussion). |

No other `.html`/`.php` files are tracked or present on disk.

---

## 6. Can the HTML "fix" these flags at this URL?

**No.** The interstitial sits in front of `index.html`; no change to the HTML can influence what PSI sees through the forward. Correct remediations:

| Option | Result |
|---|---|
| **Deploy to GitHub Pages** (free, permanent, no interstitial) | ✅ PSI scans the real page → both audits pass. Recommended end-state for a portfolio. |
| Re-run PSI against the `github.io` / custom domain URL after deploy | Confirm both audits clear (score 100 for SEO/Best-Practices dimensions). |
| Keep the Codespaces URL for dev | Fine for humans; automated scanners will keep hitting the interstitial — treat the flags as known noise at that URL. |

---

## 7. Out-of-scope notes (for future reference)

- **Accessibility contrast** (Score 95): measured — `text-stone-400` (#a8a29e) on `stone-50`/white/`stone-100` yields ≈ 2.31–2.52:1, **fails WCAG AA** (3:1 large / 4.5:1 normal). This is a **real** accessibility issue but the user explicitly requested it be ignored as non-technical for this exploration. Fix if ever revisited: bump caption/timestamp text to `text-stone-500` or `text-stone-600`.
- **Trust & Safety flags** (from the same Best-Practices section: CSP, HSTS, COOP, XFO/clickjacking, Trusted Types): expected for a static template served without security headers; not investigated here.

---

## 8. Key takeaways / lessons

1. **Verify against source before concluding.** Both "errors" are explained by Lighthouse's actual audit logic and GitHub's proxy behavior — not by the page markup.
2. **Bracketed placeholders are valid content** for lighthouse audits; do not "fix" SEO flags by changing them.
3. **PSI + Codespaces public URL is an invalid test context** for doctype/meta audits due to the once-per-session interstitial + fresh headless browser.
4. **The real fix is deployment**, not markup edits.