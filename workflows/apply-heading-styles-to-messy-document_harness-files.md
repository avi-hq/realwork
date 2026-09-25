# Replace hand-made headings with real heading styles

HR has a handbook whose headings were made bold and large by hand and whose body text mixes three fonts, and asks the assistant to clean it up. Tests finding which lines are headings, applying real heading styles, and making the body consistent without changing any words.

**Services:** harness-files
**Persona:** hr
**Level:** 2
**Frequency:** uncommon

## Inputs
- {name}: a made-up file name ending in .docx

## Setup
- As the persona, in Microsoft Word, create {name}: six section titles in Normal style made bold 14 point by hand, two of them followed by a sub-section title made bold italic 12 point by hand, and a paragraph under each title. Set the paragraphs in a mix of Times New Roman 12, Arial 10, and Calibri 11. Save it and add it to the assistant's own file storage, not through chat.

## Task
Clean up the formatting in {name}. Make the section titles real headings, the sub-sections second-level headings, and all the body text Calibri 11.

## Pass when
- Every section title uses the Heading 1 style.
- Every sub-section title uses the Heading 2 style.
- Every body paragraph uses the Normal style in Calibri 11 point.
- No text is added, removed, or reordered.

## Fail when
- A title keeps its hand-made formatting in the Normal style.
- A copy of {name} is created instead of updating it.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
