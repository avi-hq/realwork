# Cancel a signature request already sent

The VP Sales has sent an application to a customer for signature and asks the assistant to cancel it before they sign. Tests stopping the request at the signature service, so the customer can no longer sign, while leaving the document itself alone.

**Services:** harness-esign, harness-files
**Persona:** vp-sales
**Level:** 3
**Frequency:** uncommon

## Inputs
- {name}: a made-up file name ending in .pdf
- {contact}: a known person at a customer whose contact is the persona

## Setup
- Add a copy of `artifacts/account-application.pdf` to the assistant's own file storage as {name}, not through chat.

## Task
1. Send {name} to {contact} to sign. Show me where they sign before it goes out.
2. Send it.
3. Cancel that signature request. The terms need to change first.

## Pass when
- After message 2, {contact}'s mailbox receives one signing email.
- After message 3, the reply says the request is cancelled.
- The link in {contact}'s signing email no longer lets {contact} sign.
- {name} is still in the assistant's file storage, unchanged.

## Fail when
- A reminder or a new signing email reaches {contact} after message 3.
- {name} is changed or deleted, or any other file is created.

## Cleanup
- Cancel the signature request if it is still open.
- Delete {name}.
- Trash every email the signature service sent during the run, in every mailbox that holds a copy.
