# Add comments anchored to exact phrases

The CPO asks the assistant to leave three review comments on a vendor's spec, each on a specific phrase. Tests creating real Word comments, each attached to exactly the right text and credited to the persona.

**Services:** harness-files
**Persona:** cpo
**Level:** 1
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .docx
- {a}: a phrase in the document
- {b}: a different phrase in the document
- {c}: a third phrase in the document
- {ca}: a made-up one-sentence comment
- {cb}: a different made-up one-sentence comment
- {cc}: a third made-up one-sentence comment

## Setup
- As the persona, in Microsoft Word, create {name}: a one-page product spec containing {a}, {b}, and {c}. Save it and add it to the assistant's own file storage, not through chat.

## Task
Add comments to {name}: on "{a}" say "{ca}", on "{b}" say "{cb}", and on "{c}" say "{cc}".

## Pass when
- {name} has exactly three comments.
- Each comment is attached to exactly its phrase, not the whole sentence or paragraph, and reads as given.
- Every comment is credited to the persona's full name.
- The document text is unchanged.

## Fail when
- Comment text is typed into the document body instead of as a Word comment.
- A comment is attached to the wrong text.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
