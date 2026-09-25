# Export a document to a PDF that matches it page for page

The CPO asks the assistant to export a formatted Word document to PDF. Tests that the PDF keeps the document's layout exactly: the same pages, fonts, header, footer, and repeating table header.

**Services:** harness-files
**Persona:** cpo
**Level:** 1
**Frequency:** common

## Inputs
- {pdf}: a made-up file name ending in .pdf

## Setup
None.

## Task
Export Reference.docx to a PDF named {pdf}.

## Pass when
- One PDF named {pdf} is created during the run.
- It matches Reference.docx page for page: three US Letter pages, each starting and ending with the same content as in Word.
- The header and the "Page X of Y" footer appear on every page, with the right numbers.
- The table's header row repeats at the top of page 2.
- Every font is embedded and is the same font Word uses for that text.

## Fail when
- Reference.docx is changed.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
