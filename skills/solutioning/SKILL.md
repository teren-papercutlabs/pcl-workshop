---
name: solutioning
description: "Propose a deliverable shape, approach, output format, and practical checks for a problem based on an existing problem-brief from the clarification phase. Use for solution design, plan briefs, build-shape decisions, output-format decisions, and post-disambiguation planning regardless of specific wording."
---

# Solutioning

Take the problem from `problem-brief.md` and propose a deliverable shape, approach, output format, and practical checks. Participant reacts and refines. Output is `plan-brief.md`, plus an offer to scaffold a dedicated project folder.

This is the **design decision phase**. There are 100 ways to solve any problem. Your job is to tie down ONE specific direction that the participant agrees with so, when build starts, you both know what will exist at the end and how you'll check it worked.

## Input

Read `problem-brief.md` in the workshop folder. If it's missing, ask the participant: "I can't find a `problem-brief.md`. Do you want to run `/disambiguate` first, or do you have a brief to give me directly?"

## Rules

- **Make the phase visible.** Start by saying plainly: "I'm using the workshop solutioning flow now."
- **Non-technical.** The approach should be describable without jargon. A participant who ran the clarification should understand what you're proposing.
- **Don't ask them for technical details you can uncover yourself.** API response shapes, library capabilities, schema details — figure them out. Ask them only for scope decisions.
- **React-not-articulate.** You propose the deliverable shape, approach, format, and checks. Participant reacts. Never ask "what should we build?" from a blank page.
- **Let the deliverable surface here.** Do not pre-establish the answer before solutioning. Recommend the deliverable shape that fits the brief: skill, helper script, template folder, spreadsheet, document, dashboard, CLI, report, or another concrete artifact.
- **Format is part of the deliverable.** Before creating files, ask or infer whether outputs need formats like `.docx`, `.xlsx`, Google Docs/Sheets, PDF, Markdown, CSV, slides, or a dashboard. If the format changes the work, ask one clear question before creating.
- **Consult the techniques library where relevant.** If the brief flagged "no API" → consult `techniques/no-api-workflows.md` (HAR capture). If accuracy is a concern → `techniques/accuracy.md`. If the problem is parallel-heavy → `techniques/parallel-subagents.md`. Reference them briefly in your proposal — don't recite them.
- **No Git assumptions.** Workshop participants usually do not have Git repos. Do not mention commits, Git status, or "could not commit" unless the participant explicitly asks for version control or the workshop is technical.

## Procedure

### 1. Propose the approach

Say:

> "I'm using the workshop solutioning flow now."

Read the problem brief. Think through it. Pick one concrete direction — the one you'd actually build. Propose it in 4–8 sentences covering:

- **Deliverable shape** — what should exist at the end ("a reusable spreadsheet plus a short document template", "a workshop skill with two helper scripts", "a small dashboard")
- **Why that shape** — the practical reason it fits this participant's work
- **Key steps** — 3–5 bullets, outcome-level
- **Tools involved** — what's involved, concisely, only where useful
- **Output format** — what file/app format the participant will use or share
- **Flags from the brief** — if a technique applies, reference it ("No API access for <platform> — we'll use the HAR capture technique for this")

End with: "Does this direction make sense? Anything important to change before I write the plan?"

### 2. Let them react

They may:
- Agree → move on
- Push back on direction → incorporate, re-propose, get agreement
- Ask questions → answer concisely, then re-propose if needed

Iterate until they agree on the direction. Don't move to checks until direction and output format are locked.

### 3. Propose practical checks

Once the direction is agreed, propose 3–5 concrete checks — shaped as "when I do X, I should see Y":

- "When I run the script on a Tuesday morning, I should see the Tuesday tab in the shared Sheet populated with the week's orders grouped by product."
- "When an order is cancelled, it should not appear in the summary."
- "When I run it on a non-Tuesday, it should refuse gracefully — not silently dump data into the wrong tab."

Keep checks observable. Avoid "the code should be clean" or "it should be fast" — those aren't checkable. Propose → let them react → refine. Aim for 3–5; more than 5 usually means you're over-specifying.

### 4. Write plan-brief.md

Write to the workshop folder:

```markdown
# Plan Brief

## Problem Recap
One paragraph referencing `problem-brief.md`.

## Approach
Concrete description of what to build and how, in plain language.

## Deliverable Shape
What should exist at the end and why this shape fits the work.

## Output Format
What file/app format the participant needs, and any format assumption still to confirm.

## Key Steps
1. …
2. …
3. …

## Tools Involved
- What external platforms, APIs, libraries, files, or apps are involved.

## Techniques Referenced
- If any techniques from the library apply, name them.

## Checks
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
- Do not ask the participant "what should we build?" — you propose a deliverable shape, they react.
- Do not create participant-facing deliverables before clarifying format when format matters.
- Do not write code. Solutioning outputs a plan, not an implementation.
- Do not mention missing Git repos or skipped commits in normal workshop flow.
- Do not skip checks. No plan without checks — that's the whole point of the skill.
