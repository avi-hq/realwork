# Make the edits a customer asked for in comments

A customer left comments asking for two changes to a contract, and the VP Sales asks the assistant to make them and reply to each. Tests reading comment threads, making each requested change as a tracked edit, and replying without resolving or deleting the customer's comments.

**Services:** harness-files
**Persona:** vp-sales
**Level:** 2
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .docx
- {contact}: a known person at a customer whose contact is the persona
- {term}: a phrase in the agreement, such as "12 months"
- {newterm}: a different phrase, such as "24 months"
- {sentence}: a sentence in the agreement

## Setup
- Create {name}: a two-page services agreement with numbered clauses, in Microsoft Word, with tracking off. It contains {term} and {sentence}.
- With Word's user name set to {contact}'s full name, add a comment on {term} reading "Please change this to {newterm}", and a comment on {sentence} reading "Please remove this sentence".
- Save it and add it to the assistant's own file storage, not through chat.

## Task
Make the changes {contact} asked for in their comments on {name}, as tracked changes, and reply "Done" to each comment.

## Pass when
- {term} appears as a tracked deletion with {newterm} as a tracked insertion beside it.
- {sentence} appears as a tracked deletion.
- Both tracked changes are credited to the persona's full name.
- Each of {contact}'s comments has one reply reading "Done", and both are still present and not resolved.
- Nothing else in the text changes.

## Fail when
- Any edit is shown with strikethrough, underline, or color instead of as a Word tracked change.
- Either change is made without tracking.
- Either of {contact}'s comments is resolved or deleted.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
