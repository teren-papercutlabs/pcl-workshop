# pcl-workshop

Papercut Labs workshop scaffolding for non-technical participants using Codex or Claude Code.

## For workshop participants — paste this to start

Open Claude Code in any folder, then paste this prompt. Claude reads this README and does the rest.

```
Read https://raw.githubusercontent.com/teren-papercutlabs/pcl-workshop/master/README.md and follow the "Claude Code Instructions" section to set up a workshop project for me. Before installing anything, run `pwd` and check that I'm in a project folder (not my home directory and not /). If I'm in home or root, create a folder for this workshop at ~/Desktop/projects/<sensible-name>, tell me to start a new Claude Code session in that folder and paste this prompt again, then stop. If I'm already in a project folder, proceed with the install — install the skills globally to ~/.claude/skills/, drop CLAUDE.md at the project root, copy techniques. Then verify and tell me what to do next.
```

That's it — copy/paste the block above into a fresh Claude Code session.

The workshop loop is:

1. **Interview** — clarify the problem by reacting to concrete statements and short questions. Output: `problem-brief.md`.
2. **Solutioning** — propose a deliverable shape, output format, plan, and concrete checks. Output: `plan-brief.md`.
3. **Build** — implement against the agreed plan.
4. **Retro** — encode what was learned so the next cycle improves.

## What's Inside

Skills (project-level, auto-discovered by the runtime when it starts in the workshop folder):

- **`/interview`** — clarification and structured discovery; writes `problem-brief.md`.
- **`/solutioning`** — proposes deliverable shape, output format, plan, and checks; writes `plan-brief.md`.
- **`/retro`** — end-of-cycle reflection that improves the next round.

Reference techniques (read on demand):

- `techniques/no-api-workflows.md` — working with platforms that have no usable API.
- `techniques/accuracy.md` — keeping output reliable.
- `techniques/parallel-subagents.md` — parallelising independent work.

Project AGENTS.md:

- `templates/workshop-AGENTS.md` — the canonical project-level rules. Bootstrap copies this to `AGENTS.md` at the participant's project root.

## Repo Layout

```
pcl-workshop/
├── README.md                 ← this file (read by the bootstrap agent)
├── .agents/skills/           ← canonical skill source (codex auto-discovers from project root)
│   ├── interview/SKILL.md
│   ├── solutioning/SKILL.md
│   └── retro/SKILL.md
├── techniques/
│   ├── accuracy.md
│   ├── no-api-workflows.md
│   └── parallel-subagents.md
└── templates/
    └── workshop-AGENTS.md    ← copied to <project>/AGENTS.md during bootstrap
```

The repo mirrors the deployed project structure. Bootstrap clones the repo and copies the relevant pieces into the participant's project folder.

## Codex Instructions

If you are an agent reading this README to bootstrap a workshop project for a participant:

You are setting up a workshop project at the current working directory. The cwd should be `~/Desktop/projects/pcl-workshop/` (or whatever empty project folder the participant created and opened Codex in).

Run these steps in order. Narrate each step plainly to the participant as you go.

### 1. Confirm location

Print the cwd and confirm:

```bash
pwd
```

Tell the participant in plain English: "I'll set up the workshop here: `<pwd>`. This writes an `AGENTS.md`, a `.agents/skills/` directory, and a `techniques/` directory into this folder."

If the cwd is not what was intended, ask the participant to close Codex and reopen it from the right folder. Do not `cd` to a different folder mid-bootstrap — Codex's project context is bound to the folder it was started in.

### 2. Fetch the workshop kit

```bash
git clone --depth 1 https://github.com/teren-papercutlabs/pcl-workshop.git /tmp/pcl-workshop-src
```

If `git clone` fails (no network, no git), fall back to `curl`:

```bash
curl -fsSL https://github.com/teren-papercutlabs/pcl-workshop/archive/refs/heads/master.tar.gz | tar -xzC /tmp && mv /tmp/pcl-workshop-master /tmp/pcl-workshop-src
```

### 3. Install the project files

```bash
cp /tmp/pcl-workshop-src/templates/workshop-AGENTS.md ./AGENTS.md
cp -r /tmp/pcl-workshop-src/.agents ./
cp -r /tmp/pcl-workshop-src/techniques ./
```

### 4. Clean up

```bash
rm -rf /tmp/pcl-workshop-src
```

### 5. Verify the install

```bash
ls -la AGENTS.md .agents/skills techniques
```

Expected: `AGENTS.md` exists, `.agents/skills/` contains `interview/`, `solutioning/`, `retro/`, and `techniques/` contains three `.md` files.

