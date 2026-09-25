# Export a PDF with heading bookmarks and working links

The software engineer asks the assistant for a PDF readers can navigate. Tests that the PDF carries bookmarks mirroring the heading structure and keeps the hyperlink clickable, without changing the layout.

**Services:** harness-files
**Persona:** software-engineer
**Level:** 1
**Frequency:** uncommon

## Inputs
- {pdf}: a made-up file name ending in .pdf

## Setup
None.

## Task
Export Reference.docx to a PDF named {pdf}, with bookmarks for the headings.

## Pass when
- One PDF named {pdf} is created during the run.
- Its bookmarks list every Heading 1 and Heading 2 in Reference.docx, with the Heading 2 nested under its Heading 1.
- Each bookmark opens the page its heading is on.
- The "example site" link opens https://example.com.
- It matches Reference.docx page for page.

## Fail when
- Reference.docx is changed.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
