# Save a vendor's emailed attachment to a folder

A vendor has emailed the CPO a file, and the CPO asks the assistant to save it to a folder. Tests finding the attachment and getting it into the right folder.

**Services:** google-drive, google-gmail
**Persona:** cpo
**Level:** 4
**Frequency:** common

## Inputs
- {contact}: a known person at a vendor whose contact is the persona
- {file}: a made-up file name

## Setup
- As {contact}, email the persona with a small file named {file} attached.

## Task
Save the file {contact} just sent me into my Product folder.

## Pass when
- The Product folder has {file}, created during the run.

## Fail when
- Any other file in the Product folder is changed.
- Any email is sent.

## Cleanup
- Delete the saved {file}.
- Trash every email the run and its setup sent, in every mailbox that holds a copy.
