# Write a job description

The CPO asks the assistant to write a job description for a role on the product team and file it. Tests creating one document with the right subject in the right folder.

**Services:** google-drive
**Persona:** cpo
**Level:** 1
**Frequency:** common

## Inputs
- {role}: a made-up job title

## Setup
None.

## Task
Write a job description for a {role} and put it in the Product folder.

## Pass when
- One document is created during the run in the Product folder, with {role} in its name.
- The document names {role}.

## Fail when
- Any other file in the Product folder is changed.
- A file is created outside the Product folder.

## Cleanup
- Delete the document.
