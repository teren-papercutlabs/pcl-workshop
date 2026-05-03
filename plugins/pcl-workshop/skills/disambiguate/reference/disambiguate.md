# Disambiguate — Full Protocol

## why this works

people struggle to articulate requirements from scratch. given an empty prompt ("what do you want?"), they produce vague answers or go blank. given a concrete statement to react to, they immediately know whether it resonates.

this is recognition over recall. the technique exploits it deliberately.

## statement generation rules

**what makes a statement good**

- specific enough to be wrong. "this saves me time" is bad — who would say no? "this works best for people with one specific recurring problem, not general exploration" is good.
- one claim per statement. don't bundle.
- opinionated. if you could imagine the person saying "I hadn't thought about it that way", the statement is doing work.
- distinct from the other statements in the batch. four statements that all say "this is simple" waste rounds.

**what makes a statement bad**

- wishy-washy ("this might be useful for...")
- universally agreeable ("this should be reliable")
- compound ("this is fast AND beautiful AND easy")
- jargon the user might not share

## statement types and when to use them

**functional** — what the thing does / produces
use these first. ground the exercise in concrete outcomes.
> "at the end of this ritual, I know exactly what I accomplished today and what carries over to tomorrow"
> "this gives me a way to close the workday that doesn't require willpower"

**emotional** — how using the thing feels
use these in round 1-2 to surface tone and register.
> "this feels like a clean sweep, not a report"
> "using this makes me feel like I'm in control, not just catching up"

**anti** — what the thing is not
use these when you have positive signal but the shape is still blurry. often produce stronger signal than positive statements.
> "this is NOT about tracking productivity — I don't want numbers or metrics"
> "this is not a meeting prep tool. that's a different problem"

**trade-off** — explicit prioritization
use these in round 2-3 when you have two competing directions and need to force a choice.
> "I'd rather have a ritual that takes 5 minutes consistently than one that takes 15 minutes but feels thorough"
> "I'd rather it feel personal and a bit rough than polished and generic"

## running the exercise — step by step

### before you start

read any context the user has given. if they described the thing at all, use that as raw material. don't generate generic statements — anchor them to what you already know.

### step 1: frame (1 sentence)

state what you're disambiguating. this creates shared vocabulary for the exercise.

> "let's figure out what your end-of-day ritual actually needs to be"

don't explain the technique at length. just start.

### pre-step: figure out the altitude

before generating any statements, determine where to start. three levels:

- **why** — the underlying need. start here when the user has a fuzzy sense that they need something but hasn't articulated the problem yet.
- **shape** — what the solution feels like. start here when the problem is clear but the form of the solution isn't.
- **specifics** — features and mechanics. start here only when both problem and shape are already established.

**default: start at "why."** let responses pull you down to shape, then specifics. jumping to specifics before "why" is clear produces statements the user can't react to meaningfully — they don't yet know whether those specifics matter.

### step 2: statements (mode B default)

**mode B (default) — one at a time:**

present one statement. user reacts on a scale: strongly disagree / disagree / agree / strongly agree. after each response, summarize the signal in one line, then present the next statement.

```
react: strongly disagree / disagree / agree / strongly agree

"the reason i want an EOD ritual is that by the end of the day my head is full of half-finished threads and i can't tell which ones matter anymore"
```

**mode A — batch of 4 (alternatives mode):**

use only when narrowing between known competing directions. present 4 mutually exclusive statements and ask the user to pick the one that resonates most.

mode A is not the default. it's for late-stage narrowing, not early-stage exploration.

### step 3: read the signal

after each response, extract what's confirmed and what's still open. state this in one line before presenting the next statement:

> "strong signal: the thread-loss problem is real. open: whether the solution is about capturing threads or about judgment over them."

then generate the next statement targeting the open question. use anti and trade-off statements to force sharper choices.

### step 4: converge

when you can answer "what does this thing need to do and what does it explicitly not need to do?" — you're done. one-at-a-time mode typically takes 4-8 statements.

produce the design brief (see below).

## design brief format

title it: "what [thing] needs to be"

**the core** — one sentence. what is this fundamentally?

**it must** — 3-5 bullet points. non-negotiable functional requirements based on confirmed signal.

**it must not** — 2-4 bullet points. explicit exclusions based on strong-no or anti-signal.

**the feel** — one sentence. emotional register.

**open questions** — anything that didn't resolve. 0-3 items. if there are none, the exercise succeeded.

---

## example: designing kleya's eod ritual (real exercise, one-at-a-time mode)

this is a real exercise. it demonstrates starting at "why" altitude and descending to shape.

### frame

> "let's figure out what your end-of-day ritual actually needs to be"

