# Build a short customer deck from a brief

The VP of sales asks the assistant for a short deck for a customer meeting from a few facts. Tests a new deck whose slides each have a title, whose numbers become a chart, and whose text all fits on its slides.

**Services:** harness-files
**Persona:** vp-sales
**Level:** 1
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .pptx
- {customer}: a customer whose contact is the persona
- {seats}: a whole number of seats between 50 and 500
- {usage}: four made-up active-user counts for Q4 2025, Q1 2026, Q2 2026, and Q3 2026, each between 100 and 2,000
- {ask}: a made-up next step to ask the customer for, such as a pilot of a new product

## Setup
None.

## Task
Make a deck named {name} for our meeting with {customer}: a title slide, a slide on their account ({seats} seats), a chart of active users by quarter ({usage}), and a slide asking for {ask}.

## Pass when
- One deck named {name} is created during the run.
- Its first slide is a title slide that names {customer}, and it has at least three more slides.
- Every slide after the first has a title.
- One slide shows a chart with one bar or point for each of the four quarters, labelled with the quarters, at the counts in {usage}.
- One slide names {ask}.
- On every slide, no text is cut off, runs past the edge of the slide, or overlaps other text.

## Fail when
- The chart is missing, or shows other numbers.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run created.
