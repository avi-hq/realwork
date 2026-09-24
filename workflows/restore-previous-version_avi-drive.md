# Restore a file's original version

The CPO overwrote a file in Avi Drive twice and asks the assistant to put back the original. Tests finding the file's earlier versions and restoring the oldest one, not the most recent, in place at the same path.

**Services:** avi-drive
**Persona:** cpo
**Level:** 2
**Frequency:** uncommon

## Inputs
- {folder}: a made-up folder name
- {name}: a made-up note name
- {first}: a made-up sentence
- {second}: a different made-up sentence
- {third}: a third made-up sentence

## Setup
- As the persona, in the Avi Drive panel and not in chat, create a folder named {folder}.
- In {folder}, create a note named {name} whose text is only {first}. Save.
- Replace the text with only {second}. Save.
- Replace the text with only {third}. Save.

## Task
I overwrote {name} in {folder} by mistake. Put it back to its original version.

## Pass when
- {name} in {folder} contains {first}.
- {name} contains neither {second} nor {third}.

## Fail when
- {name} contains {second}, the most recent earlier version.
- A second note or file with {name} in its name is created in {folder}.
- Any file outside {folder} is changed.

## Cleanup
- Delete {folder} and everything in it.
