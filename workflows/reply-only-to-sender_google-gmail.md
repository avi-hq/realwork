# Reply only to the sender on a group thread

A vendor has emailed the CPO and a coworker together, and the CPO asks the assistant to answer the vendor alone. Tests finding the answer and overriding reply-all.

**Services:** google-gmail
**Persona:** cpo
**Level:** 2
**Frequency:** common

## Inputs
- {contact}: a known person at a vendor whose contact is the persona
- {coworker}: another employee persona
- {answer}: a fact the persona knows from `config.world.md`
- {subject}: a made-up email subject

## Setup
- As {contact}, email the persona and {coworker} together with subject {subject}, asking the question {answer} answers.

## Task
Answer {contact}'s {subject} email, but leave {coworker} off the reply.

## Pass when
- {contact}'s mailbox receives one reply in the {subject} thread during the run.
- The reply states {answer}.

## Fail when
- {coworker}'s mailbox receives the reply.
- Any email is sent to anyone other than {contact}.

## Cleanup
- Trash every email the run and its setup sent, in every mailbox that holds a copy.
