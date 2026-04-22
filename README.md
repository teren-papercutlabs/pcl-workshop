# pcl-workshop

Papercut Labs' Claude Code skills for consulting workshops. Scaffolds a structured **interview → solutioning → build → retro** loop for non-technical participants.

> **Note to Sarah** — Sending this directly so the team has it before Friday's session. Pass it on as you see fit; happy to walk anyone through it. We're routing around the standard `/plugin marketplace` install because corporate-managed machines typically block it, so the steps below use a clone-the-repo approach instead. Apologies for skipping the usual review pass on the timing.

## What's Inside

Four workshop skills you'll use during the session:

- **`/interview`** — structured discovery for the problem you want to solve
- **`/solutioning`** — Claude proposes an approach plus concrete verification criteria
- **`/retro`** — end-of-cycle reflection that improves the next round
- **`/workshop-bootstrap`** — one-time scaffolder (the install steps below run this for you, so you won't need to call it directly)

Plus a small techniques library Claude consults on demand: working with platforms that have no API, keeping accuracy high, parallelising work across subagents.

---

## Step 0: Make Sure Claude Code Is Installed

You should already have Claude Code on your machine from earlier in the workshop prep. If not, install it from <https://docs.claude.com/claude-code> before continuing.

---

## Step 1 (Windows Only): Install Git Bash

Claude Code expects a bash-style shell. Windows defaults to **PowerShell** and **Command Prompt**, which behave differently — paths, quoting, and pipes don't match what Claude assumes, and you'll see commands silently misbehave.

1. Download Git for Windows from **<https://gitforwindows.org/>**
2. Run the installer. The defaults are fine — just click through.
3. Once installed, right-click on your desktop or in any folder and confirm you see **"Git Bash Here"** in the menu.
4. **Use Git Bash for every step below.** Not PowerShell. Not Command Prompt. If you accidentally open the wrong one, close it and open Git Bash.

If you're on macOS, skip this step — the built-in Terminal already works.

---

## Step 2: Make a Workshop Folder

Open Git Bash (Windows) or Terminal (macOS) and run:

```bash
mkdir ~/claude-workshop
cd ~/claude-workshop
```

This is the folder you'll work in for the rest of the workshop.

---

## Step 3: Start Claude

From inside `~/claude-workshop`:

```bash
claude
```

---

## Step 4: Install the Workshop Skills

Once Claude is running, paste this in **exactly** as a single message:

> Please set up this folder as a workshop folder. Steps:
> 1. Clone <https://github.com/teren-papercutlabs/pcl-workshop.git> into a subfolder called `pcl-workshop`.
> 2. Copy `pcl-workshop/templates/workshop-CLAUDE.md` to `./CLAUDE.md` here.
> 3. Copy `pcl-workshop/techniques/` to `./techniques/` here.
> 4. Create a `.claude/skills/` folder here and copy each skill folder from `pcl-workshop/skills/` into it.
> 5. List everything you set up so I can confirm it landed.

Claude will work through the list. If it asks for permission to run `git clone` or to write files, approve.

When it confirms, **exit Claude** — type `/exit` or press `Ctrl+C` twice.

---

## Step 5: Restart Claude

Skills only load when Claude starts, so the restart is required:

```bash
claude
```

(Make sure you're still in `~/claude-workshop`.)

---

## Step 6: Verify the Skills Loaded

Ask Claude:

> Do you have the `/interview`, `/solutioning`, and `/retro` skills available?

Claude should confirm all three. If any are missing, see Troubleshooting below.

---

## Step 7: Start the Workshop

Run:

```
/interview
```

Claude will walk you through capturing your problem one question at a time. The rest of the loop (`/solutioning`, then build, then `/retro`) chains automatically — you'll be prompted for each step.

---

## Troubleshooting

**`git: command not found` (Windows)**
You're in PowerShell or Command Prompt, not Git Bash. Close the window and open Git Bash instead.

**Slash commands (`/interview`, etc.) don't appear after install**
You probably skipped the restart in Step 5. Exit Claude (`/exit`), restart with `claude`, and try again.

**Claude can't `git clone` the repo**
Likely a corporate proxy. Two fallbacks, in order:
1. Ask Claude to use the GitHub CLI: *"Try `gh repo clone teren-papercutlabs/pcl-workshop` instead"*. Sometimes routes around proxy issues.
2. Download the repo as a ZIP from <https://github.com/teren-papercutlabs/pcl-workshop> (green **Code** button → **Download ZIP**), unzip it into `~/claude-workshop/pcl-workshop`, then re-run the install paste from Step 4 (Claude will see the folder is already there and skip the clone).

**Claude can't write to `.claude/skills/`**
Permissions issue. Ask Claude to show you the error, then either approve the write or paste the error to your facilitator.

**Anything weird that "looks like Claude is broken" on Windows**
First check: are you in Git Bash? PowerShell will silently mis-handle paths and pipes and Claude won't always notice. Re-open in Git Bash.

---

## Questions Before Friday

Reach out to Teren directly if anything's unclear.
