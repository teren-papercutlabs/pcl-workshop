# pcl-workshop

Papercut Labs' Claude Code plugin for consulting workshops. Scaffolds a structured interview → solutioning → build → retro loop for non-technical workshop participants.

## What's Inside

Four skills:

- `/workshop-bootstrap` — one-time scaffold of a workshop folder (CLAUDE.md + techniques library)
- `/interview` — structured discovery to produce `problem-brief.md`
- `/solutioning` — Claude proposes an approach + verification criteria, writes `plan-brief.md`, offers to create a dedicated project folder
- `/retro` — end-of-cycle retrospective; Claude self-critiques, participant reacts, learnings encoded into CLAUDE.md and MEMORY.md

Techniques library (consulted on demand, not invoked directly):

- `techniques/no-api-workflows.md` — HAR capture and replay
- `techniques/accuracy.md` — keeping Claude's output reliable
- `techniques/parallel-subagents.md` — parallelisation for speed

## Install

```
/plugin marketplace add teren-papercutlabs/pcl-workshop
/plugin install pcl-workshop@pcl-workshop
```

Works in both Claude Desktop and Claude Code CLI.

## Using It

1. Make a folder for your workshop work: `mkdir ~/claude-workshop && cd ~/claude-workshop`
2. Start Claude: `claude`
3. Run `/workshop-bootstrap` — scaffolds the folder with CLAUDE.md and techniques
4. Restart Claude (so CLAUDE.md is picked up)
5. Run `/interview` to work through your first problem
6. Follow the prompts — `/solutioning` is chained automatically
7. Build in the project folder
8. Run `/retro` at the end of each cycle

## Design Principles

- **React, not articulate.** Claude proposes — participant reacts. Recognition is cheaper than recall for non-technical participants.
- **Distinctly non-technical.** Interview and solutioning use plain business language. No jargon, no implementation details unless asked.
- **Don't ask for what Claude can discover.** API response shapes, documentation, schemas — Claude figures those out. Only ask the participant for scope decisions they actually own.
- **Plugin is scaffolding, not a cage.** Participants should outgrow it. The skills teach patterns (react-not-articulate, verification-criteria-first, retro-to-codify) that transfer beyond the workshop.

## Who This Is For

PcL workshop participants — non-technical folks learning to work with Claude Code. If you're technical, the skills still work but the voice is tuned for people who don't think in code.
