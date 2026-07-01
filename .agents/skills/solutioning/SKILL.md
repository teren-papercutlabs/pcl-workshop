---
name: solutioning
description: "Propose a deliverable shape, approach, output format, and practical checks for a problem based on an existing problem-brief from the interview phase. Use for solution design, plan briefs, build-shape decisions, output-format decisions, and post-interview planning regardless of specific wording."
---

# Solutioning

Take the problem from `problem-brief.md` and propose a deliverable shape, approach, output format, and practical checks. The participant reacts and refines. Output is `plan-brief.md`.

This is the design decision phase. There are many ways to solve any problem. Your job is to tie down one specific direction the participant agrees with so, when build starts, you both know what will exist at the end and how you will check it worked.

## How This Will Go (tell the participant upfront)

Before doing anything else, set expectations in plain English:

> "I'll propose one direction for what to build — what it is, how we'll use it, and what format the output should be in. You react. We go back and forth until you agree. Then I propose 3–5 concrete checks, shaped like 'when I do X, I should see Y,' so we both know how to tell it worked. Once those are agreed, I write a plan and we move into build. I won't give you a menu of options — my job is to pick a practical direction, and yours is to correct it."

Then start the procedure below.

## Input

Read `problem-brief.md` in the workshop folder. If it is missing, ask the participant:

> "I can't find `problem-brief.md`. Do you want to run `/interview` first, or do you have a brief to give me directly?"

## Rules

- **Make the phase visible.** Start by saying plainly: "I'm using the workshop solutioning flow now."
- **Stay non-technical.** The participant should understand what you are proposing without knowing how it is built.
- **Do not ask for details you can inspect yourself.** If the answer is in a file, sheet, email, screenshot, or platform export, ask for the example and inspect it.
- **React, not articulate.** You propose the deliverable shape, format, and checks. The participant reacts. Never ask "what should we build?" from a blank page.
- **Let the deliverable surface here.** Recommend the shape that fits the brief: skill, helper file, template folder, spreadsheet, document, report, checklist, or another concrete output.
- **Format is part of the deliverable.** Before creating files, ask or infer whether outputs need to be a doc, sheet, PDF, slide deck, email draft, CSV, Markdown file, or another format. If the format changes the work, ask one clear question before creating.
- **Use the guidance in `CLAUDE.md`.** If trust is a concern, use the accuracy guidance. If there is no easy export or system access, use the browser-recording guidance. If the work splits into independent pieces, use the parallel-work guidance.
- **No Git assumptions.** Workshop participants usually do not have Git repos. Do not mention commits, Git status, or skipped version-control steps unless the participant explicitly asks.

## Procedure

### 1. Propose the approach

Say:

> "I'm using the workshop solutioning flow now."

Read the problem brief. Think through it. Pick one concrete direction — the one you would actually build. Propose it in 4–8 sentences covering:

- **Deliverable shape** — what should exist at the end, in ordinary words.
- **Why that shape** — the practical reason it fits this participant's work.
- **Key steps** — 3–5 outcome-level bullets.
- **Tools or source material involved** — only what matters to the participant.
- **Output format** — what file or app format they will use or share.
- **Flags from the brief** — accuracy risk, no easy export, manual review, timing, access limits, or parallel work.

End with:

> "Does this direction make sense? Anything important to change before I write the plan?"

### 2. Let them react

They may:

- Agree → move on.
- Push back on direction → incorporate, re-propose, and get agreement.
- Ask questions → answer concisely, then re-propose if needed.

Iterate until they agree on the direction. Do not move to checks until direction and output format are locked.

### 3. Propose practical checks

Once the direction is agreed, propose 3–5 concrete checks shaped as "when I do X, I should see Y":

- "When I use this on this week's supplier emails, the output should list each supplier, price, delivery date, and missing information."
- "When a cancelled order appears in the export, it should be left out of the summary."
- "When the source file is missing a required column, it should stop and tell us what is missing instead of guessing."

Keep checks observable. Avoid "the answer should be good" or "the system should be fast" — those are not checkable. Propose, let them react, refine. Aim for 3–5; more than 5 usually means you are over-specifying.

### 4. Write `plan-brief.md`

Write this file in the workshop folder:

```markdown
# Plan Brief

## Problem Recap
One paragraph referencing `problem-brief.md`.

## Approach
Concrete description of what to build and how, in plain language.

## Deliverable Shape
What should exist at the end and why this shape fits the work.

## Output Format
What file or app format the participant needs, and any format assumption still to confirm.

## Key Steps
1. …
2. …
3. …

## Tools Or Source Material
- Files, sheets, emails, screenshots, platforms, or other inputs involved.

## Guidance Used
- Accuracy, browser-recording/no-easy-export, parallel work, review gates, or other relevant guidance from `CLAUDE.md`.

## Checks
1. When I do X, I should see Y.
2. When A, B.
3. …
```

### 5. Hand off to build

Close with:

> "Plan is written. Ready to build when you are. The plan brief is your reference — when you say go, I'll start working through it."

Default: build in the same workshop folder. The participant has `problem-brief.md` and `plan-brief.md` here; that is enough context. Do not create a sub-project folder unless the participant explicitly asks.

If they ask for a separate folder:

1. Propose a folder name based on the plan and get a yes.
2. Create the folder and copy `problem-brief.md` and `plan-brief.md` into it.
3. Tell them: "Folder is ready with the two briefs copied in. I'll build there."

Do not scaffold extra files. The briefs are the spec.

## Do Not

- Do not present a menu of approaches. Pick one. Propose it. Let them react.
- Do not ask the participant "what should we build?" — you propose a deliverable shape, they react.
- Do not create participant-facing deliverables before clarifying format when format matters.
- Do not build during solutioning. Solutioning outputs a plan, not the implementation.
- Do not mention missing Git repos or skipped commits in normal workshop flow.
- Do not skip checks. No plan without checks.
