# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

**Run the app:**
```bash
python src/app.py
```
App runs at `http://localhost:5000` in debug mode.

**Run tests:**
```bash
python -m unittest discover -s tests
```

**Run a single test:**
```bash
python -m unittest tests.test_app.AppTestCase.test_index
```

**Install dependencies:**
```bash
pip install -r requirements.txt
```

## Architecture

Flask MVC app with Jinja2 templating.

- **[src/app.py](src/app.py)** — Flask app factory and route registration via `add_url_rule`
- **[src/views.py](src/views.py)** — Route handler functions (`index`, `course`)
- **[src/models.py](src/models.py)** — `Course` dataclass and hardcoded course list
- **[src/templates/](src/templates/)** — Jinja2 templates; `layout.html` is the base template extended by all pages
- **[src/static/css/styles.css](src/static/css/styles.css)** — All styles

Routes:
- `GET /` → lists all courses
- `GET /course/<course_id>` → course detail (course_id is a 0-based index into the courses list in `models.py`)

## Environment

`.env` holds `GOOGLE_API_KEY` (currently unused in the codebase — placeholder for future integration). Loaded via `python-dotenv`.
