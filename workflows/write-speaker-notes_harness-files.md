# Write speaker notes for a deck

The VP of sales asks the assistant to write what to say for each slide of a deck. Tests notes that belong to each slide's own content, written as speaker notes and not onto the slides.

**Services:** harness-files
**Persona:** vp-sales
**Level:** 2
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .pptx

## Setup
- Add a copy of `artifacts/quarterly-review.pptx` to the assistant's own file storage as {name}, not through chat.

## Task
Write speaker notes for every slide in {name} that isn't hidden: two or three sentences each on what I should say. Keep the note that's already on Highlights.

## Pass when
- Each of the five slides that are not hidden has two or three new sentences of speaker notes that mention something shown on that slide (on Highlights, besides the note it already had).
- The Highlights slide's notes still include "Open with the revenue number."
- No slide shows any new text on the slide itself.

## Fail when
- Any slide's text, chart, or table changes.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
