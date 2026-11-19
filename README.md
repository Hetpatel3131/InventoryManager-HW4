# Inventory Manager — CPS 310 Homework 4

A small Python command-line program for tracking inventory. Homework 4 adds
Ruff checks and formatting, plus a documentation website built with MkDocs.

## Project starting point

This project uses the supplied **Homework 1 instructor solution checkpoint**:
`inventory_manager.py`, `inventory.txt`, and `TESTING.md`. The assignment permits
using a previous course project. The HW2 test suite was not included in the
supplied source, so no claim is made that its 47 tests were rerun here.

## Run the program

Use Python 3.10 or newer. Open a terminal in this folder and run:

```bash
python inventory_manager.py
```

On a Mac, use `python3` if `python` is unavailable. Run from this folder so the
program finds `inventory.txt`. Only the developer tools need extra packages.

## Install the developer tools

```bash
python -m venv .venv
```

Activate the environment on macOS, Linux, or GitHub Codespaces:

```bash
source .venv/bin/activate
```

On Windows PowerShell, activation is:

```powershell
.venv\Scripts\Activate.ps1
```

Then install the recorded tool versions:

```bash
python -m pip install -r requirements-dev.txt
```

## Run the checks

```bash
python -m ruff check .
python -m ruff format --check .
python -m mkdocs build --strict
```

To preview the documentation locally:

```bash
python -m mkdocs serve
```

Open the local address printed by MkDocs. Press Ctrl+C to stop the server.
The generated `site/` directory is excluded from Git; it can be rebuilt.

## Homework evidence

- [TOOLS.md](TOOLS.md): both tool integrations and reflection draft.
- [Evidence guide](evidence/README.md): real before/after output and verification.
- `pyproject.toml`: Ruff configuration.
- `mkdocs.yml` and `docs/`: MkDocs configuration and five source pages.
- `requirements-dev.txt`: the two tool versions used.
- [AI assistance](AI_ASSISTANCE.md): scope and provenance of the preparation.

The included sample contains 5 unique items, total quantity 52, and 2 low-stock
items. Low stock means a quantity below 5.
