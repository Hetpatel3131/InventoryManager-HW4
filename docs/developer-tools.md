# Developer Tools

The two Homework 4 tools are **Ruff** (Code Quality) and **MkDocs**
(Documentation). They serve different purposes.

## Install

Create and activate a virtual environment from the project folder:

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements-dev.txt
```

On Windows PowerShell, activate with `.venv\Scripts\Activate.ps1`.
On a Mac, use `python3` to create the environment if needed.

## Ruff: inspect and fix code

```bash
python -m ruff check .
python -m ruff format --check .
```

Ruff uses the configuration in `pyproject.toml`. The selected rules check
common errors and imports, plus `FURB122`, which identifies repeated
`file.write()` calls inside a loop that can use `file.writelines()`.

To apply supported fixes and formatting after reviewing output:

```bash
python -m ruff check --fix .
python -m ruff format .
```

The HW4 change simplifies the save operation and applies consistent formatting.
This is a code-quality improvement; no performance benchmark was performed.
Ruff does not prove that a program meets all its requirements.

Official references:

- [Ruff configuration](https://docs.astral.sh/ruff/configuration/)
- [Ruff formatter](https://docs.astral.sh/ruff/formatter/)
- [FURB122 rule](https://docs.astral.sh/ruff/rules/for-loop-writes/)

## MkDocs: build documentation

```bash
python -m mkdocs build --strict
```

MkDocs reads `mkdocs.yml` and the five Markdown files in `docs/`. It creates
the documentation website in `site/`. Strict mode makes warnings fail the
build. A passing build confirms generation succeeded; it does not guarantee
that every explanation is correct.

To view the site locally:

```bash
python -m mkdocs serve
```

Open the address printed in the terminal and stop the server with Ctrl+C.
Publishing the site is not needed for this homework. Keep `site/` out of Git.

Official references:

- [MkDocs getting started](https://www.mkdocs.org/getting-started/)
- [MkDocs configuration](https://www.mkdocs.org/user-guide/configuration/)

## Verify the application

Run `python inventory_manager.py` and choose `6` to check the sample summary.
When using an unchanged sample, expect 5 unique items, total quantity 52,
and 2 low-stock items. Also try a search and a complete add/update/remove
workflow using a backup copy of the data.

The repository's `evidence/` folder records the actual before/after results.
