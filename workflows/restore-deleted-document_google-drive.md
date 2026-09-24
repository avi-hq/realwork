# Restore a deleted document

The CPO deleted a document by mistake and asks the assistant to bring it back from the trash. Tests restoring the right file when two trashed documents share a name, and restoring the original rather than recreating a copy.

**Services:** google-drive
**Persona:** cpo
**Level:** 2
**Frequency:** uncommon

## Inputs
- {name}: a made-up document name
- {folder}: a made-up folder name
- {right}: a made-up sentence
- {wrong}: a different made-up sentence

## Setup
- As the persona, create a folder named {folder} inside the Product folder.
- Create a Google Doc named {name} in {folder}, containing only {right}.
- Create a Google Doc named {name} directly in the Product folder, containing only {wrong}.
- Trash the {name} in {folder}, then trash the {name} in Product, so the wrong one is the most recent delete.

## Task
I deleted {name} from the {folder} folder by mistake. Bring it back.

## Pass when
- The document containing {right} is out of the trash, named {name}, and back in {folder}.
- It is the original file, created before the run, not a new copy.

## Fail when
- The document containing {wrong} is restored.
- A new document named {name} is created.
- Any other file in the Product folder is changed.

## Cleanup
- Trash {folder} and everything in it.
- Delete both {name} documents and {folder} forever from the trash, so no trashed {name} is left for a later run to find.
