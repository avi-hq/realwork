# Avi

EXAMPLE. Copy this file to `config.harness.md` and fill in the assistant under test. `config.harness.md` is gitignored because it holds sign-in details.

**Services:** google-gmail, google-calendar, google-drive, google-contacts, avi-drive

## Connect

Once per employer. Avi connects through its apps, one account per user, not through MCP. Each person in the employer signs in at https://avi.run with their account on the employer's domain and connects Google when Avi asks. That covers Gmail, Calendar, Drive, and Contacts.

## Run

Sign in at https://avi.run as the persona. Open a new chat for every workflow and paste the task. Answer clarifying questions as the persona.

## Reset

Part of Clear, before and after every session. Sign in at https://avi.run as each person in the employer and delete:

- Every conversation.
- Every background agent and anything scheduled to run.
- Everything in Avi Drive: files, notes, documents, and folders.
- Every Avi task.
- Anything else Avi keeps between conversations, such as memories.

Keep Google connected. Reconnecting is part of Setup, not Reset.
