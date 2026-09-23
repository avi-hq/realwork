# Forward a customer's email to a coworker with a note

The VP Sales asks the assistant to forward a customer's email with an attachment to a coworker. Tests forwarding the right message, attachment included, to the right person.

**Services:** google-gmail
**Persona:** vp-sales
**Level:** 1
**Frequency:** common

## Inputs
- {contact}: a known person at a customer whose contact is the persona
- {coworker}: another employee persona
- {subject}: a made-up email subject

## Setup
- As {contact}, email the persona with subject {subject} and a small attached file.

## Task
Forward {contact}'s {subject} email to {coworker} and ask them to take a look.

## Pass when
- {coworker}'s mailbox receives one forward of {subject}, with the attachment.

## Fail when
- Any email is sent to anyone other than {coworker}.

## Cleanup
- Trash every email the run and its setup sent, in every mailbox that holds a copy.
