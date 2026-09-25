# Build nested numbered lists and a table whose header repeats on every page

The CPO asks the assistant for a product spec with nested lists and a long table. Tests real Word list formatting at two levels, and a table header row that repeats on each page instead of being copied by hand.

**Services:** harness-files
**Persona:** cpo
**Level:** 1
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .docx
- {product}: a made-up product name

## Setup
None.

## Task
Create a Word document named {name} with a product spec for {product}. Include a numbered list of three requirements, each with two lettered sub-points under it, and a bulleted list of risks. Then add a table of 40 milestones with columns Milestone, Owner, and Date. Make the table's top row bold with light gray shading, and repeat it at the top of every page the table runs onto.

## Pass when
- One document named {name} is created during the run.
- The requirements use Word's numbered list formatting, 1 to 3, with each item's two sub-points at the second list level, lettered a and b.
- The risks use Word's bulleted list formatting.
- The table has 3 columns and 41 rows. Its first row is bold, shaded light gray, and set to repeat as a header row.
- On every page the table spans, that header row appears at the top of the table.

## Fail when
- Any list number, letter, or bullet is typed text instead of list formatting.
- The header row is copied by hand onto later pages instead of set to repeat.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
