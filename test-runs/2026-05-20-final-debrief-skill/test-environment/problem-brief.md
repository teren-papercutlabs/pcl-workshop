# Problem Brief

## Problem
Maya is the finance and operations lead for a small food importer. Every Monday she has to brief the founder on cash pressure: which invoices are late, which supplier payments are due, and whether there is enough cash buffer for the next two weeks. Today this is assembled manually from three exports and a lot of checking in chat.

## Current State
Maya opens the bank export, the receivables ageing sheet, and the supplier payment tracker. She copies the important rows into a note, rewrites it in plain English, and then sends it to the founder. The slow part is not writing the note; it is deciding what is actually worth escalating and making sure she did not miss one invoice or payment.

## What Good Looks Like
Claude produces a first draft of the Monday cash watch note from the three files. The note should call out risk, explain what changed from last week, and end with a short "what to decide" section. Maya still checks the numbers before sending.

## Examples And Files
- `inputs/bank-export.csv`
- `inputs/ar-aging.csv`
- `inputs/supplier-payments.csv`
- `outputs/cash-watch-note.md`

## Constraints
No bank API access. Maya will download CSVs manually. The output must be a short Markdown note she can paste into email or WhatsApp. Amounts must be checked before sending.

## Open
The workshop did not confirm whether the source exports always use the same column names.

## Notes For Solutioning
Maya is comfortable reviewing a draft. She is less confident when Claude asks for file paths or when a CSV looks different from the example.
