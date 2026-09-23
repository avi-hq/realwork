# Add a coworker to an existing meeting

The CPO asks the assistant to add a coworker to a meeting already on the calendar. Tests updating the attendee list of the right event without moving it or making a copy.

**Services:** google-calendar
**Persona:** cpo
**Level:** 1
**Frequency:** common

## Inputs
- {coworker}: another employee persona
- {event}: a made-up meeting title
- {time}: a weekday time next week when the persona is free

## Setup
- As the persona, create a 30-minute {event} at {time} with no attendees.

## Task
Add {coworker} to my {event} meeting.

## Pass when
- {event} is still at {time} and has {coworker} as an attendee.
- {coworker}'s calendar shows {event}.

## Fail when
- A second {event} exists.
- {event} is moved.
- Any other event is created, moved, or removed.

## Cleanup
- Delete {event} without notifying attendees.
- Trash every email the run and its setup sent, in every mailbox that holds a copy.
