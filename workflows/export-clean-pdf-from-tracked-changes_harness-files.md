# Export a clean PDF from a document with tracked changes

The VP Sales asks for a send-ready PDF of a document that still has tracked changes and a comment. Tests that the PDF shows the edited text with no markup or comments, while the document itself keeps them unresolved.

**Services:** harness-files
**Persona:** vp-sales
**Level:** 2
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .docx
- {pdf}: a made-up file name ending in .pdf
- {added}: a made-up sentence
- {removed}: a sentence from the Summary section of Reference.docx
- {comment}: a made-up comment

## Setup
- As the persona, copy Reference.docx to {name}. In Microsoft Word, turn on tracking, insert {added} into the Summary section, delete {removed}, and add a comment reading {comment}. Save it and add it to the assistant's own file storage, not through chat.

## Task
Export {name} as a clean PDF named {pdf}, with the edits applied and no markup or comments.

## Pass when
- One PDF named {pdf} is created during the run.
- It shows {added} as plain text and does not show {removed}.
- It shows no change markup, no comment, and no comment balloon.
- {name} still holds both tracked changes and the comment, none accepted or deleted.

## Fail when
- {name} is changed.
- Reference.docx is changed.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
