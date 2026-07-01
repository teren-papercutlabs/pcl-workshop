---
name: retro
description: "End-of-cycle retrospective. The agent self-critiques, participant reacts, and future-useful learnings are encoded into CLAUDE.md immediately. Trigger for: /retro, retrospective, wrap up, what did we learn, end of cycle."
---

# Retrospective — The Codification Loop

Run this at the end of each build cycle, or any time mid-session when something worth keeping surfaces and we need to capture it before it slips.

Goal is not a retro document. Goal is codification: improve the next cycle by writing what should be remembered into `CLAUDE.md`.

You are codifying two kinds of things:

- **Improvements** — what to do differently so the next cycle is better.
- **Facts** — what is now true about the participant's business, workflow, data, preferences, or constraints.

A fact with nothing "wrong" attached still gets codified. "The data refreshes every Monday" is worth remembering even if nobody made a mistake.

## How This Will Go (tell the participant upfront)

Before doing anything else, tell the participant what you are about to do:

> "I'm going to do the workshop retro now. First I'll reflect back what happened and capture your point of view — what worked, what felt wrong, and what facts about your work I should remember. Then we'll walk through the concrete changes to `CLAUDE.md` so future sessions pick them up. The output is the updated workshop memory, not a separate retro document."

Then start the procedure below.

## The Shape: Agent Self-Critiques First

Open by self-critiquing. You know your own failure modes best — surface them before the participant has to. They react, add what you missed, then you encode both.

This matches the react-not-articulate principle: do not ask the participant to invent feedback from a blank page. You propose; they react.

## Mid-Session Mode

`/retro` does not only run at end-of-cycle. If the participant says something that sounds like a learning mid-session — "oh wait, X always means Y", "we tried Z and it didn't work because W", "actually, can you not do A in this project" — surface it on the spot:

> "That sounds worth remembering for next time. I'll add it to `CLAUDE.md` unless you want it kept out."

If they agree, run a compressed version for that one learning:

1. State the learning back in one sentence.
2. Choose the right section of `CLAUDE.md`.
3. Generalise it so it helps future sessions.
4. Edit `CLAUDE.md` in front of them.
5. Read back what you wrote.

Then continue whatever the participant was doing before. Do not run the full self-critique procedure for a single mid-session learning — that is saved for end-of-cycle.

## Procedure

### 1. Self-critique (you go first)

Look back across the cycle. Output a concrete self-critique in three short lists.

**What I got wrong / had to correct:**

- Specific things. Example: "I assumed the export had one row per order, but it had one row per item. I had to adjust the summary."
- Not vague self-improvement language.

**What worked:**

- Specific things that went smoothly and should be reinforced.
- Example: "Running the checks on the real spreadsheet caught the missing cancelled-order rule."

**What I learned about your work:**

- Facts about the business, process, files, timing, preferences, people, or constraints.
- Example: "The Tuesday report is for the ops lead, not finance, so the summary needs to focus on blockers, not accounting detail."

Keep each list to 3–5 items. Do not pad.

### 2. Let the participant react

Ask:

> "What did I miss or get wrong in that read?"

They may add:

- Things they noticed that you did not.
- Things you flagged that are not actually issues.
- Patterns they want to reinforce or avoid.
- Business context they want future sessions to remember.

Take what they add seriously. They see things you do not.

### 3. Find codification opportunities

For each item, decide where it belongs inside `CLAUDE.md`:

- **Participant Context** — role, team, tools, files, constraints, review rules.
- **Business Facts To Remember** — facts about the domain, workflow, data, timing, or people.
- **Decisions And Things Tried** — choices made, tradeoffs, failed approaches, and why.
- **Preferences And Working Style** — output style, review style, wording, pacing, examples.
- **Reusable Workflow Notes** — repeated steps, templates, folder names, skill names, or file locations.

If the learning is a repeatable procedure that deserves its own command, write or update a skill and record the skill name in `CLAUDE.md`.

### 4. Generalise

Every rule or fact must be useful beyond this exact moment:

- Bad: "When the participant says 50 boxes, double-check."
- Good: "Always confirm quantities before placing orders."

- Bad: "The cancelled-order bug is fixed."
- Good: "When summarising orders, exclude cancelled orders and show the rule used."

### 5. Encode immediately

Make the changes now. Do not list what should change later.

Edit `CLAUDE.md`. If a skill needs to change, edit the skill too. Then read back the change briefly:

> "Updated `CLAUDE.md` with the order-status rule and the Tuesday report audience. Future sessions will see those before building."

### 6. Close

Briefly summarise:

- What was built this cycle.
- What was written into `CLAUDE.md`.
- Any skill or reusable workflow note changed.

## Output

The changed files are the real output. Do not create a standalone retro-notes file.

## Do Not

- Do not skip the self-critique step. If you genuinely have no specific mistakes, say so plainly so the participant can correct you.
- Do not skip the fact scan. Facts that are not tied to a mistake are the easiest to lose.
- Do not write a retro document as the output.
- Do not create a separate memory file. Business context and future-session memory live in `CLAUDE.md`.
- Do not retroactively praise the participant or yourself. Retro is for encoding, not morale.
- Do not mention Git or commits unless the participant explicitly asks for version control.
