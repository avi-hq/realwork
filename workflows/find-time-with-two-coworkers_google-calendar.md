# Find a time with two coworkers and book it

The CPO asks the assistant to find a half hour next week that suits two coworkers and book it. Tests reading other people's availability, then booking one slot that is free for all three.

**Services:** google-calendar
**Persona:** cpo
**Level:** 2
**Frequency:** common

## Inputs
- {first}: another employee persona
- {second}: a third employee persona
- {event}: a made-up meeting title

## Setup
None.

## Task
Find 30 minutes next week that work for me, {first}, and {second}, and book {event}.

## Pass when
- One {event} is created during the run next week, 30 minutes long, with {first} and {second} as attendees.
- None of the three had another event at that time.

## Fail when
- More than one event is created.
- Any other event is moved or removed.

## Cleanup
- Delete {event} without notifying attendees.
- Trash every email the run and its setup sent, in every mailbox that holds a copy.
