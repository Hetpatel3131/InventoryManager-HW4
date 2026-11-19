# Data and Troubleshooting

## Inventory format

Each nonblank line in `inventory.txt` contains:

```text
name|category|quantity
```

For example:

```text
Laptop Charger|Electronics|8
Printer Paper|Office Supplies|25
```

Files are read and written as UTF-8. Blank lines are ignored. Loading a missing
file returns an empty inventory. Saving replaces the file with the current
inventory, so a backup is useful before editing data manually.

## Common problems

| Symptom | Check |
| --- | --- |
| Program starts empty unexpectedly | Run from the folder containing `inventory.txt`. |
| `python` is not found on a Mac | Try `python3 --version` and `python3 inventory_manager.py`. |
| Item number is rejected | Use a number from 1 through the current list length. |
| Quantity is rejected | Use ordinary whole-number digits, such as `0` or `12`. |
| Duplicate item is rejected | Names are compared without case sensitivity. |
| Loading crashes after a manual file edit | Check every nonblank line has exactly three fields and an integer quantity. |
| `No module named ruff` or `mkdocs` | Activate the virtual environment and install `requirements-dev.txt`. |
| File cannot be saved | Check that the folder is writable and the file is not read-only. |

## Current limitations

This checkpoint is a classroom application. It does not recover gracefully
from malformed records, file permission errors, or all unusual Unicode
number characters. It does not reapply the menu's duplicate-name and quantity
validation when loading a manually edited file. Avoid direct edits unless
you follow the format and keep a backup.

There is no database, login system, concurrent editing protection, or automatic
backup. These are documented limitations, not problems claimed to be fixed by
the HW4 tools.
