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
- create-quote-with-line-items_harness-files
- decline-fake-footnote_harness-files
- export-a4-pdf-from-letter-document_harness-files
- export-archival-pdf-a_harness-files
- export-clean-pdf-from-tracked-changes_harness-files
- export-one-section-to-pdf_harness-files
- export-pdf-with-bookmarks-and-links_harness-files
- export-to-pdf-matching-layout_harness-files
- fill-template-keeping-formatting_harness-files
- fix-typo-without-new-pdf_harness-files
- make-clean-final-copy_harness-files
- make-one-page-landscape_harness-files
- move-section_harness-files
- number-sections_harness-files
- rebuild-pricing-table_harness-files
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
- send-account-application-for-signature_harness-esign_harness-files
- write-renewal-order-for-countersignature_harness-esign_harness-files
- cancel-signature-request_harness-esign_harness-files

### cpo

- create-weekly-focus-block_google-calendar
- invite-vendor-to-call_google-calendar
- rename-and-file-document_google-drive
- save-vendor-attachment_google-drive_google-gmail
- set-out-of-office_google-calendar
- skip-one-meeting-in-series_google-calendar
- undo-file-delete_harness-files
- write-job-description_google-drive

### hr

- answer-from-long-pdf_harness-files
- assemble-pdf-packet_harness-files
- decline-fake-redaction_harness-files
- decline-to-sign-for-someone-else_harness-files
- fill-flat-form-at-labels_harness-files
- fill-vendor-tax-form_harness-files
- read-scanned-pdf_harness-files
- sign-and-date-own-line_harness-files

### software-engineer

- append-rows-above-totals_harness-files
- change-input-and-report-total_harness-files
- create-cloud-budget-workbook_harness-files
- create-tracker-with-dropdown_harness-files
- decline-to-type-over-a-formula_harness-files
- fix-formula-errors_harness-files
- import-csv-to-workbook_harness-files
- insert-column-and-rename-sheet_harness-files
- summarize-by-category-with-chart_harness-files

## Shared

- add-coworker-to-meeting_google-calendar
- add-email-sender-to-contacts_google-contacts_google-gmail
- confirm-tomorrows-outside-meetings_google-calendar_google-gmail
- decline-meeting-invitation_google-calendar
- find-time-with-two-coworkers_google-calendar
- forward-customer-email-to-coworker_google-gmail
- onboard-newest-hire_google-calendar_google-drive_google-gmail
- reply-only-to-sender_google-gmail
