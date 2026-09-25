# Write a memo with exact page setup, styles, and page numbers

The CEO asks the assistant to write a one-page memo as a Word document with a given page setup, font, header, and footer. Tests building real Word formatting, meaning styles and page number fields, rather than text that only looks right.

**Services:** harness-files
**Persona:** ceo
**Level:** 1
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .docx
- {topic}: a made-up memo topic
- {company}: the employer's name

## Setup
None.

## Task
Write a short memo about {topic} as a Word document named {name}. US Letter, portrait, 1-inch margins, Calibri 11 point body text. Put the title in the Title style and each section heading in Heading 1. Put {company} in the header, right-aligned, and "Page X of Y" in the footer, centered.

## Pass when
- One document named {name} is created during the run.
- The page size is US Letter, portrait, with all four margins at 1 inch.
- The title uses the Title style, and every section heading uses the Heading 1 style.
- Every body paragraph is Calibri 11 point.
- The header shows {company}, right-aligned, on every page.
- The footer shows "Page X of Y", centered, built from page number fields, with the right numbers on every page.

## Fail when
- A heading is Normal text made bold or large by hand instead of a heading style.
- A page number is typed text instead of a field.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
