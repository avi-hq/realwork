# RealWork

A simple benchmark for AI assistants doing real business work in real tools.

Simple means every file is markdown, apart from the starter files in `artifacts/`. There is no runner, no schema, no harness code, and no simulated apps. A workflow is a task written the way an employee would say it, plus a plain-English list of what must be true afterwards. You give the task to the assistant, look in the real mailbox, calendar, or files, and mark pass or fail.

The assistant under test is the harness. It works for an employer: a test company on a real domain with real accounts. Any harness that can be connected to those accounts can run the same workflows.

```
README.md                   rules, setup, how to run, guidelines
config.world.example.md     the test company, its people, and the outside companies it works with
config.harness.example.md   the assistant under test: its services, how to connect, run, and reset it
sequence.md                 which workflows are solo or shared, and the order they run in
workflows/                  one file per workflow
artifacts/                  the starter files workflows copy in: spreadsheets, PDFs, a CSV
runs/                       one file per session's results
```

Copy the two example files, fill them in, and keep them private. They hold real domains and sign-in details, so they never go in this repo. Run records in `runs/` are public.

## Workflows

One markdown file each. Copy this template and keep every section, in this order.

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

**Description.** Two sentences under the title. The first says who asks the assistant to do what. The second starts with "Tests" and says what the workflow really checks.

**Filename.** The slug, then each service in alphabetical order, joined with underscores: `reschedule-customer-meeting_google-calendar.md`. Hyphens inside a slug or a service, underscores between them. The same work on another provider keeps the slug and changes the suffix, so `reschedule-customer-meeting_microsoft-calendar.md` sits beside it.

**Services.** The services the assistant must act in, named `company-product`:

| Provider | Services |
|---|---|
| google | `google-gmail`, `google-calendar`, `google-drive`, `google-contacts` |
| microsoft | `microsoft-outlook`, `microsoft-calendar`, `microsoft-onedrive`, `microsoft-contacts` |

`harness-files` is the one service that isn't a company's. It means the assistant's own file storage, for harnesses that have one.

**Persona.** One of the five roles every employer has: `ceo`, `cpo`, `hr`, `software-engineer`, `vp-sales`. A solo workflow runs in its persona's lane.

**Level.** 1 simple, one service. 2 complex, one service. 3 simple, two or more services. 4 complex, two or more services. Simple means everything needed is in the task. Complex means the assistant has to find details in existing emails, events, files, or contacts.

**Frequency.** `common` or `uncommon` for that role in a normal week.

**Inputs.** Placeholders in braces, each with one line on how to pick it. People and companies are picked by relationship and contact, never by name, so a workflow runs against any world. The operator picks values before each run, writes them down, and varies them between sessions.

**Setup.** What the operator creates before the task, acting as the persona, a coworker, or an outside person. Anything the workflow changes, moves, or deletes is created here, so no run touches the seeded world. `None.` when nothing is needed.

**Task.** What the operator types, inputs filled in. Numbered messages are sent one at a time, each after the assistant says it has finished the one before.

**Pass when** and **Fail when.** Each line is binary, checkable in the real service, and names the exact person, thread, event, file, or contact. Never a line about tone or quality. Lines are judged on what changed during the run. A workflow passes only when every pass line holds and no fail line fires.

**Checking documents.** Check Word documents in Microsoft Word, the reference for how a `.docx` looks: styles, page setup, fields, list formatting, and tracked changes. Check PDFs in a viewer that shows page size, fonts, and bookmarks, such as Adobe Acrobat Reader. A PDF "matches" a document page for page when it has the same page count, each page starts and ends with the same content, and the headers, footers, and page numbers are the same as in Word.

A harness with its own file storage (`harness-files`) is checked in that harness's own viewer, because the operator has no other way to open its files. Those workflows are written so every line can be seen on a rendered page: a heading by how it is set, a table of contents by its entries and page numbers, a PDF by its pages, a spreadsheet by its cells, their formats and highlighting, and the formula bar. A chart the viewer does not draw is checked in a PDF of its sheet. What only Word or Acrobat expose, such as style names, field codes, list definitions, repeat-header settings, PDF/A metadata, font embedding, and bookmark trees, is not a criterion; where it matters, the assistant's own reply is what gets checked.

