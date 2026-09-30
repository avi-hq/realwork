# Export an A4 PDF from a US Letter document

The CEO asks for an A4 PDF of a US Letter document for a customer who prints on A4. Tests changing the paper size for the export only, with nothing clipped and the document itself left as Letter.

**Services:** harness-files
**Persona:** ceo
**Level:** 1
**Frequency:** uncommon

## Inputs
- {pdf}: a made-up file name ending in .pdf

## Setup
None.

## Task
Export Reference.docx to an A4 PDF named {pdf}. The customer prints on A4.

## Pass when
- One PDF named {pdf} is created during the run.
- Every page has A4 proportions: noticeably taller for its width than a Letter page (about 1.41 to 1, against 1.29 to 1).
- No text or table cell is cut off or runs past the page margins.
- The header and footer appear on every page.
- Reference.docx still shows Letter pages.

## Fail when
- Reference.docx is changed.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
