# Update a contact's title after they announce a new role

A customer has emailed that they have a new job title, and the VP Sales asks the assistant to update contacts. Tests finding the news in the email and changing the existing contact instead of creating a new one.

**Services:** google-contacts, google-gmail
**Persona:** vp-sales
**Level:** 4
**Frequency:** uncommon

## Inputs
- {contact}: a known person at a customer, already in the persona's contacts
- {title}: a made-up job title

## Setup
- As {contact}, email the persona that they are now {title}.

## Task
Update my contacts with {contact}'s news.

## Pass when
- {contact}'s contact has the title {title}.

## Fail when
- A new contact is created.
- Any other contact is changed.

## Cleanup
- Set {contact}'s title back to what it was.
- Trash every email the run and its setup sent, in every mailbox that holds a copy.
