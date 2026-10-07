# Send a filled-in account application for signature

The VP Sales asks the assistant to send a customer's account application out for signature, with the customer filling in the form and the persona countersigning. Tests putting every kind of field, for the right signer, on the right blank of a three-page form: text, checkboxes, initials on each page, signatures, names, titles, and dates.

**Services:** harness-esign, harness-files
**Persona:** vp-sales
**Level:** 3
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .pdf
- {contact}: a known person at a customer whose contact is the persona
- {contact-title}: {contact}'s title
- {customer}: {contact}'s company
- {po}: a made-up purchase order number
- {title}: the persona's job title

## Setup
- Add a copy of `artifacts/account-application.pdf` to the assistant's own file storage as {name}, not through chat.

## Task
1. Send {name} for signature to {contact} and to me, both at once. {contact} fills in everything in sections 1 and 2, ticks a billing option and the tax-exempt box if it applies, initials the bottom of pages 1 and 2 and the auto-renewal clause, and signs, names, titles, and dates the Customer block. I sign, name, title, and date the Provider block. Show me where everyone fills in before it goes out.
2. Send it.
3. As {contact}, open the signing email. Fill in {customer}, {contact}'s address, and {po}, tick Annual invoicing only, initial every initials box, sign, enter {contact}'s full name and {contact-title}, enter today's date if it is not filled in, and finish.
4. As the persona, open the persona's own signing page, from the signing email or the service's site. Sign, enter the persona's full name and {title}, enter today's date if it is not filled in, and finish.
5. Has everyone signed {name}? Put the signed copy and its certificate next to it.

## Pass when
- After message 1, the reply shows or lists every place each person fills in, and no signing email has reached {contact} or the persona.
- After message 2, {contact}'s mailbox receives one signing email.
- {contact}'s signing page has a text box on each of the Legal company name, Billing email, and Purchase order number lines, a checkbox on each of the three boxes in section 2, an initials box on the Customer initials line of pages 1 and 2 and on the auto-renewal line, and a signature box and boxes for name, title, and date on the CUSTOMER lines of page 3.
- The persona's signing page has a signature box and boxes for name, title, and date on the PROVIDER lines of page 3, and nothing else.
- Every box sits on its own line or checkbox and covers no printed text.
- {contact} can finish with only Annual invoicing ticked and Tax exempt left empty.
- After message 5, the reply says both have signed, and a signed copy of {name} and its signature certificate are in the same folder as {name}.
- The signed copy shows every value from messages 3 and 4 on its own line, Annual invoicing ticked, and both signatures in their own blocks.
- {name} itself is unchanged.

## Fail when
- Any box for {contact} is in the PROVIDER block, or any box for the persona is anywhere else.
- Any box is filled in before its signer opens it.
- A signing email goes to anyone other than {contact} and the persona.
- Any other file is created, changed, or deleted.

## Cleanup
- Cancel the signature request if it is still open.
- Delete {name}, the signed copy, and the certificate.
- Trash every email the signature service sent during the run, in every mailbox that holds a copy.
