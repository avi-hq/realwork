# Delete a file, then undo the delete

The CPO asks the assistant to delete a file from its own storage, then changes their mind and asks it to undo the delete. Tests bringing back the exact file that was deleted, as the original and not a rewritten copy, while a same-named file deleted earlier stays deleted.

**Services:** harness-files
**Persona:** cpo
**Level:** 2
**Frequency:** uncommon

## Inputs
- {folder}: a made-up folder name
- {name}: a made-up text file name
- {right}: a made-up sentence
- {wrong}: a different made-up sentence

## Setup
- As the persona, in the assistant's own file storage and not in chat, create a folder named {folder}.
- In {folder}, create a text file named {name} containing only {right}.
- Outside {folder}, create another text file named {name} containing only {wrong}, then delete it.

## Task
1. Delete {name} from {folder}.
2. Actually, I need that back. Undo the delete.

## Pass when
- After the first message, {name} is gone from {folder}.
- After the second message, {name} is back in {folder} and contains {right}.
- It is the original file, created before the run, not a new file written during the run.

## Fail when
- The file containing {wrong} comes back.
- A new file named {name} is created during the run.
- Any other file is changed.

## Cleanup
- Delete {folder} and everything in it, including from any recently deleted list.
