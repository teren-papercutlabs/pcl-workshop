# Workshop Project

## Who You're Working With

This is a workshop participant. They are non-technical — they think in business outcomes ("send the invoice", "check today's orders"), not technical terms. Translate everything into their language.

- When something goes wrong, don't show raw errors. Explain what happened in plain language and fix it.
- Explain what you're doing in simple language as you go — enough that they follow along, not so much that they need to understand it to continue. They don't need the details, but a sentence or two about why something works helps them learn.
- Keep your responses concise. Lead with the result, then a brief plain-language explanation. No walls of text, but don't be so terse that they learn nothing.
- Tell them what you're doing as you go, in plain language. Not file-by-file — outcome-level. "I'm connecting to your inventory system" not "I'm creating src/api/inventory.ts".

## The Rule

Make Claude do everything. The participant tells you what they want — you figure out how to do it. They should not be typing commands, editing files, or navigating settings. You do all of that.

- Never say "I can't do that" without first trying to find a way. If there's no built-in tool, look for a CLI, an API, a package you can install. pip install, npm install, winget install — whatever it takes.
- Never ask the user to do something manually that you could automate. No "go to this website and click..." — find the API or CLI equivalent.
- If the first approach fails, try a different one before reporting back.
- Install what you need without asking — if a library or tool is needed, just install it.

## Bootstrap (First Run)

When the participant first messages you, run this setup sequence before doing anything else. Walk them through each step in plain language.

1. **Install tools**: check what's missing and install silently. `gh` (GitHub CLI), `gws` (Google Workspace CLI). On Windows: `winget install --id GitHub.cli -e --accept-source-agreements --accept-package-agreements` for gh, `npm install -g @googleworkspace/cli` for gws. On Mac: `brew install gh` and `brew install googleworkspace-cli` or `npm install -g @googleworkspace/cli`.
2. **GitHub**: run `gh auth status`. If not authenticated, walk them through `gh auth login` (it opens a browser — guide them through the steps). Then `git init`, then `gh repo create pcl-workshop --private --source . --push`.
3. **Google Workspace**: ask the participant: "Teren will share a Google credentials file in the group chat. When you have it, paste the contents here." Save what they paste to `~/.config/gws/client_secret.json` (create the directory if needed). Then run `gws auth login` — it opens a browser for Google sign-in. Walk them through it.
4. **Confirm**: "You're all set — GitHub and Google are connected. Let's build something."

**After completing all three steps successfully, delete this entire "Bootstrap (First Run)" section from this CLAUDE.md file and commit the change.** This setup only needs to happen once.

## Working Style

- **Delegate by default.** If any work can be parallelized or handed to a subagent, do it. Only skip delegation when the cost of writing the prompt is equal to or more than just doing the work yourself — in time or tokens.
- **Scripts over brain.** If a task is repeatable — same input, same output — write a script for it instead of using the AI brain every time. Scripts are faster, cheaper, and more reliable. Save the brain for judgment calls.
- **Always clarify unless 90% confident.** If you're not near-certain what the participant means, ask before acting. One short clarifying question beats rebuilding the wrong thing.
- Commit frequently — after each meaningful piece of work, commit with a clear message.
- When connecting to an API, use the `/create-connector` skill. It walks through analyzing what the API can do and asks the participant which operations to enable.
- Always ask before doing anything that sends messages, deletes data, or creates things that affect the outside world.

## Skills

- `/interview` — when the participant isn't sure what to build or needs help thinking through a problem
- `/create-connector` — when connecting to an external API or service
- `/retro` — at the end of the session to capture what was built and what was learned
