# Replace a pricing table's rows, keeping its total last

The CEO asks the assistant to swap a proposal's pricing for new items. Tests replacing a table's rows in place, so the old rows go, the total stays last and adds up, and the body rows don't take on the header's look.

**Services:** harness-files
**Persona:** ceo
**Level:** 2
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .docx
- {items}: four made-up items, each with a quantity and a unit price

## Setup
- As the persona, in Microsoft Word, create {name}: a one-page proposal with a paragraph above and below a pricing table. The table has a bold, gray-shaded header row of Item, Qty, Price, and Amount, three item rows, and a Total row at the bottom. Save it and add it to the assistant's own file storage, not through chat.

## Task
Replace the pricing in {name} with these items: {items}. Keep the total at the bottom.

## Pass when
- The table still has its header row, then exactly the four new items, then the Total row last.
- No row from the old pricing remains.
- Each Amount is quantity times price, and the Total adds them.
- The item rows are not bold or shaded like the header.
- The paragraphs above and below the table are unchanged.

## Fail when
- The new rows are added below the old ones, or the total is no longer last.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
