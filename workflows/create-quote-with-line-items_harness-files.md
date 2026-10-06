# Make a quote with line items, tax, and totals

The CEO asks the assistant for a quote with several line items and sales tax. Tests a document whose table shows each line's amount and a subtotal, tax, and total that are right to the cent.

**Services:** harness-files
**Persona:** ceo
**Level:** 1
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .docx
- {client}: a customer's company name
- {items}: three made-up line items, each with a quantity and a unit price
- {tax}: a sales tax rate between 5 and 10 percent

## Setup
None.

## Task
Make a quote named {name} for {client}: {items}, with {tax} percent sales tax. Show each line's amount, then the subtotal, tax, and total.

## Pass when
- One document named {name} is created during the run, naming {client}.
- Its table has a row for each line item with its quantity, unit price, and amount, and every amount is quantity times unit price.
- The subtotal, tax at {tax} percent, and total are right to the cent.
- Money is shown in dollars with cents, such as $1,250.00.

## Fail when
- Any amount, subtotal, tax, or total is wrong.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
