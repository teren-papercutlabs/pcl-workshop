---
name: retro
description: "Build-cycle retrospective — the improvement loop. Trigger for: /retro, retrospective, wrap up, what did we learn."
---

# Retrospective — The Improvement Loop

Run this after every build cycle. The goal is not reflection — it's codification. You're looking for things to encode so the next cycle is better.

## Procedure

### 1. Review the cycle

Look back through what just happened. Briefly note:
- What was built
- Where things went smoothly
- Where things went wrong, got stuck, or needed correction

### 2. Find codification opportunities

For each friction point or pattern, ask these three questions:

**Was there context you had to give that should be permanent?**
→ Add it to CLAUDE.md. Things like preferences, constraints, domain knowledge, working style. If you told Claude something it should have already known, that's a CLAUDE.md gap.

**Was there a situational workflow you figured out?**
→ Make it a skill. A repeatable procedure for a specific job — "how to check stock levels", "how to prepare a weekly report." If you walked through a multi-step process that you'll do again, it should be a skill.

### 3. Important: generalize the improvements

Every rule, skill, or macro must be **general**, not specific to this one case. If Claude got a quantity wrong on an order, the rule is "always confirm quantities before placing orders" — not "when someone says 50 boxes, double-check." The improvement should help in any similar situation, not just replay this exact one.

### 4. Encode it

Make the changes now — update CLAUDE.md, create the skill file, or write the macro. Don't just list what should change. Actually do it. Then commit.

Read back what you changed to the participant so they see the improvement happening.

## Output

Brief summary:
- What was built
- What was codified (which files changed and why)

The changed files are the real output — not the summary.
