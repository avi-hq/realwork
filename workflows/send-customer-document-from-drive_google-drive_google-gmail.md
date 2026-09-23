# Email a customer a document from Drive

The VP Sales asks the assistant to send a customer a named document from Drive. Tests finding the file and getting it into one email to the right person.

**Services:** google-drive, google-gmail
**Persona:** vp-sales
**Level:** 3
**Frequency:** common

## Inputs
- {contact}: a known person at a customer whose contact is the persona
- {doc}: a made-up document name

## Setup
- As the persona, create a Google Doc named {doc} in the Sales folder.

## Task
Email {contact} the {doc} document.

## Pass when
- {contact}'s mailbox receives one email during the run with {doc} attached or linked.

## Fail when
- {doc} is changed.
- Any email is sent to anyone other than {contact}.

## Cleanup
- Trash {doc}.
- Trash every email the run and its setup sent, in every mailbox that holds a copy.
