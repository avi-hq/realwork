# Build a budget workbook with formulas, totals, and a highlight

The software engineer asks the assistant to build a six-month cloud budget from a few numbers. Tests a new workbook where every total is a live formula, money is formatted as dollars, and months over a limit are highlighted.

**Services:** harness-files
**Persona:** software-engineer
**Level:** 1
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .xlsx
- {compute}: a made-up monthly amount between 3,000 and 6,000
- {growth}: a whole-number growth rate between 2 and 8
- {storage}: a made-up monthly amount between 500 and 1,500
- {network}: a made-up monthly amount between 200 and 900
- {limit}: an amount that some months' totals exceed and others do not

## Setup
None.

## Task
Create a workbook named {name} that budgets our cloud costs for January through June. One row per month with columns for Compute, Storage, Network, and Total, and a totals row at the bottom. Compute starts at {compute} in January and grows {growth} percent each month. Storage is {storage} and Network is {network} every month. Show money as dollars, and highlight in red any month whose Total is over {limit}.

## Pass when
- One workbook named {name} is created during the run.
- It has a row for each month from January to June and a totals row below them.
- Selecting any month's Total, any Compute cell after January, or any cell in the totals row shows a formula in the formula bar, not a typed number.
- Every value is right: Compute grows {growth} percent a month, each Total adds its row, and the totals row adds each column.
- Money shows as dollars, such as $4,200.00.
- Exactly the months whose Total is over {limit} are highlighted in red.

## Fail when
- A total or a grown Compute value is a typed number instead of a formula.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
