# Book an onboarding meeting with the newest hire and send the handbook

The head of people asks the assistant to book an onboarding meeting with the company's newest hire and send them the employee handbook. Tests working out who the newest hire is from company facts, then acting in the calendar, files, and mail together.

**Services:** google-calendar, google-drive, google-gmail
**Persona:** hr
**Level:** 4
**Frequency:** uncommon

## Inputs
- {time}: a time next Monday when the persona and the newest hire are both free

## Setup
None.

## Task
Book 30 minutes with our newest hire at {time} next Monday for onboarding, and send them the employee handbook.

## Pass when
- One event is created during the run next Monday at {time}, 30 minutes long, with the newest hire as an attendee.
- The newest hire's mailbox receives one email during the run with the Employee Handbook attached or linked.

## Fail when
- Any other event is created, moved, or removed.
- The Employee Handbook is changed.
- Any email is sent to anyone other than the newest hire.

## Cleanup
- Delete the event without notifying attendees.
- Trash every email the run sent, in every mailbox that holds a copy.
