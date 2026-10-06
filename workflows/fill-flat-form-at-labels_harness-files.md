# Fill a form that has no fields

The head of people asks the assistant to fill a printed form whose blanks are just lines. Tests writing each value on the line after its label, with nothing overlapping the printed words.

**Services:** harness-files
**Persona:** hr
**Level:** 1
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .pdf
- {full}: a made-up full name
- {preferred}: a made-up preferred name
- {start}: a made-up start date
- {department}: a made-up department
- {manager}: a made-up manager's name
- {emergency}: a made-up emergency contact
- {phone}: a made-up phone number

## Setup
- Add a copy of `artifacts/new-hire-form.pdf` to the assistant's own file storage as {name}, not through chat.

## Task
Fill out {name}: full name {full}, preferred name {preferred}, start date {start}, department {department}, manager {manager}, emergency contact {emergency}, emergency phone {phone}.

## Pass when
- A filled copy of the form is created during the run, and {name} itself is still blank.
- In the copy, each value sits on the line after its own label, from Full name to Emergency phone.
- No value overlaps a label, another value, or any printed text.

## Fail when
- A value lands on the wrong line.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
