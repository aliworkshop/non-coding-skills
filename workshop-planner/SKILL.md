---
name: workshop-planner
description: >
  Plan a technical workshop, course session, talk, or tutorial series for developers: pick
  the use cases, sequence the steps, design the staged failures, and write the session
  outline and README narrative. Use when Ali is preparing a session of an AI engineering
  course, porting a workshop to Go, giving a talk on a Go library, or teaching a team a
  tool. Triggers: "plan the next session", "outline this workshop", "what should the demo
  be", "how do I teach X", "break this into parts", "write the session README", "یه ورکشاپ
  برای X طراحی کن". Not for writing the code itself — this plans what to build and how to
  tell it.
---

# Workshop Planner

Ali teaches the way the code should be built: from nothing, one step at a time, each step
fixing a problem the previous one left visible. A good session is a story with a failure in
the middle, not a tour of features.

## Phase 1: Context

Get these first (one question if anything is missing):

- **Audience**: who, their level (junior Go devs? backend engineers new to LLMs?), and what
  they already have running from earlier sessions.
- **Outcome**: the one thing attendees can do afterwards that they couldn't before.
- **Format and time**: live or recorded, length, hands-on or demo.
- **Constraints**: language (Go, or porting from another language), dependencies allowed,
  API keys attendees will have, the previous session's branch to build on.

If there's an earlier session, read its README and code first. The new session starts exactly
where that one stopped.

## Phase 2: Find the problem worth teaching

List 3-5 candidate topics. For each, name the **failure it fixes**, the thing that visibly
breaks without it. Use web research to ground them: the official docs, a well-known
production incident, a respected post. Link sources.

Score each candidate:

| | Visible failure? | Fits the time? | Builds on last session? | Small code? |
|---|---|---|---|---|

Pick the one with a failure attendees can trigger themselves. If nothing breaks without it,
it's a footnote, not a session.

## Phase 3: Sequence the steps

Each step is a small, runnable increment. One commit per step, and each commit builds on its
own.

```
Step N — <name>
  Problem left by step N-1: <one line>
  Change: <the smallest change that fixes it>
  Demo: <command to run, what attendees see>
  Still broken: <what this step deliberately doesn't fix — the hook for N+1>
```

Rules:
- **Stage failures on purpose.** Give the program a flag that makes it break the way you want
  to talk about (`-crash-at 2`, `-sandbox`). Attendees should see the failure before the fix.
- **Minimum dependencies.** Every dependency is something attendees must install and trust.
  Justify each one in a line.
- **One new idea per step.** If a step introduces two concepts, split it.
- **Name what's still broken at the end.** That's the reason to come to the next session.

## Phase 4: Write the session README

Follow `writing-style`. The shape that works:

1. One line on what this is and what branch it lives on, with links to the other branches.
2. How to run it: one code block, every flag explained in a trailing comment.
3. Real output from a run, trimmed.
4. A **before / now** table: each failure from the last session and its status now, honestly
   (including "still true").
5. One section per new idea, each starting from the problem.
6. What's next.

## Phase 5: Hand-off checklist

- [ ] Each step's commit builds and runs on its own (`git rebase --exec` it).
- [ ] The previous session's branch is untouched.
- [ ] Every demo command in the README was actually run, and its output pasted, not imagined.
- [ ] Slides or a talk outline, if needed: one slide per step, the failure on the slide before
      the fix.

Branching, committing, and pushing are Ali's call. Plan them in the outline, don't do them.
