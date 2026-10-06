# Number a document's sections and subsections

The CEO asks the assistant to number a document's headings in outline style. Tests numbering that runs 1, 1.1, 1.2, 2 down the headings without retyping or changing them.

**Services:** harness-files
**Persona:** ceo
**Level:** 2
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .docx

## Setup
- As the persona, in Microsoft Word, create {name}: four Heading 1 sections, the first and third each with two Heading 2 sub-sections, and a paragraph under every heading, with no numbering. Save it and add it to the assistant's own file storage, not through chat.

## Task
Number the sections in {name} as 1, 1.1, 1.2, 2, and so on.

## Pass when
- The four sections are numbered 1 to 4 in order.
- The sub-sections are numbered 1.1, 1.2, 3.1, and 3.2.
- Every heading's own words are unchanged, and no paragraph changes.

## Fail when
- A number is missing, repeated, or out of order.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
