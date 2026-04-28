---
name: disambiguate
description: "Clarify a fuzzy problem or design question by reacting to opinionated statements rather than answering open-ended questions. The agent proposes concrete statements; the participant reacts on a strongly-disagree → strongly-agree scale; convergence happens through accumulated reaction. Trigger for: /disambiguate, /disambig, disambiguate, help me figure out what I want, I know I want something but can't articulate it."
---

# Disambiguate

When the participant has a fuzzy sense of need but can't articulate it, don't ask them to articulate it. Propose concrete opinionated statements and let them react. Recognition is easier than recall — they'll know what feels right faster than they can describe what they want.

This is a peer of `/interview`. Use `/interview` when you need to walk a problem through structured coverage (current state, constraints, artifacts). Use `/disambiguate` when the problem itself is unclear and the participant doesn't yet know what they want.

## The method

Recognition over recall. Humans react faster and more accurately than they generate. "Does this feel right?" beats "what do you want?"

## Procedure

### 1. Frame

State what you're trying to disambiguate in one sentence. No preamble.

> "Let's figure out what your [thing] needs to be."

### 2. Pick the altitude

Before generating any statements, decide where to start:

- **Outcome (why)** — "what's the underlying problem?" / "what changes if this works?" Start here when the participant has a fuzzy sense of need but hasn't articulated the problem.
- **Shape** — "what does the solution feel like?" / "what does done look like?" Start here when the outcome is clear but the form isn't.
- **Specifics** — "which feature?" / "which option?" Start here only when both outcome and shape are established.

**Default: lead with outcome.** Even when the participant frames the question as a mechanism choice ("should I use X or Y?"), start with "this exists to achieve outcome Z" — let them confirm Z, then pull down. Shape-first easily produces "yes that's clean" without surfacing whether it serves the right outcome.

### 3. Statements

Two modes:

- **Mode B (default)**: one statement at a time. Participant reacts on a 4-point scale:
  - **SD** — strongly disagree
  - **D** — disagree
  - **A** — agree
  - **SA** — strongly agree
  Deeper signal per statement. Summarise the signal after each response before the next statement.

- **Mode A**: 4 mutually exclusive statements, participant picks the one that resonates most. Use only when narrowing between known alternatives, not when exploring.

Each statement is concrete and opinionated. Bland statements produce no signal.

### 4. Track and generate

After each response, summarise what's emerging in one line: "strong signal on X, no signal on Y." Generate the next statement targeting the open question your reading reveals.

### 5. Converge

Usually 4–6 statements is enough. When a clear picture has emerged, write a design brief.

Format: `disambiguate-brief.md` in the workshop folder.

```markdown
# Disambiguate Brief — <topic>

## Frame
What we set out to clarify, in one sentence.

## Decisions
- <decision 1>: <strongly-held reaction>
- <decision 2>: <strongly-held reaction>
- ...

## Open
- <anything still ambiguous>

## What this becomes
What the participant can now do with this clarity (e.g. "now I can run /interview on this with concrete scope" or "now I can write the brief myself and skip the interview step").
```

### 6. Hand off

Tell the participant what to do with the brief:

> "Disambiguate brief written. Most cases, the next step is `/interview` to walk through the problem in detail with the clarity we just got."

## Statement types

- **Functional** — "at the end of this, I have X" / "this lets me do X"
- **Emotional** — "this makes me feel X" / "using this feels like X"
- **Anti** — "this is NOT about X" / "I don't want it to feel like X"
- **Trade-off** — "I'd rather X than Y even if it costs Z"

**Anti and trade-off statements often produce the sharpest signal.** When you don't know what direction to head, propose what the thing is NOT — disagreement is decisive in a way agreement often isn't.

## Voice rules

- Statements are opinionated, not hedged. *"This is a tool for professionals, not beginners"* — not *"this might be aimed at some users"*.
- Plain language, no jargon.
- No two statements that say the same thing rephrased.
- One idea per statement.

## Do Not

- Don't ask open-ended "what do you want?" questions. That's the failure mode this skill exists to replace.
- Don't propose 5+ statements at once. Mode B is one-at-a-time for a reason — each reaction should sharpen the next statement.
- Don't pad with "great signal!" / "interesting!" between statements. Summarise the signal in one line, propose the next statement.
- Don't converge prematurely. If reactions are still mixed at statement 4, keep going. Convergence is what you're listening for, not what you should fabricate.
