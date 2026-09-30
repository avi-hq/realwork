# Make hand-made headings consistent headings

The CEO has an employee handbook whose headings were made bold and large by hand and whose body text mixes three fonts, and asks the assistant to clean it up. Tests finding which lines are headings, setting them consistently, and making the body consistent without changing any words.

**Services:** harness-files
**Persona:** ceo
**Level:** 2
**Frequency:** uncommon

## Inputs
- {name}: a made-up file name ending in .docx

## Setup
- As the persona, in Microsoft Word, create {name}: six section titles in Normal style made bold 14 point by hand, two of them followed by a sub-section title made bold italic 12 point by hand, and a paragraph under each title. Set the paragraphs in a mix of Times New Roman 12, Arial 10, and Calibri 11. Save it and add it to the assistant's own file storage, not through chat.

## Task
Clean up the formatting in {name}. Make the section titles real headings, the sub-sections second-level headings, and all the body text Calibri 11.

## Pass when
- Every section title is set the same way as the other section titles, larger than the body text.
- Every sub-section title is set the same way as the other sub-section titles, between section titles and body text in size.
- Every body paragraph is in one sans-serif font at one size.
- No text is added, removed, or reordered.

## Fail when
- A title is set differently from the other titles at its level.
- A copy of {name} is created instead of updating it.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
