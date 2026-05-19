# Workshop Final Debrief Skill Review Package

This package is the AM-review packet for WB `5966cd71-d634-4780-a1cd-11e4b0d3402f`.

## What Is Here

- New skill: `../../.agents/skills/debrief/SKILL.md`
- Clean transcript: `transcript.md`
- Raw Claude Code TUI transcript: `claude-transcript.raw.gz`
- Actual debrief output: `final-debrief.md`
- Test participant environment: `test-environment/`

## Test Environment

The simulated participant was Maya, a finance/ops lead for a small food importer. Her workshop workflow was non-technical: turn three weekly CSV exports into a Monday cash-watch note for the founder.

The environment used the exact workshop bootstrap instructions: `templates/workshop-AGENTS.md` was copied to `CLAUDE.md` before the Claude Code run.

## Honest Assessment

This did uncover useful truth; it was not only debrief theatre.

What worked:

- The artifact-first inspection found issues a polite participant likely would not volunteer: the "What Changed" section had no prior-week baseline, "current cash" was undefined with future-dated rows, and CSV column drift was unresolved.
- The react-not-articulate questions surfaced the real adoption blocker: not "confidence" in the abstract, but the first weird Monday when a CSV looks different and Claude gives either a technical error or a confident-looking wrong answer.
- The indirect 80% question separated one workflow category from the participant's whole job. That is exactly the distinction a direct "how confident are you?" question would likely blur.
- It surfaced a hidden in-room concern: the participant felt uneasy trusting a finance note she did not assemble herself, but would not have said that while everyone else sounded excited.

Where it felt hollow or weak:

- The first reflection bundled three soft spots before letting the participant react. That gave good signal here, but it risks becoming a mini-audit instead of a debrief. I tightened the skill after the run to force one adoption-relevant beat at a time.
- It also bundled the 80% boundary and the hidden-concern prompt in one turn. Again, good signal, wrong shape. The committed skill now says not to ask two questions in the same turn.
- Claude scanned `~/.claude/skills/` before inspecting the known skill path, which is too broad for a participant environment. The committed skill now explicitly says to infer the skill name from the briefs and inspect only that folder.

Bottom line: the mechanism is promising. The core move that worked was not "ask for feedback"; it was "look at the artifacts, propose the concern the participant may be quietly carrying, and make them react." The skill needed sharper guardrails against bundling, and those are now in the committed version.
