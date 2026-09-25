# Reword a suggestion that is still pending

The VP Sales asks the assistant to change the wording of their own pending suggested insertion before sending the document back. Tests editing an existing tracked insertion so it stays one suggestion with the new words, instead of stacking a new change on top of it or accepting it.

**Services:** harness-files
**Persona:** vp-sales
**Level:** 2
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .docx
- {draft}: a made-up sentence
- {final}: a different made-up sentence

## Setup
- As the persona, with Word's user name set to the persona's full name, create {name}: a two-page services agreement with numbered clauses, in Microsoft Word. Turn tracking on and insert {draft} as a new sentence in clause 3. Save it and add it to the assistant's own file storage, not through chat.

## Task
In {name}, change my suggested sentence "{draft}" to "{final}". Keep it as a suggestion.

## Pass when
- Clause 3 holds {final} as one tracked insertion credited to the persona's full name.
- {draft} no longer appears anywhere, including as a tracked deletion.
- There are no other tracked changes, and the rest of the text is unchanged.

## Fail when
- The insertion is accepted.
- {draft} is left as a tracked deletion next to a new insertion.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
