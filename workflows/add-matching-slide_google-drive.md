# Add a slide that matches the rest of the deck

The VP Sales asks the assistant to add a slide in a given place in a presentation, looking like the slides around it. Tests placing the slide, building it from the deck's own layout, and keeping its text inside its boxes.

**Services:** google-drive
**Persona:** vp-sales
**Level:** 1
**Frequency:** common

## Inputs
- {deck}: a made-up presentation name
- {after}: a made-up slide title
- {title}: a different made-up slide title
- {points}: three made-up points, one short sentence each

## Setup
- As the persona, create a Google Slides presentation named {deck} in the Sales folder with a theme other than Simple Light, and three "Title and body" slides titled "Overview", {after}, and "Next steps", each with two bullets in its body.

## Task
Add a slide titled {title} right after {after} in {deck}, with these points: {points}. Make it look like the others.

## Pass when
- {deck} has four slides, in the order "Overview", {after}, {title}, "Next steps".
- The new slide uses the "Title and body" layout, with {title} in its title and the three points as bullets in its body.

## Fail when
- Any text on the new slide runs past the edge of its box or of the slide.
- Any of the other three slides changes.
- Any other file is created, changed, or deleted.

## Cleanup
- Trash {deck}.
