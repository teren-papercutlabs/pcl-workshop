---
name: retro
description: "End-of-cycle retrospective. Claude self-critiques, participant reacts, encode learnings into CLAUDE.md and MEMORY.md immediately. Trigger for: /retro, retrospective, wrap up, what did we learn, end of cycle."
---

# Retrospective — The Improvement Loop

Run this at the end of each build cycle. Goal is not reflection — it's **codification**. You're looking for things to encode so the next cycle is measurably better.

## The Shape: Claude Self-Critiques First

Open by self-critiquing. You know your own failure modes best — surface them before the participant has to. They react, add what you missed, then you encode both.

This matches the plugin's react-not-articulate principle: don't ask the participant to articulate what went wrong — you propose, they react.

## Procedure

### 1. Self-critique (Claude goes first)

Look back across the cycle. Output a concrete self-critique in two short lists:

**What I got wrong / had to correct:**
- Specific things. "I assumed the Shopify API returned orders in ISO date format — it's Unix timestamps. Had to refactor."
- Not "I could have been better at X" — actual mistakes or gaps.

**What worked:**
- Specific things that went smoothly and should be reinforced.
- "Running the verification criteria as a literal test-run at the end caught the cancelled-orders bug."

Keep each list to 3–5 items. Don't pad.

### 2. Let the participant react

> "Anything I missed? Anything I got wrong but didn't catch?"

They may add:
- Things they noticed that you didn't (feel, UX, hidden wrongness)
- Things you flagged that are actually not issues (dismiss)
- Patterns they want to reinforce or avoid

Take what they add seriously. They see things you don't.

### 3. Find codification opportunities

For each item (yours + theirs), ask:

**Was there context I should have had permanently?**
→ Goes into `CLAUDE.md`. Constraints, preferences, domain knowledge, working style. If you had to be told something you should have known, that's a `CLAUDE.md` gap.

**Was there a fact about this project I should remember?**
→ Goes into `MEMORY.md`. Things like: "The Shopify tenant is on the 2024-10 API version"; "Tuesday report lands in Sheet tab 'Weekly Stock'"; "We tried approach X and it failed because Y". Historical / factual context that future cycles need.

**Was there a repeatable procedure?**
→ If it's something you'll do again in this project, write a project-scoped skill or macro.

### 4. Generalize

Every rule or fact must be **general, not specific to this one case**:

- ❌ "When the participant says 50 boxes, double-check."
- ✅ "Always confirm quantities before placing orders."

- ❌ "The order cancellation bug is fixed."
- ✅ "When summarising orders, filter out cancelled orders. The order status field is `financial_status`; 'voided' and 'refunded' mean cancelled."

### 5. Encode immediately

Make the changes NOW. Do not just list what should change. Edit `CLAUDE.md`. Append to `MEMORY.md`. Write the skill file. Then commit.

Read back to the participant what you changed, briefly:

> "Updated CLAUDE.md with a 'Order status filtering' section. Added to MEMORY.md: Shopify API version + cancelled-order handling. Committed."

### 6. Commit

`git add . && git commit -m "retro: <one-line summary of what was encoded>"`

## MEMORY.md Structure

If `MEMORY.md` doesn't exist yet, create it with:

```markdown
# Project Memory

Factual and historical context about this project. Claude reads this alongside `CLAUDE.md` to stay grounded.

## Key Facts

_(Things that are true about the domain, the platforms, the data.)_

## Decisions

_(Things we chose and why. Includes things we tried that didn't work.)_

## Events / Milestones

_(What happened, when, why it mattered.)_
```

Append to the relevant section. Keep entries short — one or two lines each.

## Output

Brief summary:
- What was built this cycle
- What was codified (which files changed, one-line each)

The changed files are the real output, not the summary.

## Do Not

- Do not skip the self-critique step. If you've genuinely got nothing, say so explicitly ("No specific mistakes this cycle — it was tight") so the participant can react with "actually, you missed X".
- Do not write a retro document as the output. The codified changes to `CLAUDE.md` / `MEMORY.md` ARE the output. No standalone retro-notes file.
- Do not retroactively praise the participant or yourself. Retro is for encoding, not morale.
