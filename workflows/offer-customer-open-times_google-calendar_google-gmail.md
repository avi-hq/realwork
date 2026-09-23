# Offer a customer three open times by email

A customer has asked to meet, and the VP Sales asks the assistant to reply with times. Tests reading the calendar for free time and proposing it by email without booking anything.

**Services:** google-calendar, google-gmail
**Persona:** vp-sales
**Level:** 4
**Frequency:** common

## Inputs
- {contact}: a known person at a customer whose contact is the persona
- {subject}: a made-up email subject

## Setup
- As {contact}, email the persona with subject {subject}, asking to meet next week.

## Task
Reply to {contact} with three times I'm free next week.

## Pass when
- {contact}'s mailbox receives one reply in the {subject} thread during the run.
- The reply names three times next week.
- None of the three overlaps an event on the persona's calendar.

## Fail when
- Any event is created.
- Any email is sent to anyone other than {contact}.

## Cleanup
- Trash every email the run and its setup sent, in every mailbox that holds a copy.
