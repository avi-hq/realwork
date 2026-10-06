# Combine two PDFs into one packet and fix a sideways page

The head of people asks the assistant to put an offer letter and a benefits summary into one PDF. Tests merging in the asked order, turning a sideways page upright, and leaving the sources untouched.

**Services:** harness-files
**Persona:** hr
**Level:** 1
**Frequency:** common

## Inputs
- {offer}: a made-up file name ending in .pdf
- {benefits}: a different made-up file name ending in .pdf
- {packet}: a third made-up file name ending in .pdf

## Setup
- Add a copy of `artifacts/offer-letter.pdf` to the assistant's own file storage as {offer}, not through chat.
- Add a copy of `artifacts/benefits-summary.pdf` to the assistant's own file storage as {benefits}, not through chat. Its page 2 shows sideways.

## Task
Combine {offer} and {benefits} into one PDF named {packet}, with the offer letter first, and fix the sideways page.

## Pass when
- One PDF named {packet} is created during the run, with five pages.
- Pages 1 and 2 are the offer letter's pages 1 and 2, and pages 3 to 5 are the benefits summary's pages 1 to 3, in that order.
- Every page reads upright.
- {offer} and {benefits} are unchanged.

## Fail when
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
