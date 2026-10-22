# Fix a slide that holds too much

The VP of sales asks the assistant to fix a slide whose list of priorities runs off the bottom. Tests making every priority readable without dropping or rewording any, and without touching the other slides.

**Services:** harness-files
**Persona:** vp-sales
**Level:** 2
**Frequency:** uncommon

## Inputs
- {name}: a made-up file name ending in .pptx

## Setup
- Add a copy of `artifacts/crowded-deck.pptx` to the assistant's own file storage as {name}, not through chat.

## Task
The priorities slide in {name} has too much on it. Fix it so everything is readable.

## Pass when
- All twelve priorities from the original slide appear in the deck, each exactly once, in their original words.
- No slide's text is cut off or runs past the edge of the slide.
- Every slide that holds priorities has a title, and no two of them share a title.
- The Sales Kickoff, Where we stand, and Questions slides are unchanged.

## Fail when
- A priority is missing, repeated, or reworded.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
