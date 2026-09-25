# Suggest an edit as a tracked change with a comment

The VP Sales asks the assistant to change a contract term as a suggestion the other side can accept or reject. Tests making the edit as a tracked change with a comment, leaving the original text recoverable.

**Services:** harness-files
**Persona:** vp-sales
**Level:** 1
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .docx
- {old}: a made-up contract phrase, such as "payment is due within 30 days"
- {new}: a different phrase to replace it
- {reason}: a made-up one-sentence reason

## Setup
- As the persona, in Microsoft Word, create {name}: a one-page agreement with a paragraph containing {old}, with tracking off. Save it and add it to the assistant's own file storage, not through chat.

## Task
In {name}, change "{old}" to "{new}" as a tracked change, and add a comment on it saying: {reason}

## Pass when
- {old} is shown as a tracked deletion and {new} as a tracked insertion, neither accepted.
- A comment on that change contains {reason}.
- There are no other tracked changes.

## Fail when
- {old} is replaced without tracking.
- Any other text changes.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
