# Sequence

The order every session runs in. Every workflow file is listed here exactly once.

**Solo** workflows touch only their persona's own accounts, their own assistant storage, and outside people whose contact is that persona. Each persona is a lane. Lanes run at the same time, and inside a lane workflows run one at a time, in the order listed.

**Shared** workflows touch another employee's account, or an outside person who belongs to another lane. They run one at a time, in the order listed, after every lane has finished.

## Solo

### ceo

- accept-one-reviewer-reject-another_harness-files
- add-cover-page-numbered-from-page-two_harness-files
- add-table-of-contents_harness-files
- address-comments-with-tracked-edits_harness-files
- apply-heading-styles-to-messy-document_harness-files
- comment-on-specific-phrases_harness-files
- compare-returned-copy-into-redline_harness-files
- create-formatted-memo_harness-files
- create-lists-and-repeating-table_harness-files
- export-a4-pdf-from-letter-document_harness-files
- export-archival-pdf-a_harness-files
- export-clean-pdf-from-tracked-changes_harness-files
- export-one-section-to-pdf_harness-files
- export-pdf-with-bookmarks-and-links_harness-files
- export-to-pdf-matching-layout_harness-files
- fill-template-keeping-formatting_harness-files
- make-clean-final-copy_harness-files
- make-one-page-landscape_harness-files
- redline-contract_harness-files
- reply-to-comment-and-edit-own_harness-files
- resolve-and-delete-comments_harness-files
- revise-pending-suggestion_harness-files
- update-document-and-its-pdf_harness-files

### vp-sales

- draft-customer-reply-without-sending_google-gmail
- label-and-archive-company-threads_google-gmail
- offer-customer-open-times_google-calendar_google-gmail
- reply-to-customer-question-from-facts_google-gmail
- reschedule-customer-meeting_google-calendar
- send-customer-document_google-drive_google-gmail
- update-contact-title-from-email_google-contacts_google-gmail

### cpo

- invite-vendor-to-call_google-calendar
- rename-and-file-document_google-drive
- save-vendor-attachment_google-drive_google-gmail
- undo-file-delete_harness-files

### hr

- set-out-of-office_google-calendar
- write-job-description_google-drive

### software-engineer

- create-weekly-focus-block_google-calendar
- skip-one-meeting-in-series_google-calendar

## Shared

- add-coworker-to-meeting_google-calendar
- add-email-sender-to-contacts_google-contacts_google-gmail
- confirm-tomorrows-outside-meetings_google-calendar_google-gmail
- decline-meeting-invitation_google-calendar
- find-time-with-two-coworkers_google-calendar
- forward-customer-email-to-coworker_google-gmail
- onboard-newest-hire_google-calendar_google-drive_google-gmail
- reply-only-to-sender_google-gmail
