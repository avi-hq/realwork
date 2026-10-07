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
- The form is filled, either in {name} itself or in one copy of it made during the run. The filled form is called the form below.
- In the form, each value sits on the line after its own label, from Full name to Emergency phone.
- No value overlaps a label, another value, or any printed text.

## Fail when
- A value lands on the wrong line.
- Any other file is created, changed, or deleted, or more than one copy is made.

## Cleanup
- Delete every file the run and its Setup created.
