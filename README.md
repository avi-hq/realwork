# RealWork

A simple benchmark for AI assistants doing real business work in real tools.

Simple means: every file is markdown, there is no runner, no schema, no harness code, and no simulated apps. A workflow is a task written the way an employee would say it, plus a plain-English list of what must be true afterwards. You give the task to the assistant, look in the real Gmail or Calendar, and mark pass or fail. Anyone with a test company and an afternoon can run it.

Each pass condition is checked in a real service. The assistant under test is a harness. Avi is the first. It runs against an employer, a test company on a real domain with real accounts, and any harness that can be connected to that employer can run the same workflows.

```
README.md                   everything: rules, setup, how to run, guidelines
config.world.example.md     the cast: employers, their people and services, outside companies
config.harness.example.md   the assistant under test: its services, how to connect, run, and reset it
workflows/                  one file per workflow, flat
runs/                       one file per run
```

Copy the two example files, fill them in, and keep them somewhere private. They hold real domains and sign-in details, so they never go in this repo. The operator needs those two files and the workflows, nothing else. Run records in `runs/` are public and belong here.

## Workflows

One markdown file each. This is the template. Copy it.

```markdown
# Reschedule a customer meeting

The VP Sales asks the assistant to move an existing meeting with a customer to a new time. Tests changing the event in place so the customer sees the new time, without creating a second event.

**Services:** google-calendar
**Persona:** vp-sales
**Level:** 1
**Frequency:** common

## Inputs
- {contact}: a known person at a customer whose contact is the persona
- {event}: a made-up meeting title
- {old}: a weekday time next week when the persona is free
- {new}: a different weekday time next week when the persona is free

## Setup
- As the persona, create a 30-minute {event} at {old} with {contact} as an attendee.

## Task
Move my {event} with {contact} to {new}.

## Pass when
- {event} is at {new} and still has {contact} as an attendee.
- {contact}'s calendar shows {event} at {new}.

## Fail when
- A second {event} exists.
- Any other event is created, moved, or removed.

## Cleanup
- Delete {event} without notifying attendees.
- Trash every email the run and its setup sent, in every mailbox that holds a copy.
```

**Description** is two sentences under the title. The first says who asks the assistant to do what, in plain words. The second starts with "Tests" and says what makes the workflow hard or what it is really checking. Someone skimming the folder should know what a workflow does from this alone.

**Filename** is the slug, then each service in alphabetical order, joined with underscores: `reschedule-customer-meeting_google-calendar.md`, `offer-customer-open-times_google-calendar_google-gmail.md`. Hyphens inside a slug or a service, underscores between them. The same work on a different provider is the same slug with a different suffix, so `reschedule-customer-meeting_microsoft-calendar.md` sits beside it. To add a provider, copy the file, change the suffix and the Services line, keep everything else identical.

**Services** are `company-product`, lowercase. Never the product alone. List the services the assistant must act in.

| Provider | Services |
|---|---|
| google | `google-gmail`, `google-calendar`, `google-drive`, `google-contacts` |
| microsoft | `microsoft-outlook`, `microsoft-calendar`, `microsoft-onedrive`, `microsoft-contacts` |
| hubspot | `hubspot-crm` |
| avi | `avi-drive` |

A service named after a harness, like `avi-drive`, lives inside that harness rather than at the employer. Only the harness needs it, and every other harness skips it.

**Persona** is one of the five personas every employer has: `ceo`, `cpo`, `hr`, `software-engineer`, `vp-sales`.

**Level.** 1 simple, one service. 2 complex, one service. 3 simple, two or more services. 4 complex, two or more services. Simple means everything needed is in the task. Complex means details must be found in existing emails, events, files, or records.

**Frequency** is `common` or `uncommon` for that role in a normal week.

**Inputs** are placeholders in braces, each with one line on how to pick it. The operator picks fresh values every run and writes them down first. People and companies are picked from `config.world.md` by relationship and contact, never by name, so the same workflow runs against any employer and any outside companies a world holds. Never reuse a combination two runs in a row. Task, pass lines, and fail lines use the same placeholders.

**Task** is usually one message. A task written as numbered messages is sent one message at a time, each after the assistant says it has finished the one before.

**Pass when** and **Fail when** lines are self-contained, binary, checkable in the real service, and name the exact person, thread, event, file, or record. Never a line about tone or quality. Lines are judged on what changed during the run, not the whole account. A workflow passes only when every pass line holds and no fail line fires.

**Setup** is what the operator creates before the task, acting as the persona, a coworker, or an outside person: an email to answer, a meeting to move, a file to rename. Anything a workflow changes, moves, or deletes is created by its own Setup, so no run ever touches the seeded world. `None.` when nothing is needed.

**Cleanup** is what the operator does after judging, pass or fail, even when the run was stopped. It undoes everything the run and its Setup created or changed: delete events without notifying attendees, trash emails in every mailbox that holds a copy, discard drafts, trash files and folders, delete contacts and labels, and put back anything renamed, moved, archived, or edited. Every run leaves the world exactly as seeded. Reset clears everything before and after a session, but workflows run one after another inside it, so anything one leaves behind changes the next.

