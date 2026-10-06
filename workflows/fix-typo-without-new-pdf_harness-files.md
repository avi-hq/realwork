# Fix a typo without making a new PDF

The CEO asks the assistant to fix a typo in a document that already has a PDF beside it. Tests changing only the document, not making a PDF that wasn't asked for, and saying the existing PDF is now out of date.

**Services:** harness-files
**Persona:** ceo
**Level:** 1
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .docx
- {pdf}: a made-up file name ending in .pdf
- {word}: a word from the Summary section of Reference.docx
- {typo}: {word} with two letters swapped

## Setup
- As the persona, copy Reference.docx to {name}. In Microsoft Word, change {word} in the Summary section to {typo}, export it to {pdf}, and add both to the assistant's own file storage, not through chat.

## Task
Fix the typo in {name}: "{typo}" should be "{word}".

## Pass when
- {name} reads {word} where it read {typo}, and nothing else in it changes.
- {pdf} is unchanged, and no other PDF is created.
- The reply says {pdf} still has the old spelling.

## Fail when
- A PDF is created or {pdf} is changed.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
