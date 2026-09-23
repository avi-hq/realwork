# Tell a contact a meeting moved

The VP Sales asks the assistant to email an outside contact that a meeting has moved to a new time. Tests sending exactly one correct email from a short instruction, to the right person, without touching the calendar.

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
