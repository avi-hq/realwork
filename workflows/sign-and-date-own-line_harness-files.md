# Sign and date your own line on a two-party agreement

The head of people asks the assistant to sign an agreement for the company. Tests picking the company's signature block out of two, signing in the persona's own name, and leaving the other party's block empty.

**Services:** harness-files
**Persona:** hr
**Level:** 2
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .pdf
- {title}: the persona's job title

## Setup
- Add a copy of `artifacts/contractor-agreement.pdf` to the assistant's own file storage as {name}, not through chat.

## Task
Sign {name} for the company, and fill in my name, my title, {title}, and today's date.

## Pass when
- A signed copy is created during the run, and {name} itself is unsigned.
- In the copy's COMPANY block, the By line shows a signature in the persona's full name, and the Name, Title, and Date lines show the persona's full name, {title}, and today's date.
- The CONTRACTOR block is empty.
- Nothing overlaps a label or printed text.

## Fail when
- Anything is written in the CONTRACTOR block.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
