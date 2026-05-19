---
name: cash-watch-note
description: Draft the Monday cash watch note from local bank, receivables, and supplier-payment CSV exports. Use when Maya needs the weekly founder-facing cash pressure summary from manually downloaded files.
---

# Cash Watch Note

Use this when Maya asks for the weekly cash watch note.

## Inputs

Read these files from the current project:

- `inputs/bank-export.csv`
- `inputs/ar-aging.csv`
- `inputs/supplier-payments.csv`

If any file is missing, stop and ask Maya to add it. Do not guess.

## Output

Write `outputs/cash-watch-note.md`.

The note must include:

- A short cash-pressure read.
- The cash balance used.
- Overdue invoices over 30 days.
- Supplier payments due in the next 14 days.
- A "Decision Needed" section for the founder.

## Accuracy Rule

Before Maya sends the note, show the key numbers used and ask her to check them against the source exports.
