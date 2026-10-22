# Make a customer deck from the company template

The VP Sales asks the assistant for a quarterly review deck for a customer, made from the template deck in their Sales folder. Tests copying the template rather than starting blank, filling every placeholder, and leaving the template untouched.

**Services:** google-drive
**Persona:** vp-sales
**Level:** 2
**Frequency:** common

## Inputs
- {customer}: a customer whose contact is the persona
- {quarter}: a quarter and year, such as Q3 2026
- {name}: a made-up presentation name
- {points}: three made-up results for the quarter, one short sentence each

## Setup
- As the persona, create a Google Slides presentation named "Review template" in the Sales folder. Choose any theme other than Simple Light. Give it two slides:
  - a title slide whose title reads "{{customer}} review" and whose subtitle reads "{{quarter}}";
  - a "Title and body" slide whose title reads "Highlights" and whose body reads "{{highlights}}".

## Task
Make a quarterly review deck named {name} for {customer} for {quarter} from our review template in Sales. The highlights are: {points}.

## Pass when
- A presentation named {name} is in the Sales folder, made during the run.
- Its first slide's title reads "{customer} review" and its subtitle reads "{quarter}".
- Each of the three results in {points} appears on its slides.
- No slide in {name} shows text in double braces, such as "{{highlights}}".
- {name} uses the same theme as "Review template".

## Fail when
- "Review template" is changed.
- Any text on a slide of {name} runs past the edge of its box or of the slide.
- Any other file in Sales is created, changed, or deleted.

## Cleanup
- Trash {name} and "Review template".
