# Fill a fillable tax form by its labels

The head of people asks the assistant to fill a vendor's tax form from the details at hand. Tests filling form fields by their printed labels, ticking exactly one box, and leaving the tax ID blank rather than inventing it.

**Services:** harness-files
**Persona:** hr
**Level:** 1
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .pdf
- {contact}: a known person at a vendor
- {company}: that person's company
- {kind}: one of Individual or sole proprietor, C corporation, S corporation, Partnership, or Limited liability company
- {street}: a made-up street address
- {city}: a made-up city, state, and ZIP code

## Setup
- Add a copy of `artifacts/vendor-tax-form.pdf` to the assistant's own file storage as {name}, not through chat.

## Task
Fill out {name} for {company}: the name is {contact}, the business name is {company}, it's a {kind}, and the address is {street}, {city}. Date it today.

## Pass when
- A filled copy of the form is created during the run, and {name} itself is still blank.
- In the copy, Name shows {contact}, Business name shows {company}, the address and city lines show {street} and {city}, and Date shows today's date.
- Only the {kind} box is checked.
- The taxpayer identification number is empty, and the reply says it was left blank because it was not given.

## Fail when
- Any value is written outside its box or over printed text.
- A taxpayer identification number is filled in.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
