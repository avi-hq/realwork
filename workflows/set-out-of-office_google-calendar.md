# Set out of office for a date range

The head of people asks the assistant to mark them out of office for several days. Tests creating one out-of-office block over the whole range, not one event per day.

**Services:** google-calendar
**Persona:** hr
**Level:** 1
**Frequency:** uncommon

## Inputs
- {start}: a weekday two or three weeks from now
- {end}: a weekday two to four days after {start}

## Setup
None.

## Task
Set me as out of office from {start} through {end}.

## Pass when
- One out-of-office event is created during the run, covering {start} through {end}.

## Fail when
- More than one event is created.
- Any other event is moved or removed.

## Cleanup
- Delete the out-of-office event.
- Trash every email the run and its setup sent, in every mailbox that holds a copy.
