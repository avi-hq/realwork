# Insert a column and rename a sheet without breaking formulas

The software engineer asks the assistant to add a cost column and rename the sheet other sheets read. Tests structural edits that keep every formula pointing at the right cells.

**Services:** harness-files
**Persona:** software-engineer
**Level:** 1
**Frequency:** uncommon

## Inputs
- {name}: a made-up file name ending in .xlsx

## Setup
- Add a copy of `artifacts/budget.xlsx` to the assistant's own file storage as {name}, not through chat. Note every value on the Summary sheet.

## Task
In {name}, add a Security column just before Total on the Budget sheet, and rename the Budget sheet to Cloud Budget.

## Pass when
- The sheet is named Cloud Budget, with a Security column between Support and Total.
- Each month's Total formula includes the Security column.
- Every Summary value is the same as before, and the Summary formulas name Cloud Budget.
- No cell in the workbook shows #REF!.

## Fail when
- Any monthly figure changes.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
