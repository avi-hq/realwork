# Build a short deck, change it, then ask for a PDF

The CEO builds a small presentation with the assistant over four messages and only asks for a PDF at the end. Tests that the changes land in the one deck and that a PDF appears only after it is asked for.

**Services:** google-drive, harness-files
**Persona:** ceo
**Level:** 3
**Frequency:** common

## Inputs
- {deck}: a made-up presentation name
- {topic}: a made-up company topic, such as an office move
- {title}: a made-up title for the second slide
- {date}: a date next month

## Setup
None.

## Task
1. Make a three-slide deck named {deck} in My Drive about {topic}: a title slide, a slide on the plan, and a slide on next steps.
2. Change the second slide's title to {title}.
3. Add "{date}" to the title slide's subtitle.
4. Now send me a PDF of it.

## Pass when
- One presentation named {deck} is in My Drive, made during the run, with three slides.
- Its second slide's title reads {title}.
- Its title slide's subtitle includes "{date}".
- One PDF of {deck} is in the assistant's storage, made after message 4, with three pages matching the three slides.

## Fail when
- A PDF of {deck} exists before message 4 was sent.
- A second presentation is created.
- Any other file is created, changed, or deleted.

## Cleanup
- Trash {deck}.
- Delete the PDF from the assistant's storage.
