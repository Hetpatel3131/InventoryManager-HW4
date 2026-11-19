# User Guide

## Menu choices

| Choice | Action | Example |
| --- | --- | --- |
| 1 | View inventory | Show the item number, name, category, and quantity. |
| 2 | Add an item | `HDMI Cable`, `Electronics`, `6` |
| 3 | Update a quantity | Choose the displayed item number and enter `12`. |
| 4 | Remove an item | Choose the displayed item number. |
| 5 | Search | Enter `charger` to find `Laptop Charger`. |
| 6 | Summary | Display totals and counts by category. |
| 7 | Exit | End the program. |

## Add an item

1. Choose `2`.
2. Enter a nonempty item name.
3. Enter a nonempty category.
4. Enter a nonnegative whole-number quantity, such as `0` or `6`.

Names are unique regardless of capitalization. If `Laptop Charger` exists,
`laptop charger` is rejected. Names and categories cannot contain `|`, because
the file uses that character as a separator. Blank names and categories,
negative quantities, fractions, and ordinary text quantities are rejected.

## Update or remove

Use the item number from the complete inventory list shown by that action.
Numbers start at 1. A zero or out-of-range number is rejected. Removing an item
changes the numbering of later items. Removal saves immediately and does not
have an undo command; keep a backup before experimenting.

## Search

Search matches part or all of an item name without requiring the same
capitalization. Searching for `CHARGER` finds `Laptop Charger`. Blank search
terms are rejected. A term with no matches displays a message.

Search results have their own display numbering. Use the numbers shown by
the update or remove action when making a change.

## Summary

Unique items means the number of records, not the sum of quantities.
Low stock means quantity **less than 5**: a quantity of 4 is low, and 5 is not.
Category counts count item records and combine category names that differ
only in capitalization. The first encountered spelling is used as the label.
