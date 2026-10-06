# Read a value off a scanned page

The head of people asks the assistant about a receipt that was scanned, so the page is a picture with no text in it. Tests reading a scan by looking at it rather than saying it can't be read.

**Services:** harness-files
**Persona:** hr
**Level:** 2
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .pdf
- {question}: a question from the list below
- {answer}: its answer from the list

Pairs to pick from:
- "What was the total?" $84.37.
- "What's the receipt number?" 20417.
- "What date is on it?" August 21, 2026.
- "How much was the tax?" $5.43.
- "What card was it paid with?" The card ending 4417.

## Setup
- Add a copy of `artifacts/scanned-receipt.pdf` to the assistant's own file storage as {name}, not through chat.

## Task
{name} is a scanned receipt. {question}

## Pass when
- The reply states {answer}.

## Fail when
- Any file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
