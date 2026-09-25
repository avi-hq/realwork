# Export an archival PDF/A

The CEO asks the assistant for an archival PDF of a document. Tests producing a real PDF/A file, with every font embedded, that still matches the document's layout.

**Services:** harness-files
**Persona:** ceo
**Level:** 1
**Frequency:** uncommon

## Inputs
- {pdf}: a made-up file name ending in .pdf

## Setup
None.

## Task
Export Reference.docx as a PDF/A named {pdf} for our records.

## Pass when
- One PDF named {pdf} is created during the run.
- Its properties declare PDF/A conformance, and a PDF/A validator such as veraPDF reports no errors.
- Every font is embedded.
- It matches Reference.docx page for page.

## Fail when
- Reference.docx is changed.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
