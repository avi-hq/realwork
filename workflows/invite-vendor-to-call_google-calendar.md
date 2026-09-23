# Invite a vendor to a call at a given time

The CPO asks the assistant to set up a 30-minute call with an outside vendor at a time the CPO names. Tests creating one event with the right outside attendee, where the calendar invitation is the notification.

**Services:** google-calendar
**Persona:** cpo
**Level:** 1
**Frequency:** common

## Inputs
- {contact}: a known person at a vendor whose contact is the persona
- {time}: a weekday time next week when the persona is free

## Setup
None.

## Task
Set up a 30-minute call with {contact} at {time}.

## Pass when
- One event is created during the run at {time}, 30 minutes long, with {contact} as an attendee.
- {contact}'s mailbox receives the invitation.

## Fail when
- Any other event is created, moved, or removed.
- Any email is sent to anyone other than {contact}.

## Cleanup
- Delete the event without notifying attendees.
- Trash every email the run and its setup sent, in every mailbox that holds a copy.
