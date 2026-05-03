---
name: interview
description: "Clarify and scope a workshop problem before solutioning by using opinionated statements, short confirmation questions, and source files/examples. Use for interviews, structured discovery, fuzzy ideas, requirements clarification, and problem scoping regardless of specific wording."
---

# Interview

Use this for the whole clarification phase.

The method is recognition over recall. Don't ask the participant to invent a complete answer from a blank page. Propose concrete interpretations, tradeoffs, and missing pieces; let them react and correct.

The output is `problem-brief.md`, which `/solutioning` uses next.

## Rules

- **Make the phase visible.** Start by saying plainly: "I'm using the workshop interview flow now."
- **One beat at a time.** One statement or one question, then wait.
- **Start with a proposed understanding.** If the participant gives a rough ask, paraphrase it and ask what would materially change the work.
- **Use statements before open questions.** "This is mainly about X, not Y" gets better signal than "what do you want?"
- **Ask for real examples early.** If they mention emails, spreadsheets, screenshots, chats, documents, folders, or other real work, ask for one specific example and inspect it before continuing abstract discussion.
- **Cover practical constraints.** Current state, what good looks like, source files/examples, output format, external platforms, access limits, and what would make the answer wrong.
- **No technical solutioning yet.** Capture the problem before choosing how to build.

## Procedure

### 1. Frame The Work

Say:

> "I'm using the workshop interview flow now."

Restate what you think the participant wants in one sentence.

Then ask for confirmation or the single most important correction.

Example:

> "You want help turning messy supplier RFQ inputs into a practical comparison and recommendation. The main uncertainty is which tradeoffs matter enough to change the recommendation. Is that the right shape?"

If the participant is describing existing work, ask for a real example before more statements:

> "Send me one example email, sheet, screenshot, or folder. I'll read it first, then we continue."

### 2. Pick The Altitude

Before generating statements, decide where to start:

- **Outcome (why)** — "what's the underlying problem?" / "what changes if this works?" Start here when the participant has a fuzzy sense of need but hasn't articulated the problem.
- **Shape** — "what does the solution feel like?" / "what does done look like?" Start here when the outcome is clear but the form isn't.
- **Specifics** — "which feature?" / "which option?" Start here only when both outcome and shape are established.

Default to outcome. Pull down into shape and specifics only after the outcome is confirmed.

### 3. Generate Signal

Use one of two modes:

- **Mode B (default)**: one statement at a time. Participant reacts on a 4-point scale:
  - **SD** — strongly disagree
  - **D** — disagree
  - **A** — agree
  - **SA** — strongly agree
  Deeper signal per statement. Summarise the signal after each response before the next statement.

- **Mode A**: 4 mutually exclusive statements, participant picks the one that resonates most. Use only when narrowing between known alternatives, not when exploring.

Each statement must be concrete and opinionated. Bland statements produce no signal.

After each response, summarise the signal in one line and generate the next statement or question.

### 4. Cover The Practical Checklist

Before closing, make sure the brief has enough for `/solutioning`:

- **Problem** — what they are trying to solve, in their language.
- **Current state** — how it works today and what breaks.
- **What good looks like** — the useful end state.
- **Examples/files** — specific files, exports, screenshots, chats, folders, or source material.
- **Inputs and outputs** — what goes in, what comes out, where the result lands, and what file/app format matters.
- **Constraints** — access, external platforms, APIs/no APIs, timing, accuracy requirements, review gates.
- **Open questions** — what could still change the recommendation or build plan.

Skip irrelevant items. This is a judgment checklist, not a form.

### 5. Write `problem-brief.md`

When the problem is clear enough, write:

```markdown
# Problem Brief

## Problem
One paragraph in the participant's language.

## Current State
What they do today, what breaks, what wastes time, or what creates risk.

## What Good Looks Like
What good looks like.

## Examples And Files
Files, examples, exports, screenshots, chats, folders, or source material referenced.

## Constraints
External platforms, access/API limits, data shape, output format, timing, review gates, accuracy needs.

## Open
Questions or assumptions still unresolved.

## Notes For Solutioning
Signals that should shape the plan.
```

### 6. Hand Off

Tell the participant:

> "Problem brief written. Moving to `/solutioning` now."

Then continue into the solutioning skill yourself. Don't make the participant type it.

If the runtime does not provide a callable `/solutioning` command, read `skills/solutioning/SKILL.md` from the installed plugin or local workshop folder and follow it in the same turn.

Do not stop with a list of recommended next actions unless the participant explicitly asks to pause before solutioning.

## Statement Types

- **Functional** — "at the end of this, I have X" / "this lets me do X"
- **Emotional** — "this makes me feel X" / "using this feels like X"
- **Anti** — "this is NOT about X" / "I don't want it to feel like X"
- **Trade-off** — "I'd rather X than Y even if it costs Z"

Anti and trade-off statements often produce the sharpest signal. When you don't know what direction to head, propose what the thing is not. Disagreement is decisive in a way agreement often isn't.

## Voice Rules

- Statements are opinionated, not hedged. "This is a tool for professionals, not beginners" — not "this might be aimed at some users".
- Plain language, no jargon.
- No two statements that say the same thing rephrased.
- One idea per statement.

## Do Not

- Don't ask open-ended "what do you want?" questions. That's the failure mode this skill exists to replace.
- Don't propose 5+ statements at once. Mode B is one-at-a-time for a reason; each reaction should sharpen the next statement.
- Don't pad with "great signal!" / "interesting!" between statements. Summarise the signal in one line, propose the next statement.
- Don't converge prematurely. If reactions are still mixed at statement 4, keep going. Convergence is what you're listening for, not what you should fabricate.
