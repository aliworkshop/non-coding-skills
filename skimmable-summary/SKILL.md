---
name: skimmable-summary
description: >-
  Ali's house format for any multi-item summary, digest, briefing, status report,
  roundup, or staged plan/roadmap meant to be skimmed. Use whenever Claude presents
  several items across categories: daily briefings, "give me a rundown," "catch me
  up on X," "what happened on the board," "summarize these PRs / branches / repos,"
  standup or weekly updates for the team, research roundups, sync results. Render
  as: a dated H1, a one-line count dashboard, emoji-headed sections with
  one-sentence linked items, every section always shown with an empty-state line,
  and a "🔴 Needs Your Attention" action closer. This is the DEFAULT presentation
  for digests to Ali; apply it even when no format is named, and especially when
  asked to make something "easier to skim" or "shorter." When a task supplies its
  own section map, keep this frame with those sections. Do NOT use for single
  facts, one-item lookups, conversational replies, code, or long-form prose
  (reports, essays, letters, docs).
---

# Skimmable Summary

Ali's house style for turning a pile of gathered information into something readable in ten
seconds. A summary answers two questions before any detail: *how much is here* and *what needs
me*. Everything below serves that.

The format is a fixed **frame** with a swappable **middle**. The frame (title, count dashboard,
the rules for items, the action closer) never changes. The middle sections are whatever the
situation calls for. So a daily briefing, a repo status sweep, and a "catch me up on the board"
all look like siblings even though their sections differ.

## When this applies (and when it doesn't)

Use it for any digest of **multiple items across categories** that Ali will skim, whether a
format was asked for or not. It's the default.

Don't use it for a single fact, a one-item lookup, a normal conversational reply, code, or
long-form prose. Forcing a dashboard onto a one-line answer is worse than not having one. If
unsure, ask whether the reader would scan or read it. Scan means use this; read means don't.

A **plan or roadmap** meant to be skimmed takes this frame too. Its sections are the stages,
its items are considerations and next actions, and it ends with the same 🔴 closer for what
has to be decided next. A narrative write-up of the same plan does not.

## Language

Write the summary in the language Ali asked in. A Persian request gets a Persian summary:
same frame, same emoji, same markers, Persian labels (`🔴 نیاز به تصمیم شما`,
`✅ چیزی نیاز به توجه ندارد`). Keep proper nouns, repo names, branch names, and ticket titles
as they are; don't translate identifiers. Weekdays and dates follow the language
(`# خلاصه روز — سه‌شنبه ۴ آبان` vs `# Daily Briefing — Tue, Oct 26`).

## The frame

```
# <Title> — <Weekday, Mon D>

<count · count · count>

🔵 **<Section A>**
- <one-sentence item, name → source link>
- <empty-state line>

🔵 **<Section B>**
- …

🔴 **Needs Your Attention**
- <linked name — short context clause — **one decision-ready question?**>
```

Top to bottom: a dated **title**, a one-line **count dashboard**, the **informational
sections** (what happened, what's due, what's coming), and the **action closer** last. The
last thing Ali reads should be the thing to act on.

## The rules (these never change)

- **Title is a dated H1.** `# <Name> — <Weekday, Mon D>`. No emoji in the title.
- **Stat line is a one-line dashboard.** Counts joined by ` · `, on its own line, with a blank
  line above and below. Pick 3-5 counts that matter here; always include the count of closer
  items (`… · 2 for you`).
- **One sentence per item, most important thing first.** Lead with the name or the action,
  then the context. If a line needs two sentences, it's two items or it's too detailed.
- **Names are links, never bold.** Each card, PR, branch, commit, doc, or thread links to its
  source (Trello card, GitHub PR, Claude Doc). The summary is a launchpad. Links must point to
  something that exists. A local branch or a dirty working tree has no URL, so write its path in
  backticks instead of inventing a link.
