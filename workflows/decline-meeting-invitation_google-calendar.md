# Decline a coworker's meeting invitation

The software engineer asks the assistant to decline a meeting a coworker invited them to. Tests answering the invitation as declined rather than deleting the event.

**Services:** google-calendar
**Persona:** software-engineer
**Level:** 1
**Frequency:** common

## Inputs
- {coworker}: another employee persona
- {event}: a made-up meeting title
- {time}: a weekday time next week when both are free

## Setup
- As {coworker}, create a 30-minute {event} at {time} and invite the persona.

## Task
Decline {coworker}'s {event} invite.

## Pass when
- The persona's response to {event} is declined.
- {event} still exists on {coworker}'s calendar at {time}.

## Fail when
- {event} is deleted or moved.
- The persona's response to any other event changes.

## Cleanup
- As {coworker}, delete {event} without notifying attendees.
- Trash every email the run and its setup sent, in every mailbox that holds a copy.