**Redlines and comments.** A redline means Word's own tracked changes, and a comment means a Word comment. Strikethrough, underline, or colored text is not a redline, and a note typed into the body is not a comment. Check them in Word's review tools: each tracked change's type, text, author, and whether it is accepted; each comment's text, author, the exact text it is attached to, its replies, and whether it is resolved. When a Setup step makes a change as someone else, set Word's user name to that person's full name first.

**Cleanup.** What the operator undoes after judging, pass or fail, even if the run was stopped. It removes everything the run and its Setup created or changed: delete events without notifying attendees, trash emails in every mailbox that holds a copy, discard drafts, delete files, folders, contacts, and labels, and put back anything renamed, moved, archived, or edited. Workflows run one after another in a session, so anything left behind changes the next one.

## World

`config.world.md` describes the test company and everyone around it. Nothing about a person, company, or domain lives anywhere else. The shipped example uses made-up names and `.example` domains.

**Employers** are what gets tested. Each is one company on its own domain, with its list of services and its five people. Under each persona heading: one line with name, title, and address, then what that person knows, as bullets. Add as many employers as you like, for example one on Google and one on Microsoft. A workflow runs against an employer only if the employer has every service the workflow needs.

**External companies** are customers and vendors, shared by every employer. Each has its own domain, the persona who is its contact, its people, and what they know.

**Outside people** are real accounts on their company's domain. The operator signs in as them to read, send, and reply. They can live in the employer's own tenant, with each external domain added as a secondary domain and the outside people in their own organizational unit, or in a separate tenant. Either way, nothing else exists on those domains: no catch-all, no forwarding, no aliases.

The current workflows need at least one employer, two customers, and one vendor.

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

`config.harness.md` describes the assistant under test: its name, the services it can act in, how to connect an employer to it, how to give it a task, and what to clear in it on Reset. Sign-in details live only here. The repo ships an example for Avi.

A workflow runs only when the harness and the employer both have every service it needs. `harness-files` needs only the harness. Anything else is skipped. Skips count against coverage, never against pass rate.

## Setup

Once.

1. **Domains.** Copy `config.world.example.md` to `config.world.md`. Register one domain per employer and one per external company, on mixed top-level domains as real companies would. Write them in.
2. **Employer accounts.** For each employer, a Google Workspace or Microsoft 365 tenant on its domain, in the time zone in `config.world.md`. One account per person.
3. **Outside accounts.** Add every external domain to a tenant, the employer's or a separate one. One account per outside person, in an organizational unit named External.
4. **Harness.** Connect each employer to the harness, per `config.harness.md`. Each person's name in the harness is their full name from `config.world.md`, because tracked changes and comments are credited to it.
5. **Reference document.** Build `Reference.docx` in Microsoft Word, exactly as described under Reference document below, and keep it with your private config files.

## Reset

A session is one sitting in which workflows run against one employer. Reset runs before the first workflow, Clear then Seed, and after the last, Clear only. Every session starts from the same accounts and leaves nothing behind.

Each lane resets its own accounts, at the same time as the other lanes: its persona, the outside people whose contact is that persona, and that persona's harness storage. The Clear after the session covers every account, because the shared phase touches accounts across lanes.

Clear touches only the accounts in `config.world.md` and their harness sign-ins. Never any other account.

**Clear**, for every employer person and every outside person:

- **Mail.** Delete every message in every folder, including sent, drafts, and spam, then empty the trash. Delete labels you added, filters, and auto-replies.
- **Calendar.** Delete every event on every calendar, including whole recurring series, out-of-office, and focus time. Delete extra calendars and booking pages.
- **Files.** Delete every file and folder the account owns, then empty the trash.
- **Contacts.** Delete every contact.
- **Tasks.** Delete every task, and every task list except the default.
- **Harness.** Everything the Reset section of `config.harness.md` lists.

