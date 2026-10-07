# Write a renewal order and send it for countersignature

The VP Sales asks the assistant to write a customer's renewal order and send it to be signed by the customer first and the persona second. Tests making a finished document from the task alone and sending it to two signers in order, so the persona is asked to sign only after the customer has.

**Services:** harness-esign, harness-files
**Persona:** vp-sales
**Level:** 3
**Frequency:** common

## Inputs
- {contact}: a known person at a customer whose contact is the persona
- {customer}: {contact}'s company
- {plan}: a made-up plan name
- {price}: a made-up monthly price in dollars
- {start}: the first day of next month
- {title}: the persona's job title

## Setup
None.

## Task
1. Write a one-page renewal order for {customer}: the {plan} plan at {price} a month for 12 months, starting {start}. Give it a signature block for {contact} and one for me. Send it to {contact} to sign first, and to me once they have. Show me where each of us signs before it goes out.
2. Send it.
3. As {contact}, open the signing email, sign, fill in anything else asked for, and finish.
4. Who still has to sign the renewal order?
5. As the persona, open the persona's own signing page, from the signing email or the service's site, sign, fill in anything else asked for, and finish.
6. Put the signed copy and its certificate next to the renewal order.

## Pass when
- One new document is created in the assistant's file storage during the run, and it names {customer}, the {plan} plan, {price} a month, 12 months, and {start}.
- The document has no placeholder text left, such as brackets, blanks to complete, or "TBD".
- After message 1, the reply shows where each person signs, and no signing email has reached {contact} or the persona.
- After message 2, {contact}'s mailbox receives one signing email, and the persona has nothing to sign yet.
- The document {contact} signs is the one created in message 1, with {contact}'s signature box in {contact}'s block and none in the persona's.
- After message 4, the reply names the persona as the only one left to sign.
- The persona's signature box is in the persona's block, and none of {contact}'s is.
- After message 6, a signed copy and its signature certificate are in the same folder as the document, and the signed copy shows both signatures in their own blocks.

## Fail when
- The persona is asked to sign before {contact} has.
- A signing email goes to anyone other than {contact} and the persona.
- The price, plan, term, or start date differs from the task.
- Any file other than the document, its signed copy, and its certificate is created, changed, or deleted.

## Cleanup
- Cancel the signature request if it is still open.
- Delete the document, the signed copy, the certificate, and any other file the run created.
- Trash every email the signature service sent during the run, in every mailbox that holds a copy.
