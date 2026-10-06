# Summarize a sheet by category with a chart, and export it to PDF

The software engineer asks the assistant for totals by category on a new sheet, a chart of them, and a PDF of that sheet. Tests live summary formulas, a real chart, and an export where the chart shows.

**Services:** harness-files
**Persona:** software-engineer
**Level:** 2
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .xlsx
- {pdf}: a made-up file name ending in .pdf

## Setup
- Add a copy of `artifacts/budget.xlsx` to the assistant's own file storage as {name}, not through chat.

## Task
In {name}, add a sheet named By Category that totals the Expenses sheet by category, with the number of expenses in each, and a column chart of the totals. Then send me that sheet as a PDF named {pdf}.

## Pass when
- {name} has a sheet named By Category listing each category in the Expenses sheet exactly once, with its total and its count.
- Selecting any total or count shows a formula that reads the Expenses sheet, not a typed number.
- The category totals add up to the Expenses sheet's Total.
- One PDF named {pdf} is created during the run. It shows the By Category table and a column chart with one bar per category, each matching its total.

## Fail when
- Any cell on the Expenses or Budget sheet changes.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
