# Build a tracker with a status dropdown and a highlight

The software engineer asks the assistant for a task tracker where status is picked from a list and blocked work stands out. Tests a dropdown limited to given choices and a highlight driven by the cell's value.

**Services:** harness-files
**Persona:** software-engineer
**Level:** 1
**Frequency:** common

## Inputs
- {name}: a made-up file name ending in .xlsx
- {project}: a made-up project name
- {tasks}: four made-up tasks, each with an owner, a due date, and a status of Open, In progress, Blocked, or Done, at least one of them Blocked

## Setup
None.

## Task
Make a tracker named {name} for {project} with columns Task, Owner, Due, and Status, and add these tasks: {tasks}. Status should be a dropdown with Open, In progress, Blocked, and Done, and Blocked should show in red.

## Pass when
- One workbook named {name} is created during the run, with the four tasks under the headers Task, Owner, Due, and Status.
- Each due date shows as a date.
- Every Status cell reading Blocked is shaded red, and no other cell is.
- The reply says Status is a dropdown with exactly Open, In progress, Blocked, and Done.

## Fail when
- A task, owner, date, or status differs from what was given.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
