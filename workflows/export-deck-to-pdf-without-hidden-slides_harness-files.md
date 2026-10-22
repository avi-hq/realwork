# Export a deck to PDF without its hidden slides

The VP of sales asks the assistant for a PDF of a deck to send around. Tests an export that has every slide shown in the slide show, in order, and leaves out the hidden one, as PowerPoint does.

**Services:** harness-files
**Persona:** vp-sales
**Level:** 1
**Frequency:** uncommon

## Inputs
- {name}: a made-up file name ending in .pptx

## Setup
- Add a copy of `artifacts/quarterly-review.pptx` to the assistant's own file storage as {name}, not through chat.

## Task
Make a PDF of {name} to send around.

## Pass when
- One PDF is created during the run, named like {name} with .pdf instead of .pptx.
- It has five pages, one for each slide that is not hidden, in the deck's order, each matching its slide.
- The hidden Appendix slide is not in it.

## Fail when
- {name} changes.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
