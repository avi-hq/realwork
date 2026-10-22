# Write speaker notes for a whole deck

The CEO asks the assistant to write speaker notes for every slide of a presentation. Tests notes on every slide, drawn from what each slide says, with the slides themselves untouched.

**Services:** google-drive
**Persona:** ceo
**Level:** 1
**Frequency:** common

## Inputs
- {deck}: a made-up presentation name
- {slides}: four made-up slide titles, each with two short bullets

## Setup
- As the persona, create a Google Slides presentation named {deck} in My Drive with four "Title and body" slides holding {slides}, and no speaker notes.

## Task
Write speaker notes for every slide in {deck}.

## Pass when
- Every slide of {deck} has speaker notes of at least one full sentence.
- Each slide's notes mention something from that slide's own title or bullets.

## Fail when
- Any slide's title or body text changes.
- {deck} gains or loses a slide.
- Any other file is created, changed, or deleted.

## Cleanup
- Trash {deck}.