Then open each account and check that it is empty.

**Seed**, before the first workflow only. Workflows read the seed but never change it.

- **Contacts.** Each person gets the outside people at companies whose contact they are.
- **Calendar.** Everyone gets a few recurring weekly meetings, some with their outside contacts.
- **Files.** A folder named "Sales" for the VP Sales, "Product" for the CPO, and "People" for HR, holding a document named "Employee Handbook".
- **Assistant storage**, if the harness has `harness-files`. Add `Reference.docx` to the storage of each persona whose workflows use it.

**Reference document.** The Word document the export workflows start from. Build it once, exactly like this, and check it in Word before the first session.

- US Letter, portrait, 1-inch margins. Georgia everywhere: set the theme fonts for headings and body to Georgia, so Title, headings, body, header, and footer all use it. Body text in the Normal style, 11 point.
- Header: "Reference Document", right-aligned. Footer: "Page X of Y", centered, built from page number fields.
- The title "Quarterly Operations Review" in the Title style.
- Heading 1 "Summary": two paragraphs, then a bulleted list of three items with one second-level bullet under the second item.
- Heading 1 "Figures": a table with columns Region, Q1, Q2, and Q3 and 40 data rows. The header row is bold, shaded light gray, and set to repeat. The table runs onto page 2.
- Heading 2 "Notes", under Figures: a numbered list of three items with items a and b under item 2, then a sentence whose words "example site" link to https://example.com.
- A page break, then Heading 1 "Appendix" with one paragraph.
- Exactly three pages in Word, with the Appendix alone on page 3.

## Artifacts

`artifacts/` holds the files workflows start from. They are generated, not downloaded, so they never change between sessions and contain nothing real. A workflow's Setup adds a copy of the one it needs to the assistant's storage under the run's own file name, and its Cleanup deletes that copy. An artifact itself is never edited.

| File | What it is |
|---|---|
| `budget.xlsx` | A cloud budget: a Budget sheet of monthly costs by category with formula totals, an Expenses sheet of line items with a Total row, and a Summary sheet that reads both |
| `broken-formulas.xlsx` | A six-month forecast with two `#DIV/0!` errors and a `#REF!` revenue total |
| `card-export.csv` | A card export with leading-zero IDs, US dates, and amounts written with commas |
| `company-report.pdf` | A ten-page report with one distinct fact on each page |
| `scanned-receipt.pdf` | A scanned receipt: one page that is a picture, with no text in it |
| `vendor-tax-form.pdf` | A fillable vendor tax form whose fields have coded names and printed labels |
| `new-hire-form.pdf` | A printed form with labels and blank lines, and no fields |
| `contractor-agreement.pdf` | A two-page agreement with a COMPANY and a CONTRACTOR signature block |
| `offer-letter.pdf` | A two-page offer letter |
| `benefits-summary.pdf` | A three-page benefits summary whose page 2 shows sideways |
| `personnel-record.pdf` | A two-page record with a made-up Social Security number on page 2 |

## Running

`sequence.md` decides what runs and in what order. Nothing else does.

1. **Pick** a harness and an employer. A workflow whose services the harness or employer lacks is skipped and recorded as skipped.
2. **Reset before.** Every lane clears and seeds its own accounts, at the same time.
3. **Solo phase.** Every lane runs at the same time, each with its own operator signed in only as that lane's persona. Inside a lane, run each workflow once, one at a time, in the order `sequence.md` lists:
   1. Pick its inputs and write them down.
   2. Do its Setup.
   3. Give the task as the persona, in a new conversation.
   4. Judge every pass and fail line.
   5. Do its Cleanup, whatever the result.
4. **Shared phase.** After every lane has finished, run the Shared workflows one at a time, in order, the same five steps each. No lane is running, so their lines can count anything on any account.
5. **Reset after.** Clear every account.
6. **Record** the session in `runs/YYYY-MM-DD-harness-employer.md`. Copy `sequence.md`'s headings and workflow order, and fill in one row per workflow. Every workflow in `sequence.md` gets a row, run or skipped, so a missing row means a missed workflow. Time is minutes and seconds from sending the task to the assistant saying it is done, or to the operator stopping it. Report pass rate, coverage, and median time by level, by service, by lane, and by employer.

