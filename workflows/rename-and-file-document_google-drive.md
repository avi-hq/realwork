# Rename a document and file it in a new folder

The CEO asks the assistant to rename a document and move it into a new subfolder. Tests three Drive changes in order: create a folder, rename, and move.

**Services:** google-drive
**Persona:** ceo
**Level:** 1
**Frequency:** uncommon

## Inputs
- {name}: a made-up document name
- {new}: a different made-up document name
- {folder}: a made-up folder name

## Setup
- As the persona, create a Google Doc named {name} in the Company folder.

## Task
Rename {name} to {new} and move it into a new {folder} folder inside Company.

## Pass when
- The Company folder has a folder named {folder}.
- {folder} holds a document named {new}.
- No document named {name} remains in Company.

## Fail when
- Any other file in Company is renamed, moved, or deleted.

## Cleanup
- Trash {folder} and everything in it.
