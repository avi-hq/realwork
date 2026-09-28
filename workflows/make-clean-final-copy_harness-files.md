# Make a clean final copy of a redlined document

The CEO asks the assistant for a clean final version of a redlined document, keeping the redline itself as it is. Tests accepting every change and removing every comment in a new copy while the original redline stays untouched.

**Services:** harness-files
**Persona:** ceo
**Level:** 2
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .docx
- {final}: a different made-up file name ending in .docx

## Setup
- Create {name}: a two-page services agreement with numbered clauses, in Microsoft Word, with tracking on. Make three tracked edits and add two comments, and write down the edits. Save it and add it to the assistant's own file storage, not through chat.

## Task
Make a clean final copy of {name} named {final}: accept every change and remove all comments. Leave {name} as it is.

## Pass when
- {final} is created during the run.
- {final} has no tracked changes and no comments.
- {final}'s text is {name}'s text with all three edits accepted, and its formatting is unchanged.
- {name} still has all three tracked changes and both comments.

## Fail when
- {name} is changed.
- Any edit in {final} is rejected instead of accepted.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
