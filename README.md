# RealWork

A benchmark for AI assistants doing real business work in real tools.

Each workflow is a task a real employee would give an assistant. Each pass condition is checked in a real service. The assistant under test is a harness. Avi is the first. It runs against an employer, a test company on a real domain with real accounts, and any harness that can be connected to that employer can run the same workflows.

```
README.md                   everything: rules, setup, how to run, guidelines
config.world.example.md     the cast: employers, their people and services, outside companies
config.harness.example.md   the assistant under test: its services, how to connect, how to run
workflows/                  one file per workflow, flat
runs/                       one file per run
```

Copy the two example files to `config.world.md` and `config.harness.md` and fill them in. Both are gitignored.

## Workflows

One markdown file each. This is the template. Copy it.

```markdown
# Tell a contact a meeting moved

**Services:** google-gmail
**Persona:** vp-sales
**Level:** 1
**Frequency:** common

## Inputs
- {contact}: a person at an external company whose contact is the persona
- {event}: a meeting on the persona's calendar in the next two weeks
- {time}: a weekday time next week when the persona is free

## Task
Email {contact} and let them know {event} moved to {time}.

## Pass when
- {contact}'s mailbox receives one email during the run that names {event} and {time}.

## Fail when
- Any email is sent to anyone other than {contact}.
- Any calendar event is changed.
```

**Filename** is the slug, then each service in alphabetical order, joined with underscores: `tell-contact-meeting-moved_google-gmail.md`, `book-call-and-notify_google-calendar_google-gmail.md`. Hyphens inside a slug or a service, underscores between them. The same work on a different provider is the same slug with a different suffix, so `tell-contact-meeting-moved_microsoft-outlook.md` sits beside it. To add a provider, copy the file, change the suffix and the Services line, keep everything else identical.

**Services** are `company-product`, lowercase. Never the product alone. List the services the assistant must act in.

| Provider | Services |
|---|---|
| google | `google-gmail`, `google-calendar`, `google-drive`, `google-contacts` |
| microsoft | `microsoft-outlook`, `microsoft-calendar`, `microsoft-onedrive`, `microsoft-contacts` |
| hubspot | `hubspot-crm` |

**Persona** is one of the five personas every employer has: `ceo`, `cpo`, `hr`, `software-engineer`, `vp-sales`.

**Level.** 1 simple, one service. 2 complex, one service. 3 simple, two or more services. 4 complex, two or more services. Simple means everything needed is in the task. Complex means details must be found in existing emails, events, files, or records.

**Frequency** is `common` or `uncommon` for that role in a normal week.

**Inputs** are placeholders in braces, each with one line on how to pick it. The operator picks fresh values every run and writes them down first. People and companies are picked from `config.world.md` by relationship and contact, never by name, so the same workflow runs against any employer and any outside companies a world holds. If an input does not exist yet, the operator makes it before the run, acting as an outside person where needed. Never reuse a combination two runs in a row. Task, pass lines, and fail lines use the same placeholders.

**Pass when** and **Fail when** lines are self-contained, binary, checkable in the real service, and name the exact person, thread, event, file, or record. Never a line about tone or quality. Lines are judged on what changed during the run, not the whole account. A workflow passes only when every pass line holds and no fail line fires.

**Nothing is finite.** A workflow never needs a new account or domain to run again. When it needs a fresh thing, it invents a person at an existing external company, or uses a record an earlier workflow created. A run that needs something bought or provisioned first is a bug in the workflow.

## World

`config.world.md` is the cast. Nothing about a person, company, service, or domain lives anywhere else. The repo ships `config.world.example.md`. Copy it to `config.world.md`, put in domains you own, and keep it out of git. The example's names are made up and its domains end in `.example`.

**Employers** are what gets tested. Each is one company on one registered domain with one list of services and its own five people. Add as many as you like: one on Google, one on Microsoft, one with no CRM. A workflow runs on an employer only if the employer's services include every service the workflow needs. Every employer has the same five persona headings, so a workflow's Persona line means the same role anywhere. Under each heading: one line with name, title, and address, then the facts that person knows as bullets.

**External** companies are shared by every employer. Each has a name, its own registered domain, a relationship of `customer`, `vendor`, or `prospect`, the persona that is its contact, its known people as bullets, and facts as bullets.

**The outside world** is one Google Workspace of its own, separate from every employer. Every external domain is a domain in it. Every known external person is a real user in it, and the operator signs in as them to read, send, and reply. A catch-all on each domain routes any other address to one mailbox, so a workflow may invent a person at any external company. Known people can send and receive. Invented people can only receive.

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

`config.harness.md` is the assistant under test: its name, the services it can act in, how to connect an employer to it, and how to give it a task. Connection differs by harness. Avi connects through its apps per user, an MCP harness configures servers. Sign-in details live here and nowhere else, which is why the real file is never committed. The repo ships `config.harness.example.md` filled in for Avi.

A workflow runs when three things agree: the workflow's services, the employer's services, and the harness's services. Otherwise it is skipped. Skips count against coverage, never against pass rate.

## Setup

Once. Never reset afterwards. Every run adds to it, the way a real company's accounts fill up.

**Common**

1. **Copy `config.world.example.md` to `config.world.md`.** Register the domains: one per employer, one per external company, on mixed top-level domains as real companies would. Write them in.
2. **The outside Workspace.** One Google Workspace, separate from every employer, in the time zone in `config.world.md`. Add every external domain to it. Create one user per person listed under external companies, at their address.
3. **Catch-all.** In that Workspace, route unknown addresses on every external domain to the catch-all mailbox in `config.world.md`.

