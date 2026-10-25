---
name: newsletter-writer
description: Draft newsletters and long channel posts for Ali's audience, in English or Persian, on whatever platform carries them (an email list, Substack, a Telegram channel). Use whenever Ali asks to write, draft, edit, or repurpose a newsletter — "write a newsletter", "draft this week's send", "turn this post into a newsletter", "post this to the channel", "یه پست برای کانال بنویس", "the next email to my list", or any reference to writing for subscribers. Also trigger when Ali shares a topic, a release, a lesson, or a LinkedIn post and asks to "make it a newsletter" or "send it to the list". Covers teaching, observation, and launch/sell sends — for deep conversion diagnosis on a sell send, hand off to `conversion-copy` after the draft exists.
---

# Newsletter Writer

Ali's skill for drafting sends to subscribers: Go and backend lessons, open-source releases
under `aliworkshop`, AI engineering, and product launches. The base voice is the
`writing-style` skill. This skill adds the structure of a send.

> TODO(ali): fill in the facts this skill can't guess, then delete this note:
> - Platform(s) and list: email (which tool?), Substack, Telegram channel name, or several.
> - Audience: who subscribes (Go developers? Persian-speaking engineers? founders?) and roughly
>   how many. Don't let Claude state a number until this is filled.
> - Sign-off: the exact closing line you want (e.g. "-Ali", "Happy building, Ali", "ارادتمند، علی").
> - 2-3 past sends you're happy with, pasted into `references/past-sends.md`, so the voice can be
>   checked against real examples.

## Before drafting

Lock these:

- **Platform**: email/Substack (subject + preview + body) or Telegram channel (no subject; the
  first line is the hook, ~1024 characters if it carries an image, ~4096 otherwise).
- **Language**: English or Persian. Write natively in the chosen one (see `bilingual-copy`).
- **Mode**: teaching, observation, or launch/sell. It decides the template and the P.S.
- **One core idea.** Two ideas are two sends.
- **Source material**: the post, release notes, PR, README, or rough notes. Lean on Ali's own
  words; they're closer to the voice than anything invented.
- **Length**: 250-450 words for email; Telegram posts shorter, 80-250 words.

If any of these is unclear, ask before drafting.

## Voice

- **Cold open.** No "Hey friends" or "سلام دوستان". Open with the claim, the scene, or the problem.
- **One thought per line.** Short paragraphs, heavy whitespace.
- **Declarative, not coaching.** State it and move on. No "don't worry, you've got this".
- **No hype words**: unleash, supercharge, transform, empower, leverage, revolutionary,
  game-changing, seamless, robust.
- **Specific over vague.** The library, the function, the number, the version. "`v1.4` adds
  keyset paging" beats "a big performance update".
- **Real numbers only.** Benchmarks, stars, users, latencies come from Ali. Never invented.
- **No em dashes.** Commas, periods, or parentheses.
- **First person.** "I" and "you". Not "we" unless it's a team.

## Subject lines (email)

- **Curiosity gap (ellipsis)** — for personal or contrarian sends: *"I deleted the cache…"*
- **"How I / How to"** — for teaching: *"How I made an agent survive being killed mid-task"*
- **Concrete contrast** — for launches and results: *"[real before] → [real after] with one index"*

No emoji, all-caps, or urgency theater in subjects. When unsure between two, offer both with a
reason.

## The two templates

### 1. Framework send (most common)

Teaching a process, a set of lessons, or steps.

1. **Cold open** — 1-3 short lines: the problem, the credibility, or the contrarian observation.
2. **Reframe** — the "not X, but Y" pivot, often marked with `└→` or `→`.
3. **Numbered steps or lessons** — 3-5. Each: a title and 1-3 short paragraphs.
4. **Close** — a summary line, optionally a question that invites replies.
5. **Sign-off** — Ali's line (see TODO).
6. **P.S.** — a single CTA.

Example openers (rhythm, not facts to reuse):
- *"The agent crashed halfway through a refund. When it came back, it refunded again."*
- *"Every Go service I've shipped ended up needing the same four things by month two."*

### 2. Observation send

