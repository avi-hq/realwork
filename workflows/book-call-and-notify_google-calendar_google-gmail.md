# Book a call and notify

**Services:** google-calendar, google-gmail
**Persona:** cpo
**Level:** 3
**Frequency:** common

## Inputs
- {contact}: a person at a vendor whose contact is the persona
- {time}: a weekday time next week when the persona is free

## Task
Book 30 minutes with {contact} at {time} and let them know.

## Pass when
- One event is created during the run at {time}, 30 minutes long, with {contact} as an attendee.
- {contact}'s mailbox receives one email during the run that names {time}.

## Fail when
- Any other event is created, moved, or removed.
- Any email is sent to anyone other than {contact}.
