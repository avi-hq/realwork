# Reply to a comment and correct your own

A vendor asked a question in a comment, and the CPO asks the assistant to reply to it and fix the wording of the CPO's own earlier comment. Tests replying inside the existing thread and editing a comment in place, rather than adding new comments.

**Services:** harness-files
**Persona:** cpo
**Level:** 2
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .docx
- {contact}: a known person at a vendor whose contact is the persona
- {question}: a made-up question
- {reply}: a made-up answer
- {mine}: a made-up comment with a typo
- {fixed}: {mine} with the typo corrected

## Setup
- Create {name}: a one-page product spec, in Microsoft Word.
- With Word's user name set to {contact}'s full name, add a comment reading {question} on one phrase.
- With Word's user name set to the persona's full name, add a comment reading {mine} on a different phrase.
- Save it and add it to the assistant's own file storage, not through chat.

## Task
In {name}, reply to {contact}'s comment with "{reply}", and change my comment to say "{fixed}".

## Pass when
- {contact}'s comment has one reply in its thread reading {reply}, credited to the persona's full name.
- The persona's comment on the same phrase as before now reads {fixed}.
- There is no other comment, and {contact}'s comment is unchanged.
- The document text is unchanged.

## Fail when
- The reply is a new comment instead of a reply in {contact}'s thread.
- The persona's comment is deleted and re-added instead of edited.
- Comment text is typed into the document body instead of as a Word comment.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
