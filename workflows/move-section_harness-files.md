# Move one section above another

The CEO asks the assistant to reorder a contract's sections. Tests moving a whole section, heading and body, without changing its words or losing the comment attached to it.

**Services:** harness-files
**Persona:** ceo
**Level:** 2
**Frequency:** uncommon

## Inputs
- {name}: a made-up file name ending in .docx
- {coworker}: another employee persona
- {comment}: a made-up one-sentence comment

## Setup
- As the persona, in Microsoft Word, create {name}: five headed sections, Scope, Payment, Confidentiality, Termination, and Governing Law, each with two paragraphs. With Word's user name set to {coworker}'s full name, add a comment reading {comment} on a phrase in the Termination section. Save it and add it to the assistant's own file storage, not through chat.

## Task
In {name}, move the Termination section so it comes right after Scope.

## Pass when
- The sections now run Scope, Termination, Payment, Confidentiality, Governing Law.
- The Termination heading and both of its paragraphs moved together, word for word.
- {coworker}'s comment is still attached to the same phrase.
- Nothing else in the document changes.

## Fail when
- The Termination section is copied rather than moved, so it appears twice.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
