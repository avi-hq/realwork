# Write a job description

The head of people asks the assistant to write a job description and file it. Tests creating one document with the right subject in the right folder.

**Services:** google-drive
**Persona:** hr
**Level:** 1
**Frequency:** common

## Inputs
- {role}: a made-up job title

## Setup
None.

## Task
Write a job description for a {role} and put it in the People folder.

## Pass when
- One document is created during the run in the People folder, with {role} in its name.
- The document names {role}.

## Fail when
- Any other file in the People folder is changed.
- A file is created outside the People folder.

## Cleanup
- Delete the document.
