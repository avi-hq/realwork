# Add a cover page and start page numbers after it

The CEO asks the assistant to add a cover page to a report and number the pages from the one after it. Tests a different first page with no page number, and numbering that starts at 1 on page 2.

**Services:** harness-files
**Persona:** ceo
**Level:** 1
**Frequency:** uncommon

## Inputs
- {name}: a made-up file name ending in .docx
- {title}: a made-up report title

## Setup
- As the persona, in Microsoft Word, create {name}: three pages of text with a page number field in the footer and no cover page. Save it and add it to the assistant's own file storage, not through chat.

## Task
Add a cover page to {name} with the title {title} and today's date. The cover shouldn't show a page number, and numbering should start at 1 on the page after it.

## Pass when
- A new first page shows {title} and today's date.
- The cover shows no page number.
- The pages after the cover are numbered 1, 2, 3.
- The original text is unchanged and starts on the page after the cover.

## Fail when
- The cover shows a page number.
- Numbering after the cover starts at 2.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
