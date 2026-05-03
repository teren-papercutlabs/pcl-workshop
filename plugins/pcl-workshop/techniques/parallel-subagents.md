# Parallel Subagents

When a task splits into independent pieces, running them in parallel via subagents is dramatically faster than doing them sequentially. This is one of the biggest speedups available in Claude Code.

## When to Use This

The participant is asking about speed — "this is taking forever", "can we go faster?", "do we have to do these one at a time?" — or you notice yourself about to do three independent things sequentially.

The test: **can two tasks run at the same time without depending on each other's output?** If yes, parallelize.

## How It Works

Claude Code supports spawning subagents via the Task tool. Each subagent is an independent Claude session with its own context — you write a prompt, it runs, it returns a result.

- **You (the main session)** stay the orchestrator. You delegate, wait for results, integrate.
- **Subagents** do bounded work, report back, terminate.

Multiple subagents can run concurrently. One main + N parallel subagents = ~N× speedup on independent work.

## Patterns

### 1. Parallel research

The participant asks "check these five platforms for X". Five independent lookups.

- Sequential: 5 × time-per-lookup.
- Parallel: 1 × time-per-lookup (all five run concurrently).

Delegate each lookup to a subagent. Collect results. Synthesise.

### 2. Parallel file operations

Rewriting three independent files. Each file change doesn't depend on the others.

- Delegate each file rewrite to its own subagent.
- Check results, commit.

### 3. Parallel explore + build

While you build file A, a subagent investigates the shape of API B. When it returns with the API shape, you weave it into your code.

Orchestrator continues while investigation runs. Zero wasted time.

### 4. Parallel verification

Running three verification checks (does the output file exist, does it have the right shape, does it match the criteria). Dispatch all three as quick subagents, wait for the collective verdict.

## When NOT to Parallelize

- **When tasks depend on each other's output.** Sequential is mandatory.
- **When parallelism costs more than it saves.** One short file read isn't worth a subagent.
- **When the prompt for each subagent is as much work as just doing the thing.** Judgment call.

## Consulting This Technique

When the participant asks about speed, show them:

1. **Identify the split points.** "We've got three things to do — they're independent. I'll run them in parallel."
2. **Dispatch concurrently.** Multiple Task tool calls in a single message.
3. **Wait for the callback.** Don't poll. Subagents notify when done.
4. **Integrate the results.**

They may not need to understand the mechanics. What they need to see is: "This would have taken 15 minutes sequentially. I did it in 5 by running three things at once."

## Key Principle

**Delegate by default.** The main session's job is orchestration and integration. Implementation and investigation go to subagents wherever possible. The ceiling on how fast this workshop can move is set by how aggressively you parallelize.
