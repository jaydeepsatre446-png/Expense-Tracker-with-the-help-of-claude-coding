# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Spendly — a personal expense tracker built with Flask 3.1 + SQLite, Jinja2 templates, and plain CSS/JS (no frontend build step, no ORM). It is being built incrementally as a numbered sequence of "Steps" (tracked in README.md under Features → Planned). Placeholder code and comments reference these step numbers; when implementing a step, replace the corresponding placeholder and update README.md's Done/Planned lists.

## Commands

```bash
# Setup (Windows PowerShell: .\venv\Scripts\Activate.ps1; Git Bash: source venv/Scripts/activate)
python -m venv venv
pip install -r requirements.txt

python app.py                      # dev server on http://localhost:5001 (debug mode)
pytest                             # run all tests (pytest + pytest-flask)
pytest tests/test_file.py::test_name   # run a single test
```

No tests or `tests/` directory exist yet; pytest-flask expects an `app` fixture in `conftest.py` when tests are added. There is no linter configured.

## Architecture

- **`app.py`** — single module holding the Flask `app` and every route. No blueprints. Routes are split into two sections: implemented pages (landing, register, login, terms, privacy — currently GET-only, render templates, no form handling) and **placeholder routes** returning plain strings like `"Logout — coming in Step 3"` (`/logout`, `/profile`, `/expenses/add`, `/expenses/<id>/edit`, `/expenses/<id>/delete`).
- **`database/db.py`** — `get_db()` (SQLite connection with `row_factory` and `PRAGMA foreign_keys` enabled), `init_db()` (`CREATE TABLE IF NOT EXISTS` for `users` and `expenses`), `seed_db()` (demo user + sample expenses, skipped if users exist), and the `CATEGORIES` list. `app.py` calls `init_db()` and `seed_db()` on startup. The DB file `spendly.db` (project root) is gitignored.
- **Templates** — every page extends `templates/base.html`, which provides the navbar, footer, and blocks `title`, `head` (page-specific CSS), `content`, and `scripts` (page-specific JS). `landing.html` pulls in `static/css/landing.css` via the `head` block; everything else uses the shared `static/css/style.css`. Use `url_for(...)` for links and static assets.
- **`static/js/main.js`** — empty stub loaded on every page; page-specific scripts go in the template's `scripts` block.
- Styling: DM Serif Display / DM Sans fonts from Google Fonts; currency context is Indian rupees.