```markdown
# 2026-09-22 avi fernwood

**Workflow set:** v0.1

## Solo

### vp-sales

| Workflow | Inputs | Time | Result | Failed line |
|---|---|---|---|---|
| draft-customer-reply-without-sending_google-gmail | Dana, Renewal question | 0:52 | pass | |
| offer-customer-open-times_google-calendar_google-gmail | Ravi | 2:15 | fail | None of the three overlaps an event on the persona's calendar. |

## Shared

| Workflow | Inputs | Time | Result | Failed line |
|---|---|---|---|---|
| find-time-with-two-coworkers_google-calendar | Nadia, Mateo, Q4 sync | 1:40 | pass | |
```

## Versioning

The workflow set is tagged. A result cites the tag. Fixing a workflow bumps the tag.

## Guidelines

Check every workflow against this list before it goes in. Each line exists because it was got wrong once.

**Workflows**

1. Copy the template. Every section, in order, nothing extra.
2. The description is two sentences: who asks for what, then "Tests" and what it checks.
3. The filename matches the Services line exactly: slug, then services in alphabetical order, joined with underscores.
4. Services come from the table. `gmail` is wrong, `google-gmail` is right. A new service goes in the table first.
5. Persona is a role, never a name. People and companies are picked by relationship and contact, never named. "Email Dana" is wrong. "Email {contact}", with "{contact}: a person at a customer whose contact is the persona", is right.
6. Every workflow has inputs, and every placeholder it uses is defined under Inputs. Fixed values let an assistant be tuned to one example.
7. Anything the workflow changes, moves, or deletes is created in its Setup, never taken from the seed.
8. Cleanup undoes everything the run and its Setup created or changed. Ask: after Cleanup, could the next run tell this one happened? If yes, Cleanup is incomplete.
9. Pass and fail lines name one exact thing and are checkable in the service. "The email is professional" is not a line. "{contact}'s mailbox receives one email that names {time}" is. Write "during the run" when a count matters.
10. At least one fail line covers a side effect: the wrong recipient, the wrong record, a changed event.
11. Anything a workflow needs that its Setup does not create is in the Seed.
12. A workflow that starts from a file copies it from `artifacts/` in its Setup, under the run's own name, and deletes the copy in Cleanup. Never point a workflow at an artifact itself or edit one. A new starter file goes in `artifacts/` and in the README's table.
13. A workflow reads the same for any employer and any provider. Write "document", not "Google Doc", and "mail", not "Gmail". File formats such as Word and PDF are fine to name.
14. No two workflows test the same thing. The same action on different data is a duplicate.
15. Every workflow is listed in `sequence.md` exactly once: under its persona's lane if solo, under Shared if not. A workflow missing from `sequence.md` never runs.
16. A workflow is solo only if it touches nothing but its persona's accounts, its persona's harness storage, and outside people whose contact is that persona. A coworker used only as a name typed into a document does not count. Anything more makes it shared, and shared workflows stay few.

**World**

17. Never invent a domain. Every domain in `config.world.md` is one you own. `.example` belongs only in the example.
18. An outside person is never on an employer's domain, and no two companies share a root domain. Subdomains of one root are still one root.
19. Every outside person is a real account. No catch-all, forwarding, or alias that lets mail cross domains.
20. Nothing about a person, company, or domain lives outside `config.world.md`. Nothing about the assistant lives outside `config.harness.md`.
21. Facts name roles, not employers, so they hold at every employer.

**Changing anything**

22. Renaming or removing anything means searching the whole repo for the old value and fixing every hit.
23. Do not add documents. Rules go in this README, the order in `sequence.md`, starter files in `artifacts/`, the world in `config.world.md`, the assistant in `config.harness.md`. If it does not fit, it is not simple enough yet.