**Order** of a workflow file: title, description, fields, Inputs, Setup, Task, Pass when, Fail when, Cleanup.

## World

`config.world.md` is the cast. Nothing about a person, company, service, or domain lives anywhere else. The repo ships `config.world.example.md`. Copy it to `config.world.md`, put in domains you own, and keep it out of git. The example's names are made up and its domains end in `.example`.

**Employers** are what gets tested. Each is one company on one registered domain with one list of services and its own five people. Add as many as you like: one on Google, one on Microsoft, one with no CRM. A workflow runs on an employer only if the employer's services include every service the workflow needs. Every employer has the same five persona headings, so a workflow's Persona line means the same role anywhere. Under each heading: one line with name, title, and address, then the facts that person knows as bullets.

**External** companies are shared by every employer and grouped by type: Customers, Vendors, Prospects. Each has a name, its own registered domain, the persona that is its contact, its people as bullets, and facts as bullets.

**Outside users** are real Google Workspace users on their company's domain, and the operator signs in as them to read, send, and reply. The simplest home for them is the employer's own Workspace, with every external domain added as a secondary domain and the outside users in their own organizational unit. Google then treats them as coworkers, which the current workflows don't care about. Use a separate tenant instead if you want Google itself to treat them as outsiders. Either way, nothing else exists on those domains. No catch-all, no forwarding, no aliases, so no mail ever crosses from one domain to another.

A world needs at least one employer, two customers, and one vendor for the current workflows to run.

## Operator

The operator is whoever drives the harness, a human or an agent in a VM. The operator is the persona and nothing more.

- Pick the inputs and write them down.
- Type the task exactly as written, inputs filled in.
- Answer questions only from the persona's facts, the company facts, and the inputs.
- If asked something not in the facts, say "your call" and nothing else.
- Never name a tool, a file, a record, or a screen.
- Never confirm that an answer is right.
- Never do the work.

## Harness

`config.harness.md` is the assistant under test: its name, the services it can act in, how to connect an employer to it, how to give it a task, and what to clear in it on Reset. Connection differs by harness. Avi connects through its apps per user, an MCP harness configures servers. Sign-in details live here and nowhere else, which is why the real file is never committed. The repo ships `config.harness.example.md` filled in for Avi.

A workflow runs when three things agree: the workflow's services, the employer's services, and the harness's services. A harness's own services, like `avi-drive`, only need the harness. Otherwise it is skipped. Skips count against coverage, never against pass rate.

## Setup

Once, before the first session.

1. **Copy `config.world.example.md` to `config.world.md`.** Register the domains: one per employer, one per external company, on mixed top-level domains as real companies would. Write them in.
2. **Outside users.** Add every external domain to a Google Workspace as a secondary domain. The employer's own Workspace is fine. Create one user per person listed under external companies, at their address, in an organizational unit named External.
3. **Employer tenant.** Google Workspace or Microsoft 365 on each employer's domain, in the time zone in `config.world.md`. One user per person in `config.world.md`.
4. **CRM**, if the employer has `hubspot-crm`. One free HubSpot account with the VP Sales as a user. Turn off automatic company creation from email domains. Rename the pipeline stages to New, Proposal Sent, Closed Won, Closed Lost.
5. **Harness.** Connect the employer to the harness per the Connect steps in `config.harness.md`.

## Reset

A session is one sitting in which a set of workflows runs against one employer. Every session starts from empty accounts and ends with empty accounts, so nothing from one session reaches the next. Reset runs twice per session: Clear and Seed before the first workflow, and Clear again after the last.

Clear touches only the accounts listed in `config.world.md` and the harness sign-ins for them. Never run it against any other account.

**Clear.** For every person at the employer and every outside user:

- **Mail.** Delete every message in every folder, including sent, drafts, and spam, then empty the trash. Delete every label you did not get by default, every filter, and any auto-reply.
- **Calendar.** Delete every event on every calendar, whole recurring series included, out-of-office and focus time included. Delete any extra calendars and booking pages.
- **Files.** Delete every file and folder the account owns in Drive or OneDrive, then empty the trash.
- **Contacts.** Delete every contact.
- **Tasks.** Delete every task in every task list, and every list except the default.
- **CRM**, if the employer has `hubspot-crm`. Delete every contact, company, deal, note, email, and task. Keep the pipeline stages.
- **Harness.** Everything the Reset section of `config.harness.md` lists, such as conversations and anything the assistant keeps between them.

Before seeding, open each account and check that it is empty.

**Seed.** Before the first workflow only. This is the seeded world. Workflows read it but never change it.

- **Contacts.** Give each person the external people at companies whose contact they are.
- **Calendar.** The software engineer gets a recurring "Standup", weekdays 9:30 to 9:45. Everyone gets a few recurring weekly meetings, some with their outside contacts.
- **Files.** One folder and one document each, in Drive or OneDrive. VP Sales "Sales" with "Proposal Template", software engineer "Engineering" with "Release Notes", CPO "Product" with "Roadmap", HR "People" with "Employee Handbook", CEO "Company" with "Board Update".
- **CRM**, if the employer has `hubspot-crm`. Add each customer with its people as contacts and one deal in stage "New". Prospects enter the CRM only when a workflow logs them.

