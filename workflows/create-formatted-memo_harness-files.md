# Write a memo with exact page setup, styles, and page numbers

The CEO asks the assistant to write a one-page memo as a Word document with a given page setup, font, header, and footer. Tests producing a memo whose page setup, title, headings, header, and footer render as asked.

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
Write a one-page memo about {topic} as a Word document named {name}. US Letter, portrait, 1-inch margins, Calibri 11 point body text. Put the title in the Title style and each section heading in Heading 1. Put {company} in the header, right-aligned, and "Page X of Y" in the footer, centered.

## Pass when
- One document named {name} is created during the run.
- The memo is one portrait page with even margins on all four sides.
- The title is larger than every heading, and every section heading is set the same way as the others and larger than the body text.
- Every body paragraph is in the same sans-serif font at the same size.
- The header shows {company}, right-aligned, on every page.
- The footer shows "Page 1 of 1", centered.

## Fail when
- A section heading looks like body text, or is set differently from the other headings.
- The footer page number is missing or wrong.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
