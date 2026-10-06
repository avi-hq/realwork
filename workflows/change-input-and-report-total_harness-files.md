# Change one number and report the new total

The software engineer asks the assistant to correct one month's cost and say what the year now comes to. Tests finding the right cell, changing only its value, and reporting the total the workbook recalculates.

**Services:** harness-files
**Persona:** software-engineer
**Level:** 2
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .xlsx
- {month}: a month from January to December
- {amount}: a made-up amount between 3,000 and 9,000

## Setup
- Add a copy of `artifacts/budget.xlsx` to the assistant's own file storage as {name}, not through chat. Note the Budget sheet's annual total and {month}'s Compute value.

## Task
In {name}, Compute for {month} should be {amount}. What does the year total now?

## Pass when
- Compute for {month} on the Budget sheet is {amount}, as a number.
- {month}'s Total and the annual total have recalculated, and both still show formulas in the formula bar.
- The reply states the new annual total, which equals the old one plus {amount} minus the old Compute value for {month}.

## Fail when
- Any formula is replaced with a typed number.
- Any other input cell changes.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
