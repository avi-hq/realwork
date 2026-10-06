# Find and fix every formula error

The software engineer asks the assistant to fix a forecast full of errors. Tests finding each error, fixing it with a formula rather than a typed value, and saying what was wrong.

**Services:** harness-files
**Persona:** software-engineer
**Level:** 2
**Frequency:** uncommon

## Inputs
- {name}: a made-up file name ending in .xlsx

## Setup
- Add a copy of `artifacts/broken-formulas.xlsx` to the assistant's own file storage as {name}, not through chat. It shows #DIV/0! in two cells and #REF! in the revenue total.

## Task
Fix the errors in {name}.

## Pass when
- No cell on the Forecast sheet shows an error.
- The revenue total shows a formula that adds the Revenue column, with the right value.
- Price per unit and Growth for the rows that showed #DIV/0! show a formula that handles the zero, not a typed value.
- The reply lists each cell it fixed and what was wrong with it.

## Fail when
- An error is hidden by typing a number or text over the formula.
- Any Revenue or Units value changes.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
