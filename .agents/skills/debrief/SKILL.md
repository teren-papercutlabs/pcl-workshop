---
name: debrief
description: "Run the final end-of-workshop participant debrief. Use at workshop close to inspect the participant's actual workflow artifacts, surface adoption concerns through react-not-articulate reflection, infer confidence from behavior and indirect answers, and write a structured final-debrief.md for the facilitator regardless of specific wording. Invoke only when the participant explicitly asks for the final debrief."
disable-model-invocation: true
---

# Final Workshop Debrief

Use this once at the end of the workshop. This is the backstop after the facilitator's in-room rotation: uncover what the participant actually believes about using Claude tomorrow, especially concerns they would not volunteer to "any feedback?".

The output is `final-debrief.md`. Do not send it anywhere. The participant can share the file with Teren or the facilitator through the agreed channel.

## How This Will Go

Start by saying:

> "I'm using the final workshop debrief now. I'll look at what we built and how the workflow is set up, then I'll put concrete observations in front of you. You react and correct me. I won't ask you to rate your confidence. At the end I write `final-debrief.md` for Teren; I don't send anything."

Then proceed one beat at a time.

## Rules

- **End-fire only.** Run this at workshop close, not during build work.
- **React, not articulate.** Do not ask blank-page questions like "any feedback?" or "how confident are you?" Make concrete observations and let the participant agree, disagree, or correct.
- **One reflection beat at a time.** If you see several concerns, choose the most adoption-relevant one first and hold the others. Do not list multiple soft spots before the participant reacts. Do not ask two questions in the same turn.
- **Infer confidence from behavior.** Look at what they actually built, what they kept in `CLAUDE.md`, what became a skill, whether they ran `/retro`, how much of the work and context are captured in `CLAUDE.md`, how much can realistically start in Claude tomorrow, and where human review is still required.
- **Use indirect confidence questions.** Ask about tomorrow's first blocker, the point where they would revert to the old way, whether they can get past the 80% bar for this kind of work, and what would make them quietly stop using it.
- **Follow the participant's signal.** Known anchors are feedback, concerns, confidence, adoption depth, `/retro`, and stored instructions or skills. They are starting points, not a fixed questionnaire.
- **Separate facts from inference.** In the output, clearly distinguish what the participant said, what the files show, and what you infer.
- **Keep control with the participant.** If they say something is private, omit it or mark it as not for sharing.
- **Use plain workshop English.** No consultant memo voice. No technical examples unless the participant's actual workflow is technical.

## Procedure

### 1. Inspect The Session Artifacts

Look for the real workshop outputs before asking questions:

- Workshop memory and rules: `CLAUDE.md`.
- Briefs: `problem-brief.md`, `plan-brief.md`.
- Built workflow: project skills, named output files, helper files, templates, sheets, documents, or other files referenced in the briefs.
- Learning capture: future-useful facts, preferences, decisions, and workflow notes written into `CLAUDE.md`.

If the built workflow is in `~/.claude/skills/`, infer the skill name from the briefs first and inspect only that skill folder. Do not list all global skills. If you cannot tell which skill came from this workshop, ask one short question: "Which skill did we build today?"

Do not inspect unrelated personal folders.

### 2. State Your First Read

Give one short evidence-based read:

- Name the workflow.
- Name the strongest adoption-relevant concern you see.
- Ask the participant to react.

Keep it concrete. Example:

> "My read: this is usable for a first draft of the weekly cash note, but not yet trusted as the final finance view. The skill exists, but I don't see the review rule captured in `CLAUDE.md`, so the likely risk is forgetting the human check when you're under time pressure. React to that: right, wrong, or partly right?"

### 3. Run The Reflection Beats

Use one observation or indirect question at a time. Adapt to the participant's answers. Do not run these as a checklist; pick the next beat based on the last answer.

If you have several possible observations, do this:

1. Pick the one most likely to change whether the participant uses the workflow tomorrow.
2. Get their reaction.
3. Summarise the signal in one sentence.
4. Only then choose the next beat.

Useful beat shapes:

- "The part I think you would use tomorrow is X; the part you might avoid is Y. Right or wrong?"
- "If this fails next week, I think it fails at X, not Y. Correct me."
- "This looks like it gets you to a good draft, but not something you would send without checking. Is that the real boundary?"
- "The 80% target seems possible for this workflow category, but not your whole job yet. Does that feel true?"
- "What would make you quietly go back to the old spreadsheet/email/doc process?"
- "If Teren asked what you did not say in the room, I think it would be X. Am I off?"
- "I don't see evidence that the habit is stored anywhere yet. Is the risk that you remember this today but don't start here next week?"

If the participant gives polite or vague approval, sharpen gently:

> "I'm going to test the polite version. What is the first moment next week where you might decide this is more trouble than the old way?"

### 4. Decide What Is Actually True

Before writing, settle these points in your own words:

- **Adoption read:** likely daily/weekly/occasional use, or unlikely without follow-up.
- **Confidence evidence:** behavior and indirect answers, not a numeric self-rating.
- **80% path:** whether 80% is plausible for this workflow category, and what blocks it.
- **Hidden concern:** the thing the participant was unlikely to volunteer in person.
- **Follow-up:** the smallest practical next step that would raise adoption odds.

### 5. Write `final-debrief.md`

Write this file in the workshop folder:

```markdown
# Final Workshop Debrief

## Participant And Workflow
- Participant:
- Role / team:
- Workflow built:
- Main files or skills:

## Adoption Read
- Likely use:
- 80% path:
- Boundary:

## What The Participant Said
- ...

## What The Files Show
- ...

## Concerns And Blockers
- ...

## Confidence Signals
- ...

## What Teren Probably Did Not Catch In-Room
- ...

## Recommended Follow-Up
- ...
```

Keep the file concise and useful. Do not pad it with every exchange.

### 6. Close

Tell the participant:

> "`final-debrief.md` is written. It has the parts Teren needs: what you built, what you would actually use, what still worries you, and what follow-up would help. Send that file through the agreed channel."

## Do Not

- Do not modify `/retro`, `/interview`, or the workflow skill during the debrief unless the participant explicitly asks.
- Do not ask for a confidence rating.
- Do not turn this into a satisfaction survey.
- Do not accept "all good" as the whole answer when the artifacts suggest a real blocker.
- Do not send messages, emails, or live pings.
