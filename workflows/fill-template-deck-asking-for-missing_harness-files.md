# Fill in a template deck and ask for what is missing

The VP of sales asks the assistant to fill in a business review template for a customer, leaving out one value the template asks for. Tests filling every placeholder it has a value for, and asking for the missing one instead of making it up.

**Services:** harness-files
**Persona:** vp-sales
**Level:** 2
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .pptx
- {customer}: a customer whose contact is the persona
- {quarter}: a quarter, such as Q3 2026
- {seats}: a whole number of seats between 50 and 500
- {sponsor}: a made-up full name of a person at {customer}
- {delivered}: three made-up things delivered to {customer} this quarter
- {next}: two made-up next steps

## Setup
- Add a copy of `artifacts/qbr-template.pptx` to the assistant's own file storage as {name}, not through chat.

## Task
Fill in {name} for {customer}: it's for {quarter}, prepared by me, {seats} seats, executive sponsor {sponsor}. We delivered {delivered}. Next steps: {next}.

## Pass when
- The title slide reads {customer} Quarterly Business Review, with {quarter} and the persona's full name under it.
- The at-a-glance slide shows {seats} and {sponsor}.
- The delivered slide's title names {quarter}, and it lists the three things in {delivered}.
- The next steps slide lists the two steps in {next}.
- No placeholder in double braces remains, except possibly the renewal date's.
- The reply says the renewal date is missing or asks for it.

## Fail when
- Any renewal date appears in the deck.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
