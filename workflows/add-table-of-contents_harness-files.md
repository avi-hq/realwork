# Add a table of contents with correct page numbers

The software engineer asks the assistant to add a table of contents to a four-page document. Tests inserting a real, generated table of contents whose entries and page numbers match the headings.

**Services:** harness-files
**Persona:** software-engineer
**Level:** 2
**Frequency:** uncommon

## Inputs
- {name}: a made-up file name ending in .docx

## Setup
- As the persona, in Microsoft Word, create {name}: five Heading 1 sections and three Heading 2 sub-sections, each with a paragraph, and page breaks so it runs four pages. Save it and add it to the assistant's own file storage, not through chat.

## Task
Add a table of contents at the start of {name}, on its own page.

## Pass when
- Page 1 holds a table of contents that is a generated Word field, built from the headings.
- It lists all five Heading 1 and all three Heading 2 entries, with the Heading 2 entries indented.
- Each entry's page number matches the page its heading is on.
- The rest of the document starts on page 2, otherwise unchanged.

## Fail when
- The table of contents is typed text instead of a field.
- Any heading is missing or shows the wrong page number.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
