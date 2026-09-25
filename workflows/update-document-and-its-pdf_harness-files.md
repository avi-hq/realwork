# Change a document and bring its PDF up to date

The head of people asks the assistant to change a document's title and update the PDF already made from it. Tests replacing the existing PDF so it reflects the change and is otherwise identical, rather than leaving a stale PDF or making a second one.

**Services:** harness-files
**Persona:** hr
**Level:** 1
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .docx
- {pdf}: a made-up file name ending in .pdf
- {title}: a made-up title

## Setup
- As the persona, copy Reference.docx to {name}, export it to {pdf} in Microsoft Word, and add both to the assistant's own file storage, not through chat.

## Task
Change the title of {name} to {title}, then update {pdf} to match.

## Pass when
- The title of {name} reads {title}, still in the Title style.
- {pdf} shows {title} as its title and otherwise matches {name} page for page.
- There is exactly one PDF named {pdf}.

## Fail when
- A second PDF is created instead of replacing {pdf}.
- Anything else in {name} changes.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
