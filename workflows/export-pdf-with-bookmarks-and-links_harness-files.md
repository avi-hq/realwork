# Export a PDF with heading bookmarks and working links

The CEO asks the assistant for a PDF readers can navigate. Tests that the PDF is made with bookmarks for the heading structure and keeps the hyperlink, without changing the layout.

**Services:** harness-files
**Persona:** ceo
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
- The assistant's reply lists the bookmarks it added: every Heading 1 and Heading 2 in Reference.docx, with the Heading 2 under its Heading 1.
- The "example site" link text is on the same page as in Reference.docx.
- It matches Reference.docx page for page.

## Fail when
- Reference.docx is changed.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
