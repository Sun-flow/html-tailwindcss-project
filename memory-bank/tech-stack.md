# Tech Stack

**Date:** 2026-10-14

> All versions and commands verified against actual files in the repository.

## Languages & Frameworks

| Technology | Version (verified) | Notes |
|---|---|---|
| HTML5 | — | Semantic markup per `.agents/rules/semantic-html.md` |
| CSS | — | Tailwind utility classes, no preprocessors |
| Tailwind CSS | v4 (via CDN) | Loaded from `https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4` |
| Python | 3.x (system) | Runtime for Flask dev server |
| Flask | latest (pip) | Lightweight WSGI server for local development |

## Dependencies

### Runtime (pip)

- **Flask** — installed via `pip3 install flask` (no `requirements.txt`; ad-hoc install)

### CDN (browser)

- **Tailwind CSS v4** — via `<script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>`

## No Lockfiles or Build Tools

- ❌ No `package.json` or `package-lock.json`
- ❌ No `requirements.txt`
- ❌ No `Cargo.toml`, `Dockerfile`, or `Makefile`
- ❌ No bundler, transpiler, or build step

## Tooling & Editor Config

| Tool | Purpose | Source |
|---|---|---|
| Prettier (esbenp.prettier-vscode) | Code formatter | `.vscode/settings.json` — `editor.formatOnSave: true` |
| VS Code | Recommended editor | `.vscode/settings.json` |
| Markdown preview | `.md` files open in preview by default | `workbench.editorAssociations` in settings |

## CI / Git

- **Git** — single `main` branch; 2 commits as of 2026-10-14
- ❌ No CI/CD workflows (no `.github/` directory)
- Remote: `origin` (set up by user)

## Commands

All commands run from the repository root (`/workspaces/html-tailwindcss-project`).

### Install Flask (once)

```bash
pip3 install flask
```

### Start Dev Server

```bash
python3 server.py
```

Serves at `http://0.0.0.0:3000`. Debug mode enabled; caching disabled.

### Verify Server Is Running

```bash
curl -s -o /dev/null -w "%{http_code}" http://localhost:3000
```

Expected response: `200` if `index.html` exists, otherwise `200` (Flask returns the 404 HTML page with HTTP 200 — see `server.py:18-21`).

## Environment

No `.env` file or environment variables required. The server binds to `0.0.0.0:3000` hardcoded (`server.py:31`).
