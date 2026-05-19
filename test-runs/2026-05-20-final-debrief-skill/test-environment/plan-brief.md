# Plan Brief

## Problem Recap
Maya needs a repeatable way to turn weekly cash exports into a short cash watch note for the founder without rebuilding the note from scratch every Monday.

## Approach
Build a Claude Code skill called `/cash-watch-note`. Maya will put the three exports in `inputs/`, run the skill, and Claude will read the files, compare the numbers, and write `outputs/cash-watch-note.md`. The skill should remind Claude to show the key numbers it used so Maya can check them before sending.

## Deliverable Shape
A reusable skill plus a small output template. This fits the work because Maya already downloads the files manually and needs help turning them into judgment and wording, not a new finance system.

## Output Format
Markdown note in `outputs/cash-watch-note.md`.

## Key Steps
1. Read the three input files.
2. Pull out overdue invoices, upcoming supplier payments, and current cash balance.
3. Draft the note in founder-friendly language.
4. Show the numbers used for review.
5. Save the final draft to `outputs/cash-watch-note.md`.

## Tools Involved
- Local CSV files.
- Claude Code file reading and writing.
- No bank or accounting API.

## Techniques Referenced
- `techniques/no-api-workflows.md` because the bank and accounting system exports are manual.
- `techniques/accuracy.md` because finance numbers must be checked before sending.

## Checks
1. When the three CSVs are present in `inputs/`, Claude writes `outputs/cash-watch-note.md`.
2. When an invoice is overdue by more than 30 days, the note highlights it.
3. When a supplier payment is due within 14 days, the note includes it.
4. When a file is missing, Claude stops and asks for it instead of guessing.
5. Before Maya sends the note, Claude shows the key numbers used.
