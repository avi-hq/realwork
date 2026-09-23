# Label and archive every thread from one company

The VP Sales asks the assistant to label everything from one company and clear it out of the inbox. Tests finding every thread from that company and changing only those.

**Services:** google-gmail
**Persona:** vp-sales
**Level:** 2
**Frequency:** uncommon

## Inputs
- {company}: a customer whose contact is the persona
- {other}: a different external company
- {label}: a made-up label name

## Setup
- As a person at {company}, send the persona two emails with different subjects.
- As a person at {other}, send the persona one email.

## Task
Label everything from {company} as {label} and archive it.

## Pass when
- Both setup threads from {company} have {label} and are out of the inbox.

## Fail when
- The thread from {other} is labeled or archived.
- Any thread not from {company} is labeled or archived.

## Cleanup
- Move every thread the run archived back to the inbox.
- Delete {label}.
- Trash every email the run and its setup sent, in every mailbox that holds a copy.
