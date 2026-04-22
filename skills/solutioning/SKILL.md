---
name: solutioning
description: "Propose an approach and verification criteria for a problem, based on an existing problem-brief. Claude drives — participant reacts. Trigger for: /solutioning, solutioning, propose a solution, what should we build, define done."
---

# Solutioning

Take the problem from `problem-brief.md` and propose an approach + verification criteria. Participant reacts and refines. Output is `plan-brief.md`, plus an offer to scaffold a dedicated project folder.

This is the **design decision phase**. There are 100 ways to solve any problem. Your job is to tie down ONE specific approach that the participant agrees with — so when build starts, you both know what's being built and how you'll know it's done.

## Input

Read `problem-brief.md` in the workshop folder. If it's missing, ask the participant: "I can't find a `problem-brief.md`. Do you want to run `/interview` first, or do you have a brief to give me directly?"

## Rules

- **Non-technical.** The approach should be describable without jargon — a participant who ran the interview can understand what you're proposing.
- **Don't ask them for technical details you can uncover yourself.** API response shapes, library capabilities, schema details — figure them out. Ask them only for scope decisions.
- **React-not-articulate.** You propose the approach and the criteria. Participant reacts. Never ask "what's your verification criteria?" — propose them.
- **Consult the techniques library where relevant.** If the brief flagged "no API" → consult `techniques/no-api-workflows.md` (HAR capture). If accuracy is a concern → `techniques/accuracy.md`. If the problem is parallel-heavy → `techniques/parallel-subagents.md`. Reference them briefly in your proposal — don't recite them.

## Procedure

### 1. Propose the approach

Read the problem brief. Think through it. Pick one concrete approach — the one you'd actually build. Propose it in 4–8 sentences covering:

- **What to build** — in plain language ("a CLI that reads orders from Shopify every Tuesday morning and writes a summary into the shared Sheet tab")
- **Key steps** — 3–5 bullets, outcome-level
- **Tech/tools** — what's involved, concisely ("Shopify Admin API for orders, Google Sheets API for output")
- **Flags from the brief** — if a technique applies, reference it ("No API access for <platform> — we'll use the HAR capture technique for this")

End with: "Does this approach make sense? Want to adjust direction?"

### 2. Let them react

They may:
- Agree → move on
- Push back on direction → incorporate, re-propose, get agreement
- Ask questions → answer concisely, then re-propose if needed

Iterate until they agree on the approach. Don't move to criteria until direction is locked.

### 3. Propose verification criteria

Once the approach is agreed, propose 3–5 concrete behavioural verification criteria — shaped as "when I do X, I should see Y":

- "When I run the script on a Tuesday morning, I should see the Tuesday tab in the shared Sheet populated with the week's orders grouped by product."
- "When an order is cancelled, it should not appear in the summary."
- "When I run it on a non-Tuesday, it should refuse gracefully — not silently dump data into the wrong tab."

Keep criteria observable and testable. Avoid "the code should be clean" or "it should be fast" — those aren't checkable. Propose → let them react → refine. Aim for 3–5; more than 5 usually means you're over-specifying.

### 4. Write plan-brief.md

Write to the workshop folder:

```markdown
# Plan Brief

## Problem Recap
One paragraph referencing `problem-brief.md`.

## Approach
Concrete description of what to build and how, in plain language.

## Key Steps
1. …
2. …
3. …

## Tech/Tools
- What external platforms, APIs, or libraries are involved.

## Techniques Referenced
- If any techniques from the library apply, name them.

## Verification Criteria
1. When I do X, I should see Y.
2. When A, B.
3. …
```

### 5. Offer the project folder

Close with:

> "Plan is written. Want me to set up a dedicated project folder? That gives this project its own space with its own `CLAUDE.md` that has the approach and criteria baked in — useful when you come back to this later or want to build multiple things in parallel."

If they say yes:

1. Ask for a project folder name if not obvious from the plan ("shopify-tuesday-report" or similar). Propose a name first — react-not-articulate.
2. `mkdir <project-name>` as a subfolder of the workshop folder.
3. Locate the plugin template:

   ```bash
   PLUGIN_ROOT=$(find ~/.claude/plugins -maxdepth 6 -type f -name plugin.json -exec grep -l '"name": "pcl-workshop"' {} \; 2>/dev/null | head -1 | xargs dirname | xargs dirname)
   ```

4. Read `$PLUGIN_ROOT/templates/project-CLAUDE.md`, substitute the placeholders with values derived from the plan-brief:

   - `{{PROJECT_NAME}}` → human-readable project name
   - `{{APPROACH_SUMMARY}}` → the approach text from `plan-brief.md`
   - `{{KEY_STEPS}}` → numbered list from the plan
   - `{{TECH_TOOLS}}` → tech/tools from the plan
   - `{{VERIFICATION_CRITERIA}}` → numbered criteria from the plan

5. Write the filled template to `<project-name>/CLAUDE.md`.

6. Tell them: "Project folder is at `<workshop>/<project-name>`. When you're ready to build, `cd` into it and start a fresh Claude session so it picks up the project-specific CLAUDE.md."

If they say no → stop. They can build in the workshop folder directly, or run `/solutioning` again later for a different framing.

## Do Not

- Do not present a menu of approaches. Pick one. Propose it. Let them react. The workshop doesn't have time for A/B/C decision paralysis at this layer — your job is to decide and justify.
- Do not ask the participant "what should we build?" — you propose, they react.
- Do not write code. Solutioning outputs a plan, not an implementation.
- Do not skip criteria. No plan without verification — that's the whole point of the skill.
