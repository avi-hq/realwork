# Answer a customer question

A customer has emailed a question, and the VP Sales asks the assistant to reply. Tests finding the right thread and the right fact without being told either, then answering in that thread without offering anything extra, like a discount.

**Services:** google-gmail
**Persona:** vp-sales
**Level:** 2
**Frequency:** common

## Inputs
- {contact}: a known person at a customer whose contact is the persona
- {answer}: a fact about that customer from `config.world.md`
- {thread}: an email thread from {contact} whose latest message asks the question {answer} answers, with no reply yet. If none exists, the operator sends one as {contact} before the run.

## Task
Reply to {contact}'s latest email.

## Pass when
- {contact}'s mailbox receives one reply in {thread} during the run.
- The reply states {answer}.

## Fail when
- The reply is sent as a new thread instead of in {thread}.
- The reply offers a discount.
- Any email is sent to anyone other than {contact}.
