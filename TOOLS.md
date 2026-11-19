# Developer Tool Exploration

Project: Inventory Manager, using the supplied Homework 1 instructor solution
checkpoint. The two categories are Code Quality and Documentation.

AI assistance: ChatGPT helped prepare the tool integrations, documentation, and reflection. The initial checks were run in ChatGPT's workspace using Python 3.12.14. The evidence folder contains the recorded results. See `AI_ASSISTANCE.md` for details.

## Tool 1: Ruff

### What problem does this tool solve?

Ruff checks Python code for selected code-quality problems and can format it
consistently. It helps identify small improvements that are easy to miss when
only checking whether the program runs. It is not a replacement for testing.

### How did I use it?

Ruff 0.17.5 was installed in a virtual environment with
`python -m pip install -r requirements-dev.txt`. The `pyproject.toml` file sets
an 88-character line length, Python 3.10 as the syntax target, common error and
import checks, and the `FURB122` rule. The initial source was inspected using
`python -m ruff check inventory_manager.py` and
`python -m ruff format --check inventory_manager.py` before changing it.

### What did it find, change, or automate?

The configured linter reported one `FURB122` issue in `save_inventory()`.
The function called `file.write()` once per item inside a loop. Ruff suggested
using `file.writelines()` with the generated record strings. The formatter
also reported that the one Python source file needed formatting.

### What did I change in response?

After inspecting the result, the supported fix was applied using
`python -m ruff check --fix inventory_manager.py`, followed by
`python -m ruff format inventory_manager.py`. The save function now uses
`file.writelines()` and keeps a newline at the end of each record. Quote style
and wrapping are consistent. Save/load checks and menu workflows produced the
same results as the original source. No speed improvement was measured.

### Before and After

| Measurement | Before | After |
| --- | --- | --- |
| Configured Ruff lint issues in the Python source | 1 (`FURB122`) | 0 |
| Python source files requiring formatting | 1 | 0 |
| Sample summary | 5 items, quantity 52, 2 low stock | Same |

The original output is in `evidence/before_ruff_lint.txt` and
`evidence/before_ruff_format.txt`. Final results are in
`evidence/after_ruff_lint.txt` and `evidence/after_ruff_format.txt`.
`evidence/code_changes.diff` shows the exact code changes, and
`evidence/behavior_verification.txt` records the behavior checks. The Tool 1
screenshot is `HW4_Tool1_Ruff.png` in the supplied submission package.
Its baseline command checks the preserved original source; it does not alter
the final program to recreate an issue.

### Would I use this tool again?

I would use Ruff again because a short command can check code quality and
formatting before I submit or commit a project. I would still read the
reported change and run the program afterward, because clean lint output
does not prove that all behavior is correct.

---

## Tool 2: MkDocs

### What problem does this tool solve?

MkDocs converts Markdown files into a documentation website. It helps users
find setup instructions, examples, and troubleshooting information through
organized navigation and search.

### How did I use it?

MkDocs 1.6.1 was installed through the same `requirements-dev.txt` file.
The `mkdocs.yml` configuration gives the site a name, selects the built-in
theme, and lists five documentation pages. The site was generated using
`python -m mkdocs build --strict`. It can be previewed locally with
`python -m mkdocs serve`.

### What did it find, change, or automate?

The supplied checkpoint had a manual testing record but no MkDocs
configuration or documentation website. After adding the source pages,
MkDocs built the website successfully with strict mode enabled. It generated
HTML pages, navigation, and a search index from the Markdown files.

### What did I change in response?

The project now includes a guide covering setup, all seven menu choices,
input rules, the inventory file format, troubleshooting, and developer
commands. This gives a new user a practical way to learn the program without
reading the Python code. The generated `site/` folder is ignored by Git
because MkDocs can rebuild it from the source files.

### Before and After

| Evidence | Before | After |
| --- | --- | --- |
| MkDocs configuration | None in the supplied checkpoint | `mkdocs.yml` |
| MkDocs source pages | 0 | 5 |
| Documentation website | Not supplied | Successfully generated |
| Strict build | Not configured | Exit code 0 |

`evidence/before_docs.txt` records the starting condition.
`evidence/after_mkdocs_build.txt` contains the successful build output.
The source pages are in `docs/`. The Tool 2 screenshot is
`HW4_Tool2_MkDocs.png` in the supplied submission package.

### Would I use this tool again?

I would use MkDocs again for a project with several setup steps or features.
Writing Markdown is straightforward, and the navigation makes the guide
easier to browse. For a very small script, a short README may be enough.

---

## Overall Reflection

MkDocs provided the most value to this project because it added a complete
user guide to a checkpoint that only supplied a manual testing record.
Ruff also helped by identifying a real simplification in the save function
and applying consistent formatting. The useful lesson is that tools solve
different problems: a clean code check and a successful documentation build
both help, but the application still needs to be run and checked.

## Official Documentation Consulted

- [Ruff configuration](https://docs.astral.sh/ruff/configuration/)
- [Ruff formatter](https://docs.astral.sh/ruff/formatter/)
- [Ruff FURB122 rule](https://docs.astral.sh/ruff/rules/for-loop-writes/)
- [MkDocs getting started](https://www.mkdocs.org/getting-started/)
- [MkDocs configuration](https://www.mkdocs.org/user-guide/configuration/)
