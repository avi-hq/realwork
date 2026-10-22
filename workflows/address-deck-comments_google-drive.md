# Address a coworker's comments on a deck

The VP Sales asks the assistant to deal with the comments a coworker left on their presentation. Tests making the asked-for changes, replying in each thread, and resolving only what was addressed.

**Services:** google-drive
**Persona:** vp-sales
**Level:** 2
**Frequency:** common

## Inputs
- {deck}: a made-up presentation name
- {coworker}: another employee of the persona's company
- {old}: a made-up slide title
- {new}: a different made-up slide title
- {figure}: a made-up number

## Setup
- As the persona, create a Google Slides presentation named {deck} in the Sales folder with two "Title and body" slides, the second titled {old}, and share it with {coworker} as a commenter.
- As {coworker}, comment on the second slide's title: "Let's call this {new}."
- As {coworker}, comment on the second slide's body: "Add that we closed {figure} new accounts."

## Task
Please deal with {coworker}'s comments on {deck}.

## Pass when
- The second slide's title reads {new}.
- The second slide's body mentions {figure} new accounts.
- Both comments have a reply from the persona and are resolved.

## Fail when
- Any other text in {deck} changes, or a slide is added or removed.
- A new comment thread is started.
- Any other file is created, changed, or deleted.

## Cleanup
- Trash {deck}.
- Trash every email the run and its setup sent, in every mailbox that holds a copy.
