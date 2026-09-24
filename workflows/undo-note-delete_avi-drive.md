# Delete a note, then undo the delete

The CPO asks the assistant to delete a note, then changes their mind and asks it to undo the delete. Tests bringing back the exact note that was deleted, as the original and not a rewritten copy, while a similar note that was deleted earlier stays deleted.

**Services:** avi-drive
**Persona:** cpo
**Level:** 2
**Frequency:** uncommon

## Inputs
- {folder}: a made-up folder name
- {name}: a made-up note name
- {right}: a made-up sentence
- {wrong}: a different made-up sentence

## Setup
- As the persona, in the Avi Drive panel and not in chat, create a folder named {folder}.
- In {folder}, create a note named {name} whose text is only {right}.
- Outside {folder}, create another note named {name} whose text is only {wrong}, then delete it.

## Task
1. Delete {name} from {folder}.
2. After the assistant says it is done: Actually, I need that back. Undo the delete.

## Pass when
- After the first message, {name} is gone from {folder}.
- After the second message, {name} is back in {folder} and its text is {right}.
- It is the original note, created before the run, not a new note written during the run.

## Fail when
- The note containing {wrong} comes back.
- A new note named {name} is created during the run.
- Any other file or note is changed.

## Cleanup
- Delete {folder} and everything in it.
