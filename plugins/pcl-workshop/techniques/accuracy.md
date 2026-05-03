# Accuracy

Claude can produce output that *looks* correct but isn't. A non-technical participant can't always tell the difference. These are the practices that keep output reliable.

## When to Use This

The participant is asking about trust — "how do I know it's right?", "can I rely on this?", "what if it hallucinates?" — or you notice yourself producing plausible-looking output without concrete grounding.

## Core Principles

### 1. Verification Criteria Are Non-Negotiable

The plan-brief has verification criteria for a reason. Before declaring build-done, **run through each criterion literally**. Don't eyeball the output.

- "When I do X, I should see Y" → actually do X, actually observe Y.
- If the criterion references a specific value, check the specific value.
- If the criterion is about absence ("cancelled orders should not appear"), actively verify absence — filter the output, confirm zero.

If a criterion is hard to verify mechanically, re-shape it until it's testable. "The code should be clean" is not verifiable. "The summary should list at most 20 items" is.

### 2. Ground in Real Data, Not Examples

When working out a transformation or a data shape, use the participant's actual data (or a realistic copy). Don't infer from example snippets in documentation.

- Docs describe the API's schema in theory.
- Real data shows what the API actually returns for this account, this configuration, this edge case.

If the real data differs from the docs — trust the real data. Update your understanding.

### 3. Fetch, Don't Imagine

If something is observable (an API's response shape, a library's function signature, a file's structure), fetch it or test it. Don't write code based on what you think it should look like.

- `curl` the endpoint.
- Run the function in a REPL.
- `head` the file.
- Read the actual response.

A 2-second check beats 10 minutes of wrong code.

### 4. Test Before You Say Done

"Done" requires a literal test run, not a code review. Whatever the artifact is:

- Script → run it on real input, observe output.
- CLI tool → invoke it, check exit code and output.
- Automation → trigger it end-to-end, check the destination.
- Report → read the report yourself, check numbers.

Compile-passes and type-checks-pass are plumbing checks, not behavior checks. They're necessary but never sufficient.

### 5. Test What the Participant Will See

If the participant will see it in a spreadsheet, test it in a spreadsheet. If they'll see it in an email, render the email. If they'll see it in a dashboard, load the dashboard.

HTTP 200 and "build succeeded" don't prove the thing works. They prove the plumbing works.

### 6. Checkpoints During Long Work

If a task takes more than a few tool calls, checkpoint:

- After major step → summarise what just happened, confirm it matches expectations.
- Before each irreversible action → confirm.
- After each verification criterion runs → record pass/fail.

Quiet tool-loops are where errors compound silently. Checkpoints catch drift early.

## Consulting This Technique

When the participant asks about reliability, guide them through the principles that apply to their situation:

- **Building something new?** → Point at criteria-first. "Before we build, let's lock what 'done' means. Then we can check."
- **Something went wrong?** → Point at fetch-don't-imagine + real-data grounding. "Let me check what the data actually looks like — I think I made a wrong assumption."
- **Wants confidence in a finished thing?** → Run the verification criteria literally, in front of them.

Don't recite the whole technique. Pick what applies.
