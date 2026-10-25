---
name: daily-briefing
description: >
  Ali's daily briefing: what's due on Trello today, what's open in GitHub, and what local
  work is sitting uncommitted or unpushed across the repos under ~/go/src. Use whenever Ali
  asks for a briefing, a rundown, "what's on my plate", "what do I have today", "where did I
  leave off", "morning briefing", "catch me up", "خلاصه امروز", "امروز چی دارم", or anything
  about reviewing the day's work across boards and repos. Also use at the start of a
  scheduled morning run. Read-only: it never moves a card, commits, or pushes.
---

# Daily Briefing

One picture of the day, built from three places Ali's work actually lives:

1. **Trello** — cards due today or overdue, and cards assigned to Ali that moved since yesterday.
2. **Git, locally** — repos under `~/go/src` with uncommitted changes, unpushed commits, or a
   branch that has fallen behind its remote.
3. **GitHub** — open PRs Ali authored or was asked to review (only when `gh` is installed and
   authenticated).

It's a snapshot of now, not a project plan. No backlog, no week-ahead, no advice unless asked.

## Rules that never bend

- **Read only.** The briefing reports. It doesn't move cards, commit, pull, rebase, stash, or
  push. Every suggested action goes in the 🔴 closer as a question. Ali commits and pushes when
  Ali chooses to; a push can trigger a deploy.
- **Never touch the browser.** Don't open, close, or kill Firefox or any browser process.
- **Don't fetch with side effects.** `git fetch` is fine (it only updates remote refs).
  `git pull` is not.

## Step 1: Resolve the date

Ali's Mac clock is local, so `date +%F` is Ali's today. If the session context names a timezone,
prefer it: `TZ="<zone>" date +%F`. Trello stores dates in UTC, so convert before comparing:
a card due `2026-10-27T20:30:00Z` may be "tomorrow" locally.

## Step 2: Gather, in parallel

**Trello.** Call `trelloReadMember` with `get_me` to get Ali's member id and timezone. Read Ali's
boards, then for each open board read the cards that are due on or before today, or assigned
to Ali and updated in the last 24 hours. Skip archived boards and the Inbox unless it has
dated cards. Keep each card's `url`, list name, due date, and checklist progress.

**Local git.** Find repos touched recently and check each one:

```sh
find ~/go/src -maxdepth 3 -name .git -type d -mtime -14 2>/dev/null | while read g; do
  r=${g%/.git}
  git -C "$r" fetch -q 2>/dev/null
  b=$(git -C "$r" branch --show-current)
  dirty=$(git -C "$r" status --porcelain | wc -l | tr -d ' ')
  ahead=$(git -C "$r" rev-list --count @{u}..HEAD 2>/dev/null || echo "no-upstream")
  behind=$(git -C "$r" rev-list --count HEAD..@{u} 2>/dev/null || echo 0)
  echo "$r|$b|$dirty|$ahead|$behind"
done
```

`-mtime -14` on `.git` keeps the sweep to repos with recent activity, so the ~/go/src pile of
old clones doesn't flood the report. A repo with `no-upstream` has a local branch that was
never pushed. Report that, it's work that exists on one machine only.

**GitHub.** If `command -v gh` succeeds:

```sh
gh search prs --author=@me --state=open --json repository,number,title,url,updatedAt
gh search prs --review-requested=@me --state=open --json repository,number,title,url
```

If `gh` isn't there, render the section with `gh not installed — skipped.` Don't scrape GitHub
in a browser instead.

## Step 3: Present

Format per the `skimmable-summary` skill. Write in the language Ali asked in.

```
Stat line: "N due · N open PRs · N dirty · N unpushed · N for you"
Sections, in order:
- 📌 Due today — Trello cards due today or overdue (name → card, list, checklist x/y);
  empty: "✅ Nothing due today."
- 🗂️ Moved on the board — cards assigned to Ali that changed in the last day;
  empty: "No board changes."
- 🔀 Pull requests — PRs authored or awaiting review (repo #n → PR, state);
  empty: "No open PRs."
- 🌿 Local work — dirty trees, unpushed commits, branches behind origin (path in backticks,
  branch, counts); empty: "Everything is committed and pushed."
- 🔴 Needs Your Attention [closer] — overdue cards, PRs waiting on Ali's review, branches that
  exist only locally, branches far behind origin.
Components: [verification-footer] — boards read, repos checked, 0 writes.
```

An overdue card goes in 📌 with a ⚠️ and the days overdue, and rolls up into the closer.

## When a source fails

Say so in its section (`⚠️ Trello unavailable: <error>`) and keep going with the others. A
briefing with two of three sources is still useful; a silent gap is not.
