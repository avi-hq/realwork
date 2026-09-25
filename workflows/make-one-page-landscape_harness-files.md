# Turn one page landscape and keep the rest portrait

The CPO asks the assistant to make the page with a wide table landscape. Tests using section breaks so only that page changes orientation, while headers, footers, and page numbering carry on unbroken.

**Services:** harness-files
**Persona:** cpo
**Level:** 1
**Frequency:** uncommon

## Inputs
- {name}: a made-up file name ending in .docx

## Setup
- As the persona, in Microsoft Word, create {name}: three portrait US Letter pages, a header reading "Product Plan", a footer page number field, and an eight-column table on page 2 that runs past the right margin. Save it and add it to the assistant's own file storage, not through chat.

## Task
Make page 2 of {name} landscape so the wide table fits. Keep the other pages portrait.

## Pass when
- Page 2 is landscape and pages 1 and 3 are portrait.
- The whole table fits inside page 2's margins.
- The "Product Plan" header and the page number appear on all three pages.
- Page numbers run 1, 2, 3.

## Fail when
- The whole document turns landscape.
- Page numbering restarts, or a header or footer is missing on any page.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
