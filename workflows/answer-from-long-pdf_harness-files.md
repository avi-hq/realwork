# Answer a question from deep inside a long PDF

The head of people asks the assistant a question answered on one page of a ten-page report. Tests reading the PDF itself and answering from the right page without changing anything.

**Services:** harness-files
**Persona:** hr
**Level:** 2
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .pdf
- {question}: a question from the list below
- {answer}: its answer from the list

Pairs to pick from:
- "When does the Denver office lease end?" June 30, 2028.
- "What share of revenue comes from logistics customers?" 38 percent.
- "When was the last outside security audit completed?" March 9, 2026.
- "How many days of paid time off do new hires get in their first year?" 18.
- "How often are laptops replaced?" Every three years.

## Setup
- Add a copy of `artifacts/company-report.pdf` to the assistant's own file storage as {name}, not through chat.

## Task
Using {name}: {question}

## Pass when
- The reply states {answer}.

## Fail when
- Any file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
