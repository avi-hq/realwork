# Create a weekly recurring focus block

The software engineer asks the assistant to block the same two hours every week for focused work. Tests creating one recurring event with the right day, times, and repeat rule.

**Services:** google-calendar
**Persona:** software-engineer
**Level:** 1
**Frequency:** uncommon

## Inputs
- {day}: a weekday
- {start}: a morning time
- {end}: two hours after {start}

## Setup
None.

## Task
Block every {day} from {start} to {end} for focus time.

## Pass when
- One recurring event is created during the run, from {start} to {end} on {day}.
- It occurs next {day} and four {day}s from now.

## Fail when
- More than one event is created.
- Any other event is moved or removed.

## Cleanup
- Delete the whole series the run created.
