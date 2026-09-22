# Tell a contact a meeting moved

**Services:** google-gmail
**Persona:** vp-sales
**Level:** 1
**Frequency:** common

## Inputs
- {contact}: a person at an external company whose contact is the persona
- {event}: a meeting on the persona's calendar in the next two weeks
- {time}: a weekday time next week when the persona is free

## Task
Email {contact} and let them know {event} moved to {time}.

## Pass when
- {contact}'s mailbox receives one email during the run that names {event} and {time}.

## Fail when
- Any email is sent to anyone other than {contact}.
- Any calendar event is changed.
