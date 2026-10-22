# Add a new quarter to a chart in a deck

The VP of sales asks the assistant to add a new quarter's numbers to the revenue chart in a deck. Tests changing a chart's data in place, with its own design and the numbers already in it kept.

**Services:** harness-files
**Persona:** vp-sales
**Level:** 2
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .pptx
- {q4}: four made-up revenue figures in millions, one decimal each, for East, West, North, and South

## Setup
- Add a copy of `artifacts/quarterly-review.pptx` to the assistant's own file storage as {name}, not through chat.

## Task
Add Q4 to the revenue by region chart in {name}: {q4}.

## Pass when
- The Revenue by region chart shows three bars for each region, and its legend names Q2, Q3, and Q4.
- The Q4 bars are labelled with the figures in {q4}, region by region.
- The Q2 and Q3 bars still show the labels they had.
- The chart still has a legend and labels on every bar.

## Fail when
- Any other slide changes.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
