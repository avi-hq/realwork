# Reorder a deck and hide a slide

The CPO asks the assistant to move one slide to the front of a presentation and hide another. Tests the order and the hidden state, with nothing deleted.

**Services:** google-drive
**Persona:** cpo
**Level:** 1
**Frequency:** uncommon

## Inputs
- {deck}: a made-up presentation name
- {titles}: five made-up slide titles, in order
- {first}: the fourth of {titles}
- {hidden}: the second of {titles}

## Setup
- As the persona, create a Google Slides presentation named {deck} in the Product folder with five "Title and body" slides titled {titles}, in that order.

## Task
In {deck}, make {first} the first slide and hide {hidden}.

## Pass when
- {deck}'s slides are, in order: {first}, then the other four titles in their original order.
- {hidden} is skipped in the presentation (Google Slides shows it as hidden) and still in the deck.

## Fail when
- Any slide is deleted or changed, or any slide other than {hidden} is hidden.
- Any other file is created, changed, or deleted.

## Cleanup
- Trash {deck}.
