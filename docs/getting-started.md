# Getting Started

## Requirements

Use Python 3.10 or newer. The inventory application itself uses only Python's
standard library. Ruff and MkDocs are development dependencies.

## Run the application

Open a terminal inside the project folder, then run:

```bash
python inventory_manager.py
```

If your Mac only recognizes `python3`, use that command instead. The program
shows a menu with choices 1 through 7. Enter `1` to view inventory or `7` to exit.

## Check the sample

Choose `6` to see the inventory summary. Before editing the supplied sample,
the expected results are:

| Measurement | Expected value |
| --- | --- |
| Unique items | 5 |
| Total quantity | 52 |
| Low-stock items | 2 |
| Electronics items | 2 |
| Office Supplies items | 2 |
| Classroom Supplies items | 1 |

## Where data is saved

The program opens `inventory.txt` relative to the terminal's current folder.
Keep the terminal in the project folder when running it. Add, update, and
remove actions save the inventory immediately.

If the file does not exist, the program starts with an empty inventory. Adding
an item creates the file. If you want to experiment with the sample, first
make a backup copy of `inventory.txt`.

Continue with the [User Guide](user-guide.md).
