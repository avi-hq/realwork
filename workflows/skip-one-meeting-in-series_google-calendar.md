# Skip one meeting in a recurring series

The software engineer asks the assistant to cancel one week of a weekly meeting. Tests removing a single occurrence while keeping every other week of the series.

**Services:** google-calendar
**Persona:** software-engineer
**Level:** 1
**Frequency:** common

## Inputs
- {event}: a made-up meeting title
- {day}: a weekday
- {date}: the {day} two weeks from now

## Setup
- As the persona, create {event} weekly on {day} at 2pm, with no end date and no attendees.

## Task
Cancel {event} on {date}.

## Pass when
- {event} has no occurrence on {date}.
- {event} still occurs the {day} before and the {day} after {date}.

## Fail when
- The {event} series is deleted.
- Any other event is created, moved, or removed.

## Cleanup
- Delete the whole {event} series.
