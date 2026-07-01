# pcl-workshop

Papercut Labs workshop scaffolding for non-technical participants using the Claude desktop app.

## For workshop participants — paste this to start

1. Open the Claude desktop app.
2. Start a new session.
3. Select this folder: `~/Documents/projects/workshop/pcl-workshop`.
4. Paste this prompt:

```text
Read https://raw.githubusercontent.com/teren-papercutlabs/pcl-workshop/master/README.md and follow the "Claude desktop app setup" section to set up a workshop project for me.
```

If that folder does not exist yet, start from any folder, paste the prompt, and Claude will create the workshop folder for you. Then it will ask you to start a new session and select the workshop folder.

The workshop loop is:

1. **Interview** — clarify the problem by reacting to concrete statements and short questions. Output: `problem-brief.md`.
2. **Solutioning** — propose a useful deliverable, output format, plan, and concrete checks. Output: `plan-brief.md`.
3. **Build** — make the thing described in the plan.
4. **Retro** — reflect, capture your point of view, and write future-useful context into `CLAUDE.md`.
5. **Debrief** — at workshop close, surface adoption concerns and write `final-debrief.md` for the facilitator.

## What's inside

- `CLAUDE.md` — the project instructions and workshop memory. This is the single home for workshop rules, techniques, business context, and future-session notes.
- `.agents/skills/` — the skill source copied into Claude's global skills folder during setup:
  - `/interview`
  - `/solutioning`
  - `/retro`
  - `/debrief`

## Repo layout

```text
pcl-workshop/
├── README.md                 ← setup instructions read by Claude
├── CLAUDE.md                 ← copied into the participant's workshop folder
└── .agents/skills/           ← copied into Claude's global skills folder
    ├── interview/SKILL.md
    ├── solutioning/SKILL.md
    ├── retro/SKILL.md
    └── debrief/SKILL.md
```

The participant's workshop folder should end up at:

```text
~/Documents/projects/workshop/pcl-workshop
```

## Claude desktop app setup

If you are Claude reading this README to set up a workshop project for a participant, follow this section.

### 1. Check the folder

Run:

```bash
pwd
```

The workshop folder must be:

```text
~/Documents/projects/workshop/pcl-workshop
```

If the current folder is anything else, do **not** install here. Create the workshop folder:

```bash
mkdir -p ~/Documents/projects/workshop/pcl-workshop
```

Then tell the participant, in plain English:

> "I created the workshop folder at `~/Documents/projects/workshop/pcl-workshop`. Start a new session in the Claude desktop app, select that folder, paste the setup prompt again, and I'll install the workshop tools there."

Then **stop**. Do not continue installing in the wrong folder.

If the current folder is already `~/Documents/projects/workshop/pcl-workshop`, continue.

### 2. Fetch the workshop kit

Run:

```bash
git clone --depth 1 https://github.com/teren-papercutlabs/pcl-workshop.git /tmp/pcl-workshop-src
```

If that fails because git or the network is unavailable, try this fallback:

```bash
curl -fsSL https://github.com/teren-papercutlabs/pcl-workshop/archive/refs/heads/master.tar.gz | tar -xzC /tmp && mv /tmp/pcl-workshop-master /tmp/pcl-workshop-src
```

### 3. Install the files

Skills install globally so Claude can use `/interview`, `/solutioning`, `/retro`, and `/debrief` from the workshop session. `CLAUDE.md` installs into the workshop folder and becomes the session memory.

First install the skills:

```bash
mkdir -p ~/.claude/skills
cp -r /tmp/pcl-workshop-src/.agents/skills/* ~/.claude/skills/
```

Then install the workshop memory file. If `./CLAUDE.md` already exists, do not overwrite it silently. Tell the participant you found an existing project memory file and ask whether to replace it or merge the workshop instructions into it.

If there is no existing `CLAUDE.md`, run:

```bash
cp /tmp/pcl-workshop-src/CLAUDE.md ./CLAUDE.md
```

If the participant chooses to merge instead of replace, preserve their existing notes and add the workshop sections from `/tmp/pcl-workshop-src/CLAUDE.md`.

### 4. Clean up

Run:

```bash
rm -rf /tmp/pcl-workshop-src
```

### 5. Verify

Run:

```bash
ls -la CLAUDE.md ~/.claude/skills
```

Expected:

- `CLAUDE.md` exists in the workshop folder.
- `~/.claude/skills/` contains `interview/`, `solutioning/`, `retro/`, and `debrief/`.

### 6. Tell the participant what's next

Tell them in plain English:

> "Workshop folder is ready. Start a new session in the Claude desktop app and select `~/Documents/projects/workshop/pcl-workshop` so Claude picks up the workshop memory. Then tell me what you want to work on and I'll use `/interview` to walk through it."

Then **stop**. Do not auto-fire `/interview`. The participant needs a fresh session so Claude reads the local `CLAUDE.md`.

## Troubleshooting

**Skills do not appear after setup**

Start a new session in the Claude desktop app and select the workshop folder. Skills and project instructions are picked up when the session starts.

**`CLAUDE.md` does not seem to be used**

Start a new session in the Claude desktop app and select `~/Documents/projects/workshop/pcl-workshop`.

**Fetching the workshop kit fails**

Tell the participant:

> "I could not download the workshop kit from GitHub. Please ask the facilitator for help with the workshop setup."
