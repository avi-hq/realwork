# Confirm tomorrow's meetings that have outside attendees

The VP Sales asks the assistant to confirm tomorrow's meetings with people outside the company. Tests telling outside attendees from coworkers and sending one confirmation per outside meeting.

**Services:** google-calendar, google-gmail
**Persona:** vp-sales
**Level:** 4
**Frequency:** uncommon

## Inputs
- {contact}: a known person at a customer whose contact is the persona
- {coworker}: another employee persona
- {first}: a time tomorrow when the persona is free. Run only when tomorrow is a weekday.
- {second}: a different time tomorrow when the persona is free

## Setup
- As the persona, create a 30-minute meeting at {first} with {contact}.
- As the persona, create a 30-minute meeting at {second} with {coworker}.

## Task
Email everyone outside the company I'm meeting tomorrow to confirm.

## Pass when
- {contact}'s mailbox receives one email during the run that names {first}.
- Every other outside attendee of the persona's meetings tomorrow receives one email.

## Fail when
- {coworker}'s mailbox receives an email.
- Any event is created, moved, or removed.

## Cleanup
- Delete both setup meetings without notifying attendees.
- Trash every email the run and its setup sent, in every mailbox that holds a copy.
