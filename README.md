# Spendly — Expense Tracker

A personal expense tracker web app built with Flask and SQLite, developed step by step with the help of Claude Code.

## Features

**Done**
- Landing page
- Register and login pages (UI only)

**Planned**
- Step 1 — Database setup (`database/db.py`: `get_db`, `init_db`, `seed_db`)
- Step 3 — Logout
- Step 4 — Profile page
- Step 7 — Add expense
- Step 8 — Edit expense
- Step 9 — Delete expense

## Tech stack

- Python 3, Flask 3.1
- SQLite
- Jinja2 templates, plain CSS and JavaScript
- pytest + pytest-flask for testing

## Project structure

```
expense-tracker/
├── app.py              # Flask app and routes
├── database/
│   └── db.py           # SQLite connection, schema, seed data
├── static/
│   ├── css/style.css
│   └── js/main.js
├── templates/          # base, landing, login, register
└── requirements.txt
```

## Getting started

```bash
git clone https://github.com/jaydeepsatre446-png/Expense-Tracker-with-the-help-of-claude-coding.git
cd Expense-Tracker-with-the-help-of-claude-coding

python -m venv venv
# Windows (PowerShell): .\venv\Scripts\Activate.ps1
# Windows (Git Bash):   source venv/Scripts/activate
# macOS / Linux:        source venv/bin/activate

pip install -r requirements.txt
python app.py
```

Open http://localhost:5001 in your browser.

## Running tests

```bash
pytest
```