A trend or pattern from work, code review, or conversations.

1. **Cold open** — names the trend or contrast.
2. **Grounding** — where Ali saw it ("Three PRs this month made the same mistake…").
3. **Concrete examples** — usually 3 short paragraphs, each a specific role or repo and what
   happened. Anonymize anything from work.
4. **Implication** — often a triplet of short parallel sentences.
5. **Question hook** (optional).
6. **Sign-off** and **P.S.**

## Signature moves (use 2-3 per send)

1. **The reframe** — "It's not about the ORM. It's about seeing the query it writes."
2. **Notation** — `└→` for the key insight; `→` for flows ("request → event log → replay").
3. **Self-deprecating credibility** — "Not because I'm clever, but because I broke it first."
4. **"Pro tip:" asides** — "Pro tip: `EXPLAIN ANALYZE` before you add the index, not after."
5. **Parenthetical emphasis** — "a (very) small change".
6. **Triplet rhythm** — "No new service. No new queue. One table."
7. **Code, briefly** — email can carry a short code block; a Telegram post gets one line in
   backticks at most and links to the repo for the rest.

## P.S. (always present, always one CTA)

- **Free resource** (default): the repo, the release notes, a video, the course branch.
- **Soft offer**: a beta invite, a waitlist, a consulting slot.
- **Hard sell**: price, real scarcity, link. Only for dedicated launch sends.

The P.S. extends the send's value; it doesn't open a new topic.

## Telegram channel posts

- First line is the hook; it shows in the notification preview.
- Bold sparingly for the one line that matters; Telegram supports `**bold**` and inline code.
- One link, at the end. Long link previews push the text down; disable the preview if the link
  isn't the point.
- Persian channel posts: correct ZWNJ, Persian punctuation, and keep technical terms that
  engineers actually use in Latin script.

## Output 2-3 versions of the opener

Offer 2-3 opener variants at different angles (problem, credibility, contrarian), say which
you'd pick and why. One strong draft for the rest, with alternates for the load-bearing lines
(the reframe, the close, the P.S.).

## Things to avoid

- Greetings, "Best," / "Warm regards," — never.
- Hype words, generic claims without a name or a number.
- More than one offer per send; an empty P.S.
- Walls of text.

## Handoffs

- **Sell-send diagnosis** → `conversion-copy`.
- **LinkedIn posts** → `linkedin-voice`.
- **One-to-one email** → `email-helper`.
- **Long-form sales letter for a paid offer** → `sales-letter-writer`.
- **Persian/English localisation of a finished send** → `bilingual-copy`.
- **Tracking sends on a content board** → `sfc-helper` / `trello-helper`.

## Worked example: repurposing a post into a Framework send

**Source post (raw):**
> My agent used to redo work after a crash. Now every model turn and tool call is a checkpointed
> step, and a restart replays them from disk. Four pieces: event log, step ids, replay, idempotent tools.

**Draft:**

> **Subject:** How I made an agent survive being killed mid-task
> **Preview:** It's not retries. It's a log.
>
> My agent crashed halfway through a support ticket.
>
> When it came back, it emailed the customer again.
>
> The fix wasn't more retries. It was writing down every step before taking the next one.
>
> └→ If the work is in a log, a restart is a replay, not a redo.
>
> Here are the 4 pieces.
>
> **1. An event log**
> Every model turn and tool call is an event, appended to a file before anything else happens.
>
> **2. Step ids**
> Each step gets a stable id, so a replay knows what already ran.
>
> **3. Replay on start**
> On restart, read the log and skip every step that completed. Resume at the first one that didn't.
>
> **4. Tools that are safe to run twice**
> The one step that crashed mid-flight might run again. Make sure that's harmless.
>
> No new service. No queue. One file and a rule.
>
> What's the worst thing your agent has done twice? Hit reply.
>
> [Ali's sign-off]
>
> **P.S.** The full Go code is on the course branch: [link].

## One last thing

A newsletter lands in a personal inbox or a phone notification. Brands don't belong there. If a
draft sounds like a marketing system wrote it, rewrite it until it sounds like Ali explaining
one thing to one engineer.
