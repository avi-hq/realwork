# Add a slide that matches the rest of a deck

The VP of sales asks the assistant to add a slide to an existing deck in the deck's own style. Tests a new slide placed at the right point that looks like its neighbours, with every other slide left as it was.

**Services:** harness-files
**Persona:** vp-sales
**Level:** 2
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .pptx
- {title}: a made-up slide title of three to six words about the sales plan
- {points}: three made-up short points about the sales plan, each under ten words

## Setup
- Add a copy of `artifacts/quarterly-review.pptx` to the assistant's own file storage as {name}, not through chat.

## Task
In {name}, add a slide right after Pipeline titled {title}, with these points: {points}. Make it look like the other slides.

## Pass when
- A new slide sits directly after the Pipeline slide.
- Its title reads {title}, in the same place, font, and size as the Highlights slide's title.
- It shows the three points of {points} as bullets, in the same font and size as the Highlights slide's bullets.
- No text on it is cut off or runs past the edge of the slide.
- The new slide has no speaker notes copied from another slide.

## Fail when
- Any other slide's text, chart, or table changes.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
