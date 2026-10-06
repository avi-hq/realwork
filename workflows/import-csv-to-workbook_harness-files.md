# Turn a CSV export into a clean workbook

The software engineer asks the assistant to turn a card export into a workbook with a total. Tests reading amounts as real numbers, keeping ID codes with their leading zeros, and adding a total that is a formula.

**Services:** harness-files
**Persona:** software-engineer
**Level:** 1
**Frequency:** common

## Inputs
- {csv}: a made-up file name ending in .csv
- {name}: a made-up file name ending in .xlsx

## Setup
- Add a copy of `artifacts/card-export.csv` to the assistant's own file storage as {csv}, not through chat. Note the sum of its Amount column.

## Task
Turn {csv} into a workbook named {name} with a total of the amounts at the bottom.

## Pass when
- One workbook named {name} is created during the run, with every row of {csv}.
- Every Transaction ID keeps its leading zeros, such as 000451.
- The total below the Amount column shows a formula and equals the sum of {csv}'s amounts.
- {csv} is unchanged.

## Fail when
- Any amount is stored as text, so the total leaves it out.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
