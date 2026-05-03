# pcl-workshop

Papercut Labs workshop scaffolding for non-technical participants using Claude Code or Codex.

The workshop loop is:

1. **Disambiguate** — clarify the problem by reacting to concrete statements and short questions.
2. **Solutioning** — propose one approach and concrete verification criteria.
3. **Build** — implement against the agreed plan.
4. **Retro** — encode what was learned so the next cycle improves.

## What's Inside

Core skills:

- **`/disambiguate`** — clarification and structured discovery; writes `problem-brief.md`.
- **`/interview`** — backward-compatible alias for `/disambiguate`.
- **`/solutioning`** — proposes approach plus verification criteria; writes `plan-brief.md`.
- **`/retro`** — end-of-cycle reflection that improves the next round.
- **`/workshop-bootstrap`** — one-time scaffolder for a workshop folder.

Reference techniques:

- `techniques/no-api-workflows.md` — working with platforms that have no usable API.
- `techniques/accuracy.md` — keeping output reliable.
- `techniques/parallel-subagents.md` — parallelising independent work.

## Claude Code Install

Claude Code supports plugin-style workshop setup. If plugin marketplace access is available, install through the marketplace flow used by the facilitator.

If marketplace access is blocked, use the clone-and-copy setup:

```bash
mkdir -p ~/claude-workshop
cd ~/claude-workshop
git clone https://github.com/teren-papercutlabs/pcl-workshop.git
cp pcl-workshop/templates/workshop-CLAUDE.md ./CLAUDE.md
cp -r pcl-workshop/techniques ./
mkdir -p .claude/skills
cp -r pcl-workshop/skills/* .claude/skills/
```

Restart Claude Code from the workshop folder so it picks up the local `CLAUDE.md` and skills.

## Codex Install

Codex supports plugins through marketplaces and the Plugin Directory. The plugin payload is this repo's `.codex-plugin/plugin.json`; a marketplace file tells Codex where that payload lives.

Inside the Codex CLI, open the plugin browser with:

```text
/plugins
```

From there, browse marketplace sources, install plugins, uninstall plugins, or toggle installed plugins on/off.

This repo includes:

- `.codex-plugin/plugin.json` — the Codex plugin manifest.
- `.agents/plugins/marketplace.json` — a local marketplace entry for this plugin.

### Option A: Add This Repo As A Git-Tracked Marketplace

Add the GitHub repo as a marketplace source:

```bash
codex plugin marketplace add teren-papercutlabs/pcl-workshop
```

For a branch or pinned release:

```bash
codex plugin marketplace add teren-papercutlabs/pcl-workshop --ref <branch-or-tag>
```

Then start a fresh Codex session and open the plugin browser:

```text
/plugins
```

Choose the `PcL Workshop` marketplace, install `PcL Workshop`, then start a new Codex thread.

Useful marketplace maintenance commands:

```bash
codex plugin marketplace upgrade
codex plugin marketplace remove pcl-workshop
```

Use this option when the workshop plugin is committed and pushed. `upgrade` works because Codex can fetch the marketplace from Git. If your installed CLI does not expose `codex plugin marketplace`, use Option B below.

### Option B: Embed A Repo-Scoped Marketplace In One Project

This is the clean workshop-project setup. The project carries a local marketplace plus the plugin payload, so Codex can discover the plugin from `/plugins` when started in the project folder.

From inside the project folder:

```bash
WORKSHOP=~/Documents/Codex/pcl-workshop
mkdir -p .agents/plugins plugins/pcl-workshop
rsync -a --delete --exclude='.git' "$WORKSHOP/" plugins/pcl-workshop/
```

Create `.agents/plugins/marketplace.json`:

```json
{
  "name": "local-workshop-plugins",
  "interface": {
    "displayName": "Local Workshop Plugins"
  },
  "plugins": [
    {
      "name": "pcl-workshop",
      "source": {
        "source": "local",
        "path": "./plugins/pcl-workshop"
      },
      "policy": {
        "installation": "AVAILABLE",
        "authentication": "ON_INSTALL"
      },
      "category": "Productivity"
    }
  ]
}
```

Then restart Codex from the project folder, open `/plugins`, choose the project marketplace, and install `PcL Workshop`.

This option is intentionally local. If you update files by hand or rsync, restart Codex; `codex plugin marketplace upgrade` only applies to Git-backed marketplace sources.

For this workshop setup, Teren's project is:

```text
/Users/teren/Documents/Codex/tria-codex-demo
```

### Last Resort: Copy Skills Directly

Only use this if the installed Codex build cannot read plugin marketplaces.

```bash
PROJECT=~/Documents/Codex/tria-codex-demo
WORKSHOP=~/Documents/Codex/pcl-workshop

cp -R "$WORKSHOP/techniques" "$PROJECT/"
mkdir -p "$PROJECT/skills"
cp -R "$WORKSHOP/skills/"* "$PROJECT/skills/"
```

If the project has its own `AGENTS.md`, merge in the workshop sections instead of overwriting it:

- `Clarification Flow`
- `Local Skills`
- `Techniques`

The important line is that Codex should use `/disambiguate` when the user asks for `/interview`, clarification, or problem scoping.

### Start Codex From The Project Folder

```bash
cd ~/Documents/Codex/tria-codex-demo
codex
```

Prefer Option A for reusable installs across projects; use Option B for a self-contained workshop project; use direct skill copying only when marketplace support is missing.

## Start A Workshop Cycle

After restarting inside the workshop folder, begin with:

```text
/disambiguate
```

`/interview` remains available as an alias for older instructions, but new workshop material should teach `/disambiguate`.

## Windows Note

On Windows, use Git Bash rather than PowerShell or Command Prompt. The workshop skills assume bash-style paths and quoting.

If Git Bash is missing, install it from <https://gitforwindows.org/>.

## Troubleshooting

**Slash commands or skills don't appear after install**

Restart the agent from the workshop folder. Skills and project instructions are loaded at session start.

**Clone fails**

Try the GitHub CLI:

```bash
gh repo clone teren-papercutlabs/pcl-workshop
```

If that also fails, download the ZIP from <https://github.com/teren-papercutlabs/pcl-workshop>, unzip it into the workshop folder, and repeat the copy steps.

**Codex does not expose plugin commands**

Use the Codex clone-and-copy setup above. `codex mcp` is for external MCP servers, not skills/plugins.
