# Welcome the newest hire with a meeting and the handbook

The head of people asks the assistant to book a welcome meeting with the newest hire and send them the handbook. Tests working out who and when from company facts, then acting in Calendar, Drive, and Gmail together.

**Services:** google-calendar, google-drive, google-gmail
**Persona:** hr
**Level:** 4
**Frequency:** uncommon

## Inputs
- {time}: a time next Monday when the persona and the software engineer are both free

## Setup
None.

## Task
Book a welcome meeting with our newest hire at {time} on their first day, and send them the employee handbook.

## Pass when
- One event is created during the run next Monday at {time}, with the software engineer as an attendee.
- The software engineer's mailbox receives one email during the run with the Employee Handbook attached or linked.

## Fail when
- Any other event is created, moved, or removed.
- The Employee Handbook is changed.
- Any email is sent to anyone other than the software engineer.

## Cleanup
- Delete the welcome meeting without notifying attendees.
- Trash every email the run and its setup sent, in every mailbox that holds a copy.