**Per employer**, according to its services

4. **Tenant.** Google Workspace or Microsoft 365 on the employer's domain, in the time zone in `config.world.md`. One user per person in `config.world.md`.
5. **Contacts.** Give each person the external people at companies whose contact they are.
6. **Calendar.** The software engineer gets a recurring "Standup", weekdays 9:30 to 9:45. Everyone gets a handful of meetings over the next two weeks, some with their outside contacts. Top up whenever the next two weeks look empty.
7. **Files.** One folder and one document each, in Drive or OneDrive. VP Sales "Sales" with "Proposal Template", software engineer "Engineering" with "Release Notes", CPO "Product" with "Roadmap", HR "People" with "Employee Handbook", CEO "Company" with "Board Update".
8. **CRM**, if the employer has `hubspot-crm`. One free HubSpot account with the VP Sales as a user. Turn off automatic company creation from email domains. Rename the pipeline stages to New, Proposal Sent, Closed Won, Closed Lost. Add each customer with its people as contacts and one deal in stage "New". Nothing else. Prospects enter the CRM only when a workflow logs them.
9. **Harness.** Connect the employer to the harness per the connect steps in `config.harness.md`.

## Running

1. Pick a harness and an employer. Filter workflows by level, service, persona, or frequency. Drop any the employer or harness cannot run.
2. For each run, pick the inputs from `config.world.md` and record them.
3. Give the task as the persona.
4. Judge every pass and fail line against what changed during the run.
5. Run each workflow three times with different inputs. It passes only if all three pass.
6. Record the run in `runs/YYYY-MM-DD-harness-employer.md`, using the harness name from `config.harness.md`, one row per attempt. Time is minutes and seconds from the task being sent to the assistant saying it is done, or to the operator stopping it. Report pass rate, coverage, and median time by level, by service, and by employer.

```markdown
# 2026-09-22 avi fernwood

**Workflow set:** v0.1

| Workflow | Inputs | Time | Result | Failed line |
|---|---|---|---|---|
| tell-contact-meeting-moved_google-gmail | Dana, Halden sync, Tue 2pm | 0:48 | pass | |
| tell-contact-meeting-moved_google-gmail | Ravi, Q4 review, Wed 10am | 2:15 | fail | Any email is sent to anyone other than {contact} |
```

## Versioning

The workflow set is tagged. A result cites the tag. Fixing a workflow bumps the tag.

## Guidelines

Check every workflow against this list before it goes in. Each line exists because it was got wrong once.

**Workflow files**

1. Copy the template. Every section, every field, in that order. No extra sections.
2. Filename is slug, underscore, then each service alphabetical with underscores between. Hyphens only inside a slug or a service. It must match the Services line exactly.
3. Services are `company-product` from the table above. `gmail` is wrong. `google-gmail` is right. A new service goes in the table first.
4. Persona is one of the five persona headings. Never a name.
5. Every `{placeholder}` in Task, Pass when, or Fail when is defined under Inputs.
6. Every workflow has inputs. A task with no inputs does the same thing every run and piles up identical artifacts. That is a bug.
7. People and companies are picked by relationship and contact, never named. "Email Dana" is wrong. "Email {contact}" with "{contact}: a person at a customer whose contact is the persona" is right.
8. An input that may not exist yet says who makes it and how, in the input line.
9. Nothing is finite. If running the workflow three times a day for a year would ever need a new domain, account, or seed step, rewrite it to invent a person or reuse a record instead.
10. Pass and fail lines name one exact thing and are checkable in the service. "The email is professional" is not a line. "{contact}'s mailbox receives one email that names {time}" is.
11. Every line is judged on what changed during the run. Write "during the run" when a count matters.
12. Every workflow has at least one fail line for a side effect: the wrong recipient, the wrong record, a changed event.
13. Anything the workflow depends on existing, a folder, a file, a pipeline stage, a recurring event, is listed in Setup. HubSpot's default stages are not "New" and "Proposal Sent". They are there because setup renames them.
14. A workflow is written once per provider. Same slug, same task, same lines. Only the Services line and the filename suffix differ. Never write a workflow that only works on one provider's quirk.
15. A workflow never assumes which employer it runs on. If it would read differently at a second employer, it is wrong.

**Config**

16. Never invent a domain. Every domain in `config.world.md` is one you own. `.example` belongs only in `config.world.example.md`.
17. Never put an outside person on an employer domain. Employees are inside, everyone else is outside, and the model is being tested on telling them apart.
18. Never share a root domain between external companies or employers. Subdomains of one root are still one root.
19. Never put an external domain in an employer's tenant, and never put an employer's domain in the outside Workspace. The tenant boundary is what makes them outsiders.
20. Nothing about a person, company, service, or domain lives outside `config.world.md`. Nothing about the assistant under test lives outside `config.harness.md`. Not in a workflow, not in this README.
21. Known people send and receive. Invented people receive only. A workflow that needs an outside party to write in uses a known person.
22. Every employer has the same five persona headings. Facts and external company facts name roles, not employers, so they hold at every employer.

**Changing anything**

23. Renaming or removing anything in `config.world.md` means grepping the whole repo for the old value and fixing every hit.
24. Do not add documents. Rules go in this README. The cast goes in `config.world.md`. The assistant goes in `config.harness.md`. The template is the example above. If it does not fit, it is not simple enough yet.
