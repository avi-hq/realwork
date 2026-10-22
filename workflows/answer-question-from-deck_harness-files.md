# Answer a question from a deck

The VP of sales asks the assistant for two facts that sit in a deck: one in a chart and one in a table. Tests reading a deck's chart numbers and table cells, not only its text, without changing anything.

**Services:** harness-files
**Persona:** vp-sales
**Level:** 2
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .pptx
- {region}: one of East, West, North, or South
- {stage}: one of Qualified, Proposal, or Closing

## Setup
- Add a copy of `artifacts/quarterly-review.pptx` to the assistant's own file storage as {name}, not through chat.

## Task
In {name}, what was {region}'s revenue in Q3, and how many deals are in {stage}?

## Pass when
- The reply gives {region}'s Q3 revenue exactly as the number on {region}'s Q3 bar in the Revenue by region chart.
- The reply gives the number of deals in {stage} exactly as the Pipeline table shows it.

## Fail when
- Any file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
