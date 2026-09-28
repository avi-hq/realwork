# Rename a document and file it in a new folder

The CPO asks the assistant to rename a document and move it into a new subfolder. Tests three file changes in order: create a folder, rename, and move.

**Services:** google-drive
**Persona:** cpo
**Level:** 1
**Frequency:** uncommon

## Inputs
- {name}: a made-up document name
- {new}: a different made-up document name
- {folder}: a made-up folder name

## Setup
- As the persona, create a document named {name} in the Product folder.

## Task
Rename {name} to {new} and move it into a new {folder} folder inside Product.

## Pass when
- The Product folder has a folder named {folder}.
- {folder} holds a document named {new}.
- No document named {name} remains in Product.

## Fail when
- Any other file in Product is renamed, moved, or deleted.

## Cleanup
- Trash {folder} and everything in it.
