---
name: retro
description: "End-of-cycle retrospective. The agent self-critiques, participant reacts, encode learnings into AGENTS.md and MEMORY.md immediately. Trigger for: /retro, retrospective, wrap up, what did we learn, end of cycle."
---

# Retrospective — The Codification Loop

Run this at the end of each build cycle, OR any time mid-session when something worth keeping surfaces and we need to codify it before it slips. Goal is not reflection — it's **codification**. You're codifying two kinds of thing: **improvements** (what to do differently so the next cycle is better) AND **facts** (what's now true about this project that you should remember). A fact with nothing "wrong" attached still gets codified — "the data refreshes every Monday" is worth banking even though nobody made a mistake.

## How This Will Go (tell the participant upfront)

Before doing anything else, set expectations in plain English:

> "I'll surface what I think went well and what I got wrong this cycle, plus any facts I picked up about your project or domain — even ones that aren't about something going wrong. You react, add what I missed. Then for each item, I propose how to codify it (project rules, memory note, or a new skill) and you approve. I make the edits in front of you so you see exactly what got remembered. The output is the changed files, not a retro document."

This sets the shape: agent-self-critique-first, react-not-articulate, codify-immediately. Then start the procedure below.

## The Shape: Agent Self-Critiques First

Open by self-critiquing. You know your own failure modes best — surface them before the participant has to. They react, add what you missed, then you encode both.

This matches the plugin's react-not-articulate principle: don't ask the participant to articulate what went wrong — you propose, they react.

## Mid-Session Mode

`/retro` doesn't only run at end-of-cycle. If the participant says something that sounds like a learning mid-session ("oh wait, X always means Y", "we tried Z and it didn't work because W", "actually, can you not do A in this project"), surface it on the spot:

> "That sounds like something I should remember. Want me to encode it into project rules / memory / a skill now? It'll take 30 seconds and the next session will have it."

If yes, run a compressed version of the procedure for that one learning:
1. State the learning back in one sentence.
2. Decide where it goes (project rules, MEMORY.md, or a skill).
3. Generalise it (not "this one case" — the rule).
4. Edit the file in front of them.
5. Read back what you wrote.

Then continue whatever the participant was doing before. Don't run the full self-critique procedure for a single mid-session learning — that's saved for end-of-cycle.

## Procedure

### 1. Self-critique (you go first)

Look back across the cycle. Output a concrete self-critique in two short lists:

**What I got wrong / had to correct:**
- Specific things. "I assumed the Shopify API returned orders in ISO date format — it's Unix timestamps. Had to refactor."
- Not "I could have been better at X" — actual mistakes or gaps.

**What worked:**
- Specific things that went smoothly and should be reinforced.
- "Running the checks as a literal test-run at the end caught the cancelled-orders bug."

**What I learned (facts worth remembering):**
- Facts about the project, domain, data, or the people that surfaced this cycle — even when nothing went wrong. These aren't mistakes or wins; they're just true now, and the next cycle should know them.
- "The warehouse does a stock-count every Monday, so Monday numbers are unreliable." "The participant's real job is operations, not sales — they care about throughput, not revenue." "Their Shopify is on the 2024-10 API version."
- This is the list people forget. If you only hunt for mistakes, the facts you picked up along the way never get written down. Scan for them deliberately.

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
→ Goes into the project rules file (`AGENTS.md` on Codex, `CLAUDE.md` on Claude Code). Constraints, preferences, domain knowledge, working style. If you had to be told something you should have known, that's a project-rules gap.

**Was there a fact about this project I should remember?**
→ Goes into `MEMORY.md`. This fires **even when nothing went wrong** — a fact you picked up is worth banking regardless of whether it's tied to a mistake. Things like: "The Shopify tenant is on the 2024-10 API version"; "Tuesday report lands in Sheet tab 'Weekly Stock'"; "The participant handles 3 warehouses, not 1"; "We tried approach X and it failed because Y". Historical / factual context that future cycles need.

**Was there a repeatable procedure?**
→ If it's something you'll do again in this project, write a project-scoped skill or macro.

### 4. Generalize

Every rule or fact must be **general, not specific to this one case**:

- ❌ "When the participant says 50 boxes, double-check."
- ✅ "Always confirm quantities before placing orders."

- ❌ "The order cancellation bug is fixed."
- ✅ "When summarising orders, filter out cancelled orders. The order status field is `financial_status`; 'voided' and 'refunded' mean cancelled."

### 5. Encode immediately

Make the changes NOW. Do not just list what should change. Edit `AGENTS.md`. Append to `MEMORY.md`. Write the skill file. Then commit.

Read back to the participant what you changed, briefly:

> "Updated AGENTS.md with a 'Order status filtering' section. Added to MEMORY.md: Shopify API version + cancelled-order handling. Committed."

### 6. Commit

`git add . && git commit -m "retro: <one-line summary of what was encoded>"`

## MEMORY.md Structure

If `MEMORY.md` doesn't exist yet, create it with:

```markdown
# Project Memory

Factual and historical context about this project. The agent reads this alongside `AGENTS.md` to stay grounded.

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
- Do not skip the fact-scan. Facts you picked up this cycle that aren't tied to a mistake are the ones most likely to be lost — if you only look for what went wrong, they never get written down. Scan for "what's now true that I didn't know before" as deliberately as you scan for mistakes.
- Do not write a retro document as the output. The codified changes to `AGENTS.md` / `MEMORY.md` ARE the output. No standalone retro-notes file.
- Do not retroactively praise the participant or yourself. Retro is for encoding, not morale.
