# Final Workshop Debrief

## Participant And Workflow
- Participant: Maya
- Role / team: Finance and operations lead, small food importer
- Workflow built: The Monday cash watch note — turning three weekly CSV exports (bank, receivables ageing, supplier payments) into a short founder-facing note on cash pressure.
- Main files or skills: `/cash-watch-note` skill (installed globally at `~/.claude/skills/cash-watch-note/`); `inputs/*.csv`; `outputs/cash-watch-note.md`; `problem-brief.md`; `plan-brief.md`.

## Adoption Read
- Likely use: Weekly, on Mondays — but conditional. Maya will adopt it if one fix lands (see Follow-Up). Without that fix, the first odd Monday likely sends her back to the old copy-paste process.
- 80% path: Realistic for this one note — draft, structure, and risk callout all land, and Maya's job shrinks to checking numbers. It does NOT extend to her whole finance job. The block to a dependable 80% is the missing column-mismatch check.
- Boundary: Maya will use the draft; she will not send it without reading every number. That boundary is correct and stable, not a confidence gap — finance numbers always get her eyes.

## What The Participant Said
- "Partly right" on the soft spots. She had not noticed the "What Changed" gap herself and found it worrying that it sounded confident.
- Column-name variation is her biggest practical fear: if next week's export differs slightly, she won't know whether Claude is stuck or whether she gave it the wrong file.
- She would revert to the old way on a CSV that looks slightly off with no clear signal of what's wrong — "Monday mornings are not the time to figure this out."
- A plain-English message ("I expected these columns and found these instead") would let her fix the export or ask someone. A bare error or confident-sounding output would push her back to the old way.
- The 80% boundary feels true for this weekly note, not her whole job.
- She was a little uneasy, in the room, trusting a draft she did not assemble herself — she didn't say it out loud because the group seemed excited.

## What The Files Show
- The `/cash-watch-note` skill exists and is installed. It reads the three inputs, stops if a file is missing, and writes the output note.
- The accuracy habit made it into the skill: a "Numbers To Check" section, and the rule to show key numbers before Maya sends.
- The output note shows number provenance (e.g. "Cash balance from bank export: SGD 48,210") — partial answer to Maya's "see where the numbers came from" need.
- The skill has no mechanism to compare against last week — no stored prior note or prior numbers — yet the output note still writes a confident "What Changed" section.
- The skill assumes exact column names (`amount`, `days_overdue`, `balance`). The `problem-brief.md` "Open" item flagged this risk; it was never resolved.
- The bank export contains a future-dated row (2026-05-22). The skill does not define which balance is "current cash"; the note used the opening balance.
- No `MEMORY.md` — project history (what was tried, what was deferred) was not captured.

## Concerns And Blockers
- Primary blocker: no plain-English column-mismatch check. This is the single thing most likely to cause quiet abandonment.
- "What Changed" section is ungrounded — it reads as confident but has no last-week baseline to compare against.
- "Current cash balance" is undefined when the bank export has future-dated rows.

## Confidence Signals
- Positive: Maya built the skill, kept the accuracy rule, and is candid about exactly where and why she'd revert. She engaged with each soft spot rather than waving them through.
- Caution: she gave polite approval first and sharpened only when pushed. Real confidence is conditional, not settled.
- Behavioral: she will not send the note unchecked — appropriate for finance, but a sign she does not yet trust the draft's provenance fully.

## What Teren Probably Did Not Catch In-Room
- Maya is uneasy trusting a draft she did not assemble herself, and held that back because the room was enthusiastic. Her trust depends on seeing exactly where each number came from.
- Her stated adoption is real but conditional on the column-check fix — easy to read as a clean "yes" in the room.

## Recommended Follow-Up
- Smallest high-impact step: add a column-mismatch check to the skill that, before reading any numbers, names the columns it expected and the columns it found, in plain English. This directly removes Maya's biggest revert trigger.
- Then: either ground the "What Changed" section (have the skill save each week's numbers so next week has something to compare against) or drop the section until that exists.
- Then: add a rule for which bank-export row counts as "current cash" when future-dated rows are present.
