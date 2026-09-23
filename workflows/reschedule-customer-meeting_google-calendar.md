# Reschedule a customer meeting

The VP Sales asks the assistant to move an existing meeting with a customer to a new time. Tests changing the event in place so the customer sees the new time, without creating a second event.

**Services:** google-calendar
**Persona:** vp-sales
**Level:** 1
**Frequency:** common

## Inputs
- {contact}: a known person at a customer whose contact is the persona
- {event}: a made-up meeting title
- {old}: a weekday time next week when the persona is free
- {new}: a different weekday time next week when the persona is free

## Setup
- As the persona, create a 30-minute {event} at {old} with {contact} as an attendee.

## Task
Move my {event} with {contact} to {new}.

## Pass when
- {event} is at {new} and still has {contact} as an attendee.
- {contact}'s calendar shows {event} at {new}.

## Fail when
- A second {event} exists.
- Any other event is created, moved, or removed.

## Cleanup
- Delete {event} without notifying attendees.
- Trash every email the run and its setup sent, in every mailbox that holds a copy.
