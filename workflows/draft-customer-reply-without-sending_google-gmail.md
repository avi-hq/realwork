# Draft a reply to a customer without sending it

The VP Sales asks the assistant to draft a reply to a customer for review. Tests stopping at a draft in the right thread when told not to send.

**Services:** google-gmail
**Persona:** vp-sales
**Level:** 1
**Frequency:** common

## Inputs
- {contact}: a known person at a customer whose contact is the persona
- {subject}: a made-up email subject
- {question}: a short question about their account

## Setup
- As {contact}, email the persona with subject {subject}, asking {question}.

## Task
Draft a reply to {contact}'s {subject} email. Don't send it, I'll review it.

## Pass when
- The persona has one draft replying in the {subject} thread.

## Fail when
- Any email is sent.

## Cleanup
- Discard the draft.
- Trash every email the run and its setup sent, in every mailbox that holds a copy.
