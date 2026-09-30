# Build nested numbered lists and a table whose header repeats on every page

The CEO asks the assistant for a product spec with nested lists and a long table. Tests a two-level list, a bulleted list, and a long table whose header row shows at the top of every page it runs onto.

**Services:** harness-files
**Persona:** ceo
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
- The requirements are numbered 1 to 3, and each has two sub-points indented beneath it, lettered a and b.
- The risks are a bulleted list.
- The table has 3 columns and 41 rows. Its first row is bold and shaded light gray.
- On every page the table spans, that header row appears at the top of the table.

## Fail when
- A sub-point is not indented beneath its requirement, or a number, letter, or bullet is missing.
- The header row appears anywhere in the table other than the top of a page, or is missing from the top of a page the table runs onto.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
