---
name: interview
description: "Structured interview to clarify a problem before building. Trigger for: /interview, interview me, help me figure out what I need, clarify requirements."
---

# Interview

The participant wants to work through something — a task, a problem, an idea. Help them get clear on what they actually need. The output is a `problem-brief.md` that captures the problem precisely enough that `/solutioning` can propose an approach.

## Rules

- **One question at a time.** Don't stack.
- **React, not articulate.** Where possible, propose something concrete — an interpretation, a summary, a list — and let them react. Better than asking them to articulate from a blank page.
- **Closed options over open prompts.** When the question is "which of these", give 2–3 options with pros, cons, and your recommendation. They react; they don't guess.
- **Non-technical language.** No jargon. Think in outcomes and business language, not implementation.
- **Don't ask for details you can uncover yourself.** API response shapes, documentation, schemas, library internals — figure them out. Only ask the participant for scope decisions they actually own.
- **~10 questions as a soft target.** Not a hard cap — go further if detail warrants. Stop short if you've covered it.

## Constraints to surface (soft checklist)

As you talk, make sure the following are covered before closing. Weave them in naturally — don't form-fill.

- **External platforms involved?** If yes: API access available? (If no API, we have the option of HAR capture — but don't explain that yet; flag it for solutioning.)
- **Artifacts.** When they mention a specific thing ("a report", "a spreadsheet", "a template"), ask for an example. Don't ask for "all relevant artifacts" upfront — ask inline when specifics emerge.
- **Data shape.** What goes in, what comes out, roughly. Not schemas — just "a list of orders" or "a daily summary".
- **Existing workarounds.** What do they do today when this problem comes up?
- **Output format.** Where does the result land? A file? An email? A spreadsheet cell?

If any of these feel irrelevant to the specific problem, skip them. Judgment call.

## Closing

When you've covered the essentials:

1. Summarise what you've captured — proposed in concrete form, not bullet points ("Here's what I understand: you want to automate the Tuesday morning stock report, which currently you pull manually from Shopify and copy into a shared Google Sheet. The input is the Shopify orders list, the output is a specific Sheet tab. No API issues — Shopify's standard API covers it."). Let them react and correct.

2. Ask the coverage check: "Is there anything else material to the problem that we haven't touched?" (React-not-articulate: you've proposed what you covered; they react by adding what's missing.)

3. When they confirm, write `problem-brief.md` in the workshop folder. Structure:

   ```markdown
   # Problem Brief

   ## Problem
   One paragraph, in the participant's language.

   ## Current State
   What they do today, what breaks or wastes time.

   ## Desired Outcome
   What good looks like.

   ## Constraints
   External platforms, API access, data shape, output format, any hard requirements.

   ## Artifacts
   References to files the participant shared (paths in the workshop folder).

   ## Notes for Solutioning
   Any flags — "no API, consider HAR"; "needs to fit into existing Tuesday report"; etc.
   ```

4. End by invoking `/solutioning`. Tell the participant: "Problem brief written. Moving to solutioning now." Then trigger `/solutioning` — don't make them type it.

## Do Not

- Do not ask technical implementation questions. That's solutioning's job, and it's Claude-driven there too.
- Do not push them to pick a solution during interview. Interview is for the problem, not the answer.
- Do not go past 15 questions without checking in — if the problem is still fuzzy at question 10, surface it: "We're at question 10 and still figuring out what we're solving — want to step back and narrow?"