- **Closer items are asks, not findings.** Every 🔴 item reads: linked name → short context
  clause → **the one concrete question**, bolded, at the end. The question is answerable in one
  sentence ("merge it?", "push the branch?", "move the card to Done?"). If an item can't be
  phrased as a question, it's an FYI: move it to a record section. Bolding the question is the
  one exception to the never-bold rule.
- **Every section always renders, with an explicit empty-state line.** A quiet day reads as
  cleanly as a busy one.
- **Record first, action last.**

## Marker legend (fixed meaning)

- 🔴 needs you (the closer; also an inline prefix on an item that needs review)
- ⚠️ caution / judgment call
- ✅ / ✓ clean / done / verified
- ⏭️ skipped
- 📌 due
- 📅 upcoming
- 🧹 cleanup chore

Section-topic emoji (🔀 PRs, 🌿 branches, 🗂️ cards, 🚀 releases) are free to fit the domain. The
legend is only for the status markers that recur.

## House conventions

- **Bullets:** `-`. Not `*`, not `•`.
- **Section headers:** emoji + bold label, `🔵 **Section**`. Not `##` headings.
- **The closer is named** `🔴 **Needs Your Attention**` **only when it has items.** When empty,
  the whole section collapses to the single line `✅ Nothing needs attention`.
- **Stat line** is plain counts joined by ` · `, no per-count emoji.

## Components (opt-in)

- **`[closer]`** — always present, always last. Empty-state: `✅ Nothing needs attention`.
- **`[consolidated-link-line]`** — when several closer items share one kind of follow-up, put
  them on one line: `Review PRs: [#41](url), [#43](url)`.
- **`[verification-footer]`** — for syncs and sweeps, a final `✓ Verification: …` line saying
  what was cross-checked and how many writes were made.
- **`[table-section]`** — when one section is ranked or tabular, render it as a table. The frame
  still wraps it.
- **`inline-marker`** — prefix a record item with 🔴 or ⚠️ when it also needs attention, then
  roll it up in the closer.

## Section-map contract (for codified tasks)

A scheduled task or another skill shouldn't restate these rules. It points here and declares
only **its sections**: emoji + label · what populates it · empty-state line, plus the stat-line
tokens and any components. For example:

```
Format per the skimmable-summary skill. Stat line: "N due · N moved · N open PRs · N for you".
Sections, in order:
- 📌 Due today — cards due today (name → card); empty: "✅ Nothing due today."
- 🔀 Pull requests — open PRs across repos; empty: "No open PRs."
- 🌿 Local work — dirty trees and unpushed branches; empty: "Everything is pushed."
- 🔴 Needs Your Attention [closer]
Components: [verification-footer].
```

## Default body (ad hoc)

With no section map ("catch me up on the echoserver repo"), group items into 2-4 natural buckets,
informational first, closer last. A good default for "what happened" content is
🆕 New / 🔄 Updates / 🔴 Needs Your Attention.

## Authority

The default presentation for any multi-item digest to Ali. When a task supplies a section map,
the map decides *which* sections and this skill decides *how* they render. It composes with
content skills: they gather the data, this skill shapes the summary.

## Worked example

```
# Daily Briefing — Tue, Oct 27

3 due · 2 open PRs · 1 unpushed · 2 for you

📌 **Due today**
- [Release notes for dbcore v1.4](https://trello.com/c/…) — draft is written, changelog still missing.

🔀 **Pull requests**
- [dbcore #46](https://github.com/aliworkshop/dbcore/pull/46) — keyset paging, approved, CI green.

🌿 **Local work**
- `~/go/src/aliworkshop/echoserver` — branch `feat/sse` is 3 commits ahead of origin.

🔴 **Needs Your Attention**
- [dbcore #46](https://github.com/aliworkshop/dbcore/pull/46) — approved and green — **merge it?**
- `echoserver` `feat/sse` — 3 commits only on this machine — **push the branch?**

✓ Verification: read 2 boards and 14 repos; 0 writes made.
```
