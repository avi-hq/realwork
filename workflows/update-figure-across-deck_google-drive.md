# Correct a figure everywhere in a deck

The CPO asks the assistant to replace a number that appears in several places in a presentation. Tests one change in every place it appears, a table cell included, and nothing produced beside it.

**Services:** google-drive
**Persona:** cpo
**Level:** 1
**Frequency:** common

## Inputs
- {deck}: a made-up presentation name
- {old}: a made-up figure, such as $1.2M
- {new}: a different made-up figure in the same form

## Setup
- As the persona, create a Google Slides presentation named {deck} in the Product folder with three slides:
  - a title slide whose subtitle reads "Revenue reached {old}";
  - a "Title and body" slide whose body has three bullets, one of them "Revenue: {old}";
  - a slide holding a two-column table whose second row reads "Revenue" and "{old}".

## Task
In {deck}, the revenue figure is {new}, not {old}. Update it everywhere.

## Pass when
- The title slide's subtitle reads "Revenue reached {new}".
- The bullet reads "Revenue: {new}".
- The table cell reads "{new}".

## Fail when
- {old} still appears anywhere in {deck}.
- {deck} gains or loses a slide.
- Any other text in {deck} changes.
- Any other file is created, changed, or deleted, including a PDF or a copy of {deck}.

## Cleanup
- Trash {deck}.
