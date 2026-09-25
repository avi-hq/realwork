# Resolve some comments and delete another

A coworker left three comments on the handbook, and the head of people asks the assistant to mark two as resolved and delete one that is out of date. Tests telling resolving apart from deleting and acting on exactly the right comments.

**Services:** harness-files
**Persona:** hr
**Level:** 2
**Frequency:** uncommon

## Inputs
- {name}: a made-up file name ending in .docx
- {coworker}: another employee persona
- {x}: a made-up one-word topic
- {y}: a different made-up one-word topic
- {z}: a third made-up one-word topic

## Setup
- Create {name}: a one-page handbook section, in Microsoft Word.
- With Word's user name set to {coworker}'s full name, add three comments on different phrases, one each about {x}, {y}, and {z}.
- Save it and add it to the assistant's own file storage, not through chat.

## Task
In {name}, mark {coworker}'s comments about {x} and {y} as resolved, and delete the one about {z}. It's out of date.

## Pass when
- The comments about {x} and {y} are still present and marked resolved.
- The comment about {z} is gone.
- The document text is unchanged.

## Fail when
- The {x} or {y} comment is deleted instead of resolved.
- The {z} comment is only resolved, not deleted.
- Any other file is created, changed, or deleted.

## Cleanup
- Delete every file the run and its Setup created.
