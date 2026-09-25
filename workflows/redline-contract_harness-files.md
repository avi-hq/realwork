# Redline a contract with an insertion, a deletion, and a replacement

The VP Sales asks the assistant to mark up a customer contract with three different edits. Tests making every edit as a Word tracked change credited to the persona, with nothing changed outside the edits and nothing accepted.

**Services:** harness-files
**Persona:** vp-sales
**Level:** 1
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .docx
- {clause}: a made-up one-sentence clause to add
- {after}: the number of a clause in the agreement
- {remove}: a sentence in the agreement
- {old}: a phrase in the agreement, such as "within 30 days"
- {new}: a different phrase to replace it

## Setup
- As the persona, create {name}: a two-page services agreement with numbered clauses, in Microsoft Word, with tracking off. It contains {remove} and {old}. Save it and add it to the assistant's own file storage, not through chat.

## Task
Redline {name}: add "{clause}" as a new clause after clause {after}, delete "{remove}", and change "{old}" to "{new}".

## Pass when
- {clause} appears after clause {after} as a tracked insertion.
- {remove} appears as a tracked deletion.
- {old} appears as a tracked deletion and {new} as a tracked insertion beside it.
- Every tracked change is credited to the persona's full name.
- There are exactly these four tracked changes, none accepted, and all other text and formatting is unchanged.

## Fail when
- Any edit is shown with strikethrough, underline, or color instead of as a Word tracked change.
- Any edit is made without tracking.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
