# Turn an untracked returned copy into a redline

A customer sent back an edited contract without tracking changes, and the VP Sales asks the assistant for a redline against the version that was sent. Tests comparing two documents so every difference, and only the differences, shows up as a tracked change.

**Services:** harness-files
**Persona:** vp-sales
**Level:** 2
**Frequency:** common

## Inputs
- {contact}: a known person at a customer whose contact is the persona
- {sent}: a made-up file name ending in .docx
- {returned}: a different made-up file name ending in .docx
- {redline}: a third made-up file name ending in .docx

## Setup
- Create {sent}: a two-page services agreement with numbered clauses, in Microsoft Word, with tracking off.
- Copy it to {returned}. In {returned}, with tracking off, change one phrase, delete one sentence, and add one sentence. Write down all three.
- Save both and add it to the assistant's own file storage, not through chat.

## Task
{contact} sent back {returned} without tracking their changes. Make a redline of it against {sent}, named {redline}.

## Pass when
- {redline} is created during the run.
- It shows exactly the three differences as tracked changes: the changed phrase as a deletion and an insertion, the deleted sentence as a deletion, and the added sentence as an insertion.
- Everything else in {redline} is identical to {sent}.
- {sent} and {returned} are unchanged.

## Fail when
- {redline} shows a tracked change where the documents do not differ.
- Any of the three differences is missing or not tracked.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
