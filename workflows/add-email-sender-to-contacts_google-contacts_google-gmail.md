# Add the sender of an email to contacts

Someone new has emailed the CEO, and the CEO asks the assistant to add them to contacts. Tests finding the email and pulling the person's name, address, and company into one new contact.

**Services:** google-contacts, google-gmail
**Persona:** ceo
**Level:** 4
**Frequency:** common

## Inputs
- {contact}: a known external person who is not in the persona's contacts

## Setup
- As {contact}, email the persona a short introduction, signed with their name, title, and company.

## Task
Add the person who just emailed me to my contacts.

## Pass when
- One contact is created during the run with {contact}'s name, address, and company.

## Fail when
- More than one contact is created.
- Any existing contact is changed.

## Cleanup
- Delete the contact.
- Trash every email the run and its setup sent, in every mailbox that holds a copy.
