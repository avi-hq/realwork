# Reply only to the sender on a group thread

A vendor has emailed the CPO and a coworker together asking for a yes or no, and the CPO asks the assistant to answer the vendor alone. Tests overriding reply-all so the coworker is left off.

**Services:** google-gmail
**Persona:** cpo
**Level:** 1
**Frequency:** common

## Inputs
- {contact}: a known person at a vendor whose contact is the persona
- {coworker}: another employee persona
- {subject}: a made-up email subject
- {question}: a made-up yes-or-no question about the vendor's work

## Setup
- As {contact}, email the persona and {coworker} together with subject {subject}, asking {question}.

## Task
Tell {contact} yes on their {subject} email, but leave {coworker} off the reply.

## Pass when
- {contact}'s mailbox receives one reply in the {subject} thread during the run.
- The reply says yes.

## Fail when
- {coworker}'s mailbox receives the reply.
- Any email is sent to anyone other than {contact}.

## Cleanup
- Trash every email the run and its setup sent, in every mailbox that holds a copy.
