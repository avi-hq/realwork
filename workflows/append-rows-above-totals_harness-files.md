# Add rows to a sheet that has a totals row

The software engineer asks the assistant to log three new expenses in an existing workbook. Tests adding rows above the totals row so the total and everything that reads it grow to include them, with the sheet's formats carried down.

**Services:** harness-files
**Persona:** software-engineer
**Level:** 1
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .xlsx
- {first}: a made-up expense with a date in 2026, one of the categories Compute, Storage, Network, or Support, a vendor, and an amount
- {second}: a different made-up expense in the same shape
- {third}: a third made-up expense in the same shape

## Setup
- Add a copy of `artifacts/budget.xlsx` to the assistant's own file storage as {name}, not through chat.

## Task
Add these expenses to the Expenses sheet in {name}: {first}; {second}; {third}.

## Pass when
- The three expenses appear as rows in the Expenses sheet, above the Total row.
- Their dates and amounts are shown in the same formats as the rows above them.
- The Total row's formula covers the new rows, and its value has grown by exactly the three amounts.
- The Summary sheet's Expenses logged value equals the new total.

## Fail when
- A new row lands below the Total row.
- Any existing expense or any cell on the Budget sheet changes.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
