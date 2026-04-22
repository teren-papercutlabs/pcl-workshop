---
name: workshop-bootstrap
description: "Scaffold a workshop folder with the plugin's CLAUDE.md and techniques library. Run once at the start of the workshop. Trigger for: /workshop-bootstrap, workshop-bootstrap, set up workshop, scaffold workshop, start workshop."
---

# Workshop Bootstrap

Set up a workshop folder with the plugin's behavioural rules and techniques library in place. Run this once, at the start of the workshop.

## Procedure

### 1. Confirm the location

The participant is likely running this in the folder they want to use. Confirm before writing anything:

> "I'll set up workshop scaffolding here: `<pwd>`. This writes a `CLAUDE.md` and a `techniques/` directory into this folder. OK?"

Wait for confirmation. If they want a different location, `mkdir -p` the path and `cd` there, then continue.

### 2. Locate the plugin root

Run this bash to find the installed plugin:

```bash
PLUGIN_ROOT=$(find ~/.claude/plugins -maxdepth 6 -type f -name plugin.json -exec grep -l '"name": "pcl-workshop"' {} \; 2>/dev/null | head -1 | xargs dirname | xargs dirname)
echo "$PLUGIN_ROOT"
```

If empty, the plugin isn't installed properly. Tell the participant:

> "I can't find the pcl-workshop plugin on this machine. Make sure it's installed: `/plugin install pcl-workshop@pcl-workshop` after adding the marketplace."

### 3. Copy CLAUDE.md

```bash
cp "$PLUGIN_ROOT/templates/workshop-CLAUDE.md" ./CLAUDE.md
```

As you do this, narrate a short orientation — one sentence per section. Not a lecture, just a brief walkthrough:

- **Voice rules** — concise, no preambles, react-not-articulate.
- **The Rule** — Claude does everything, participant doesn't type commands.
- **Working Style** — delegate, scripts-over-brain, clarify-by-proposing, commit often.
- **The Loop** — interview → solutioning → build → retro.
- **Techniques** — reference library consulted when topics come up.

### 4. Copy the techniques library

```bash
cp -r "$PLUGIN_ROOT/techniques" ./
```

Three files land:

- `techniques/no-api-workflows.md`
- `techniques/accuracy.md`
- `techniques/parallel-subagents.md`

Don't walk through their contents now. They're consulted on demand.

### 5. Tell them what's next

> "Workshop folder is ready. Restart Claude in this folder so it picks up CLAUDE.md, then run `/interview` when you want to work through your first problem."

Don't run `/interview` in this session. The participant needs to restart so CLAUDE.md is loaded.

### 6. Commit (optional)

If the folder is already a git repo, `git add . && git commit -m "workshop-bootstrap"`. If not, skip — don't force `git init` on the participant.

## Output

After this runs, the workshop folder contains:

```
<workshop-folder>/
├── CLAUDE.md
└── techniques/
    ├── no-api-workflows.md
    ├── accuracy.md
    └── parallel-subagents.md
```

Nothing else. `/interview` and `/solutioning` will add `problem-brief.md`, `plan-brief.md`, and a project subfolder later.

## Do Not

- Do not `git init` unsolicited
- Do not create extra files (README.md, .gitignore, etc.)
- Do not run `/interview` immediately after — restart required
