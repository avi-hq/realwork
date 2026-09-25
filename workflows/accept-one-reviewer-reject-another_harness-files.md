# Accept one reviewer's changes and reject another's

A contract has tracked changes from a coworker and from the customer, and the VP Sales asks the assistant to accept the coworker's and reject the customer's. Tests resolving tracked changes by author, so accepted text stays, rejected text returns to the original, and nothing else moves.

**Services:** harness-files
**Persona:** vp-sales
**Level:** 2
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .docx
- {coworker}: another employee persona
- {contact}: a known person at a customer whose contact is the persona

## Setup
- Create {name}: a two-page services agreement with numbered clauses, in Microsoft Word, with tracking on.
- With Word's user name set to {coworker}'s full name, make two tracked edits: one insertion and one deletion.
- With Word's user name set to {contact}'s full name, make two tracked edits in other clauses: one insertion and one deletion.
- Write down each edit's text, then save it {ADD}.

## Task
Accept all of {coworker}'s changes in {name} and reject all of {contact}'s.

## Pass when
- {coworker}'s insertion is plain text and {coworker}'s deleted text is gone.
- {contact}'s inserted text is gone and {contact}'s deleted text is back as plain text.
- No tracked changes remain.
- All text outside the four edits is unchanged.

## Fail when
- Any of {coworker}'s changes is rejected, or any of {contact}'s is accepted.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
