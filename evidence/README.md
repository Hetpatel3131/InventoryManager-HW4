# Evidence Guide

The starting point is the uploaded HW1 solution checkpoint. No issues were
intentionally inserted. The unchanged baseline source is retained as a small
text snapshot so the exact improvement can be inspected without Git history.

| File | What it demonstrates |
| --- | --- |
| `baseline_inventory_manager.py.txt` | Original supplied Python source. |
| `baseline_sha256.json` | Original hashes of the three supplied files. |
| `environment.txt` | Python environment and installed package versions. |
| `before_program.txt` | Program run before source changes. |
| `before_ruff_lint.txt` | One observed `FURB122` issue with the explicit project rules. |
| `before_ruff_format.txt` | Original Python source needed formatting. |
| `before_ruff_diff.txt` | Formatting differences before applying changes. |
| `ruff_fix.txt` | One supported lint fix applied. |
| `ruff_format_applied.txt` | Formatting applied to the Python source. |
| `after_ruff_lint.txt` | Final lint check passed. |
| `after_ruff_format.txt` | Final formatting check passed. |
| `code_changes.diff` | Exact before/after Python source diff. |
| `before_docs.txt` | No MkDocs integration in the supplied checkpoint. |
| `after_mkdocs_build.txt` | Successful strict documentation build. |
| `after_program.txt` | Program still runs with the same sample results. |
| `behavior_verification.txt` | Save/load and CLI comparisons against the original source. |

Tool 1 and Tool 2 screenshots are supplied separately in the submission
package. They can be submitted to Blackboard as the two required screenshots.
No generated `site/`, cache, or virtual environment is included in the package.

## Recheck the original lint result

From the project root, with developer dependencies installed:

```bash
python -m ruff check --stdin-filename inventory_manager.py < evidence/baseline_inventory_manager.py.txt
```

This returns a nonzero exit code because it checks the original source with
the final project's configured rules. It does not edit the current source.

## Recheck the final project

```bash
python -m ruff check .
python -m ruff format --check .
python -m mkdocs build --strict
python inventory_manager.py
```

For the last command, choose `6` and then `7`. With the original sample, the
summary is 5 items, total quantity 52, and 2 low-stock items. For commands that
change data, first make a copy of `inventory.txt`.

The baseline stdin command above is for macOS, Linux, or Codespaces terminals.
