# Export one section of a document to PDF

The CPO asks the assistant to export only the appendix of a document. Tests picking out exactly one section and exporting it with the document's formatting.

**Services:** harness-files
**Persona:** cpo
**Level:** 2
**Frequency:** uncommon

## Inputs
- {pdf}: a made-up file name ending in .pdf

## Setup
None.

## Task
Export just the Appendix of Reference.docx to a PDF named {pdf}.

## Pass when
- One PDF named {pdf} is created during the run.
- It holds the Appendix heading and its paragraph, and nothing from any other section.
- It uses the same fonts, margins, header, and footer as Reference.docx.

## Fail when
- Reference.docx is changed.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