### statement 1 (why altitude)

> react: strongly disagree / disagree / agree / strongly agree
>
> "the reason i want an EOD ritual is that by the end of the day my head is full of half-finished threads and i can't tell which ones matter anymore"

**response:** strongly agree

**signal read:** the core problem is thread-loss and signal-noise — not closure or rest. this is an organizational clarity problem, not a psychological one.

### statement 2 (why — testing the transition framing)

> "part of what makes the end of day hard is that i don't have a clean transition — work just kind of bleeds into evening"

**response:** disagree — not hard, just stuff gets lost

**signal read:** transition is not the problem. the problem is information loss and lack of prioritization. confirmed: stay at "why" for one more round.

### statement 3 (shape — testing pure mirror vs judgment)

> "if someone could just show me a list of everything i said and decided today, that alone would be enough"

**response:** agree — mirror is necessary but not sufficient, wants judgment on top

**signal read:** pure mirror isn't enough. needs CoS judgment over the mirror. descending to shape.

### statement 4 (shape — testing whose judgment)

> "what i actually want is for kleya to tell me what she thinks the most important thing from today was"

**response:** agree — not instruction, more like "this thread could be impactful, lock it in"

**signal read:** not prescriptive direction — more like "flag what's at risk of being lost." the judgment is organizational, not personal.

### statement 5 (shape — testing the feel)

> "after a good EOD session, i'd feel like someone else is holding the picture"

**response:** agree — not personal relief, organizational confidence that PcL is on top of things

**signal read:** the outcome is organizational situational awareness, not personal peace of mind.

### statement 6 (shape — testing completeness vs switching off)

> "if the EOD told me everything is accounted for, i'd close my laptop and not think about work"

**response:** disagree — not about switching off, just completeness, nothing evaporated

**signal read:** the need is organizational completeness, not personal decompression. clear enough to brief.

### design brief

**what kleya's EOD ritual needs to be**

the core: a brief EOD session showing everything that happened across PcL, with CoS judgment on what's at risk of being lost.

it must:
- mirror back all threads and decisions from the day across the whole org
- include kleya's judgment on what matters and what's at risk
- cover the whole org, not just one person's day
- be brief — a scan, not a report

it must not:
- feel like a productivity report
- try to create a work/life boundary or switch-off moment
- summarize without opinion

the feel: organizational situational awareness. "we are on top of shit."

open questions: none — signal was sufficient.

---

## altitude mistakes

the most common error: starting at specifics before "why" is clear.

**what it looks like:** you generate a statement like "the main thing the EOD does is confirm the system heard me" (a specifics-level claim about a feature) before understanding why the user needs an EOD at all. the user reacts to it, but the signal is noisy — they're reacting to an imagined implementation, not the underlying need.

**what happened in the real exercise:** the first statement attempted was "the main thing the EOD does is confirm the system heard me." the user couldn't react cleanly — they hadn't yet articulated whether the problem was thread-loss, missing transition, personal closure, or something else. the exercise restarted at "why" altitude with "the reason i want an EOD ritual is..." and immediately produced very strong signal.

**the rule:** if you find yourself writing a statement that describes what the thing *does* before the user has confirmed *why they need it*, you're at the wrong altitude. back up.

---

## format vs content — hold one variable constant

when the open question is about FORMAT or STRUCTURE — envelope shape, field order, section breakdown, visual layout — use the same situation across the comparison. do not also vary the content.

if you show format A on situation X and format B on situation Y, the user's reaction is noise — they can't tell whether they're reacting to the format difference, the content difference, or both. apples-to-apples only.

this is mode A territory (narrowing between known alternatives). pick one concrete situation, render it in 2+ formats, let the user pick the format.

**what it looks like wrong:** agent shows 3 shapes (simple/decision/ambiguity) in tight 4-part format, then 2 of those situations in an expanded format. user has to say "show me the same situation in two different formats" to get usable signal.

**what it looks like right:** agent picks one situation (e.g., a real decision from the user's current open loops), renders it in tight format and expanded format back-to-back, asks which format resonates.

**incident: 2026-04-23, /unblock skill design** — agent varied both format and situation; teren had to redirect explicitly. same rule applies to /disambiguate itself — this section added afterward.

---

## convergence heuristic

you have enough signal when:
- you can write the "it must" list without guessing
- you can write the "it must not" list without guessing
- you know the emotional register

you don't have enough signal when:
- two confirmed items seem to conflict
- a "kinda" response has been repeated across two batches on the same topic
- the user's language has shifted (they're using different words for the same thing)

if you're not sure, do one more round with 3-4 statements targeting the remaining ambiguity. don't produce the brief until the core is clear.
