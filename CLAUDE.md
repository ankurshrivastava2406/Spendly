# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Spendly** is a Flask-based personal expense tracker. The project is structured as a step-by-step student exercise — many routes and the entire database layer are stubs to be implemented.

## Commands

```bash
# Run the development server (port 5001)
python app.py

# Run all tests
pytest

# Run a single test file
pytest tests/test_something.py

# Run a specific test
pytest tests/test_something.py::test_function_name
```

Dependencies are in `requirements.txt` (Flask, Werkzeug, pytest, pytest-flask). Use the `venv` or `expensetrack` conda environment.

## Architecture

### Entry point
`app.py` — Flask app, all routes defined here. No blueprints; everything is flat in one file.

### Database layer (`database/`)
`database/db.py` is the sole database module. It should expose three functions:
- `get_db()` — returns a SQLite connection with `row_factory` set and foreign keys enabled
- `init_db()` — creates all tables using `CREATE TABLE IF NOT EXISTS`
- `seed_db()` — inserts sample data for development

`database/__init__.py` is currently empty.

### Templates (`templates/`)
Jinja2 templates with `base.html` as the layout. All pages extend `base.html` via `{% extends "base.html" %}` and fill `{% block content %}`. The navbar and footer are in `base.html`.

### Static files (`static/`)
- `css/style.css` — global styles
- `css/landing.css` — landing page-specific styles
- `js/main.js` — global JS, loaded on every page via `base.html`

## Implementation roadmap (student steps)

Routes marked "coming in Step N" in `app.py` indicate what is not yet implemented:
- Step 1: `database/db.py` (get_db, init_db, seed_db)
- Step 3: `/logout`
- Step 4: `/profile`
- Steps 7–9: `/expenses/add`, `/expenses/<id>/edit`, `/expenses/<id>/delete`

Auth (register/login) routes already render templates but have no backend logic yet.
