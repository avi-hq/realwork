# Reply to a customer's question from company facts

A customer has emailed a question, and the VP Sales asks the assistant to reply. Tests finding the right thread and the right fact without being told either, then answering in that thread without offering anything extra, like a discount.

**Services:** google-gmail
**Persona:** vp-sales
**Level:** 2
**Frequency:** common

## Inputs
- {contact}: a known person at a customer whose contact is the persona
- {answer}: a fact about that customer from `config.world.md`
- {subject}: a made-up email subject

## Setup
- As {contact}, email the persona with subject {subject}, asking the question {answer} answers.

## Task
Reply to {contact}'s latest email.

## Pass when
- {contact}'s mailbox receives one reply in the {subject} thread during the run.
- The reply states {answer}.

## Fail when
- The reply is sent as a new thread.
- The reply offers a discount.
- Any email is sent to anyone other than {contact}.

## Cleanup
- Trash every email the run and its setup sent, in every mailbox that holds a copy.