## Running

1. Pick a harness and an employer. Filter workflows by level, service, persona, or frequency. Drop any the employer or harness cannot run.
2. **Reset before:** Clear, then Seed.
3. Run each workflow once, one after another:
   1. Pick its inputs from `config.world.md` and record them.
   2. Do the workflow's Setup.
   3. Give the task as the persona, in a new conversation.
   4. Judge every pass and fail line against what changed during the run.
   5. Do the workflow's Cleanup, whatever the result.
4. **Reset after:** Clear.
5. Record the run in `runs/YYYY-MM-DD-harness-employer.md`, using the harness name from `config.harness.md`, one row per workflow. Time is minutes and seconds from the task being sent to the assistant saying it is done, or to the operator stopping it. Report pass rate, coverage, and median time by level, by service, and by employer.

```markdown
# 2026-09-22 avi fernwood

**Workflow set:** v0.1

| Workflow | Inputs | Time | Result | Failed line |
|---|---|---|---|---|
| reschedule-customer-meeting_google-calendar | Dana, Renewal sync, Tue 2pm to Wed 10am | 0:48 | pass | |
| offer-customer-open-times_google-calendar_google-gmail | Ravi, Next week | 2:15 | fail | None of the three overlaps an event on the persona's calendar. |
```

## Versioning

The workflow set is tagged. A result cites the tag. Fixing a workflow bumps the tag.

## Guidelines

Check every workflow against this list before it goes in. Each line exists because it was got wrong once.

**Workflow files**

1. Copy the template. Every section, every field, in the order above. No extra sections.
2. Write the description. Two sentences: who asks for what, then "Tests" and what it checks. A title alone is not enough to know what a workflow does.
3. Filename is slug, underscore, then each service alphabetical with underscores between. Hyphens only inside a slug or a service. It must match the Services line exactly.
4. Services are `company-product` from the table above. `gmail` is wrong. `google-gmail` is right. A new service goes in the table first.
5. Persona is one of the five persona headings. Never a name.
6. Every `{placeholder}` in Task, Pass when, or Fail when is defined under Inputs.
7. Every workflow has inputs. A task with no inputs does the same thing every run and piles up identical artifacts. That is a bug.
8. People and companies are picked by relationship and contact, never named. "Email Dana" is wrong. "Email {contact}" with "{contact}: a person at a customer whose contact is the persona" is right.
9. Anything the task acts on that is not in the seeded world is created in Setup. Anything the workflow changes, moves, or deletes is created in Setup, never taken from the seed.
10. Every workflow has a Cleanup that undoes everything the run and its Setup created or changed. Test it by asking: after Cleanup, could the next run tell this one happened? If yes, Cleanup is incomplete.
11. Pass and fail lines name one exact thing and are checkable in the service. "The email is professional" is not a line. "{contact}'s mailbox receives one email that names {time}" is.
12. Every line is judged on what changed during the run. Write "during the run" when a count matters.
13. Every workflow has at least one fail line for a side effect: the wrong recipient, the wrong record, a changed event.
14. Anything the workflow depends on existing that it does not create itself, a folder, a file, a pipeline stage, a recurring event, is listed in the README's Seed or Setup. HubSpot's default stages are not "New" and "Proposal Sent". They are there because setup renames them.
15. A workflow is written once per provider. Same slug, same task, same lines. Only the Services line and the filename suffix differ. Never write a workflow that only works on one provider's quirk.
16. A workflow never assumes which employer it runs on. If it would read differently at a second employer, it is wrong.
17. No two workflows test the same thing. Each one checks an action, a decision, or a way to go wrong that no other workflow checks. The same action on different data is a duplicate.

**Config**

18. Never invent a domain. Every domain in `config.world.md` is one you own. `.example` belongs only in `config.world.example.md`.
19. Never put an outside person on an employer domain. Employees are inside, everyone else is outside, and the model is being tested on telling them apart.
20. Never share a root domain between external companies or employers. Subdomains of one root are still one root.
21. Outside users live in their own organizational unit, on their own domains. A separate tenant is optional. What is never optional is the domain: an outside person is never on an employer's domain.
22. Nothing about a person, company, service, or domain lives outside `config.world.md`. Nothing about the assistant under test lives outside `config.harness.md`. Not in a workflow, not in this README.
23. Every outside person is a real Workspace user. Never invent an address. Never add a catch-all, forwarding, or alias that lets mail cross domains.
24. Every employer has the same five persona headings. Facts and external company facts name roles, not employers, so they hold at every employer.

**Changing anything**

25. Renaming or removing anything in `config.world.md` means grepping the whole repo for the old value and fixing every hit.
26. Do not add documents. Rules go in this README. The cast goes in `config.world.md`. The assistant goes in `config.harness.md`. The template is the example above. If it does not fit, it is not simple enough yet.
