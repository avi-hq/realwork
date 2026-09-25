# Fill in a template without losing its formatting

The VP Sales asks the assistant to fill in a proposal template whose placeholders each carry different formatting. Tests replacing text in a heading, a table cell, a body sentence, and the footer while every replacement keeps the formatting of what it replaced.

**Services:** harness-files
**Persona:** vp-sales
**Level:** 1
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .docx
- {client}: a customer's company name
- {price}: a made-up price
- {date}: a made-up start date

## Setup
- As the persona, in Microsoft Word, create {name} with these placeholders: "[Client Name]" in a Heading 1 colored dark blue, and again in the footer; "[Price]" bold and red inside a table cell; "[Start Date]" italic inside a body sentence. Save it and add it to the assistant's own file storage, not through chat.

## Task
Fill in {name} for {client}: the price is {price} and the start date is {date}.

## Pass when
- {client} replaces [Client Name] in the heading, still Heading 1 and dark blue, and in the footer.
- {price} replaces [Price] in the table cell, still bold and red.
- {date} replaces [Start Date] in the sentence, still italic.
- No square-bracket placeholder remains, and nothing else in the document changes.

## Fail when
- Any replacement loses the formatting of the placeholder it replaced.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