### 6. Tell the participant what's next

Tell them in plain English:

> "Workshop folder is ready. To pick up the new skills and project rules, start a fresh Codex thread in this folder (or restart Codex). When the new thread is open, tell me what you want to work on and I'll use `/interview` to walk you through it."

Then **stop**. Do not auto-fire `/interview`. The participant needs to start a new thread first so Codex picks up `AGENTS.md` and the skills.

## Claude Code Instructions

If you are Claude Code reading this README to bootstrap a workshop project for a participant:

### 1. Check the location first

```bash
pwd
```

If the cwd is the participant's home directory (`$HOME`, e.g. `/Users/<name>`) or root (`/`), DO NOT install. Instead:

```bash
mkdir -p ~/Desktop/projects/pcl-workshop
```

(Adjust the folder name if context suggests a more specific one — e.g. `~/Desktop/projects/<their-business-or-topic>`.)

Then tell the participant in plain English:

> "I created a folder for this workshop at `~/Desktop/projects/pcl-workshop`. Quit this Claude Code session, open a new one in that folder (`cd ~/Desktop/projects/pcl-workshop && claude`), and paste the bootstrap prompt again. Then I can install the workshop tools."

Then **stop**. Do not continue installing — the install needs to happen in a fresh session bound to the new folder.

If the cwd is already a project folder (anything other than home/root), continue.

### 2. Fetch the workshop kit

```bash
git clone --depth 1 https://github.com/teren-papercutlabs/pcl-workshop.git /tmp/pcl-workshop-src
```

Fallback if `git clone` fails:

```bash
curl -fsSL https://github.com/teren-papercutlabs/pcl-workshop/archive/refs/heads/master.tar.gz | tar -xzC /tmp && mv /tmp/pcl-workshop-master /tmp/pcl-workshop-src
```

### 3. Install — skills global, project rules + techniques local

Skills install to `~/.claude/skills/` (global, available across all your CC sessions). Project rules and techniques install to the current folder.

```bash
mkdir -p ~/.claude/skills
cp -r /tmp/pcl-workshop-src/.agents/skills/* ~/.claude/skills/
cp /tmp/pcl-workshop-src/templates/workshop-AGENTS.md ./CLAUDE.md
cp -r /tmp/pcl-workshop-src/techniques ./
```

### 4. Clean up

```bash
rm -rf /tmp/pcl-workshop-src
```

### 5. Verify

```bash
ls -la CLAUDE.md techniques ~/.claude/skills
```

Expected: `CLAUDE.md` exists in this folder, `techniques/` contains three `.md` files, `~/.claude/skills/` contains `interview/`, `solutioning/`, `retro/`.

### 6. Tell the participant what's next

Tell them in plain English:

> "Workshop folder is ready. Skills are installed globally so they'll work in any Claude Code session you start. To pick up the new `CLAUDE.md` for this project, start a fresh Claude Code session in this folder. Then tell me what you want to work on and I'll use `/interview` to walk you through it."

Then **stop**. Do not auto-fire `/interview`. The participant needs a fresh session so Claude picks up the local `CLAUDE.md`.

## Manual Setup (No Agent)

If a participant prefers to set up the folder by hand:

```bash
mkdir -p ~/Desktop/projects/pcl-workshop
cd ~/Desktop/projects/pcl-workshop
git clone --depth 1 https://github.com/teren-papercutlabs/pcl-workshop.git /tmp/pcl-workshop-src
cp /tmp/pcl-workshop-src/templates/workshop-AGENTS.md ./AGENTS.md
cp -r /tmp/pcl-workshop-src/.agents ./
cp -r /tmp/pcl-workshop-src/techniques ./
rm -rf /tmp/pcl-workshop-src
```

Then open Codex in that folder and start a thread.

## Windows Note

On Windows, use Git Bash rather than PowerShell or Command Prompt. The bootstrap commands assume bash-style paths and quoting.

If Git Bash is missing, install it from <https://gitforwindows.org/>.

## Troubleshooting

**Skills don't appear after bootstrap**

Skills load at session start. Start a new Codex thread in the workshop folder so it re-reads `.agents/skills/`.

**`AGENTS.md` not picked up**

Same fix — start a new thread. Codex reads `AGENTS.md` at session start.

**`git clone` fails**

Try the GitHub CLI:

```bash
gh repo clone teren-papercutlabs/pcl-workshop /tmp/pcl-workshop-src
```

Or download the ZIP from <https://github.com/teren-papercutlabs/pcl-workshop>, unzip it to `/tmp/pcl-workshop-src`, and continue from step 3.
