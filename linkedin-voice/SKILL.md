---
name: linkedin-voice
description: >-
  Ali's LinkedIn writing voice, in English or Persian. Load this skill EVERY time you draft,
  edit, rewrite, or critique the text of a LinkedIn post for Ali — "write a post", "draft
  this for LinkedIn", "punch up this hook", "does this sound like me?", "یه پست لینکدین
  بنویس" — or when a post draft is a sub-step of another workflow (sfc-helper briefs, a
  launch post for an app or library, a release announcement). Also load it to review someone
  else's draft against Ali's voice. sfc-helper decides WHAT to post; this skill governs HOW
  it reads. Do NOT use for newsletters (newsletter-writer), sales pages (sales-letter-writer),
  or conversion-first copy diagnosis (conversion-copy), though those may borrow its voice.
---

# Ali's LinkedIn Voice

Ali posts as a Go backend engineer and builder: Go, backend systems, the open-source libraries
under `aliworkshop`, AI engineering, and the products Ali ships. The base voice is the
`writing-style` skill: plain, specific, explain the why, short sentences, no filler. This skill
adds what a feed post needs on top of that.

## Distil the real voice first

> TODO(ali): paste 5-10 of your best-performing LinkedIn posts (English and Persian), each
> with its impressions and reactions/comments if you have them, into
> `references/ali-posts.md`. Then ask Claude to distil them: recurring openers, sentence
> rhythm, emoji use, how you close, what topics got reach vs. replies. Replace the
> "Starting principles" below with what the posts actually show, and fill Part 1 of
> `references/hook-bank.md` with your real hooks.

Until that file exists, the principles below are a starting point, not Ali's measured voice.
Say so when presenting a draft ("written to the default principles; no post history yet").

## Starting principles

### 1. Specificity is the proof

Name the library, the function, the number, the date. "Paging with `WHERE id > ?` instead of
`OFFSET` took the p99 on page 500 from [real number] to [real number]" beats "keyset
pagination is much faster." If a claim can carry a real number, it should. If you don't have
it, ask Ali. Never invent or round one. An unmeasured "10x" reads as marketing; cut it.

### 2. Write for the skimmer, reward the reader

The hook works alone, list headers work alone, whitespace does the pacing. Paragraphs are 1-2
sentences. Draft the skeleton first (hook + item headers + close) and check it stands on its
own. Then add at most 3 short sentences of commentary per item: the honest caveat, the
trade-off, the thing that broke. Skimmers get the skeleton; readers get the insight.

### 3. Peer, not guru

Teach only from what Ali has built or broken. Include at least one honest cost, failure, or
"this is what I'd do differently" in any post that shares a win. Don't tell the reader what
they're doing wrong; describe the pattern and let them place themselves in it.

### 4. Every post is an exchange

The hook makes a specific promise, the body delivers it fully (no teasing "link in comments
for the rest"), and the close asks a question the reader can answer from their own work:
"How do you page deep lists in Postgres?" not "What did you think?"

### 5. Two engines: the list and the take

Teaching (resources, lessons, a stack, a checklist) → hook, 1-2 line reframe, numbered list,
question close. Arguing (a stance on architecture, tooling, AI) → plain prose, no list, no
CTA. A CTA on an opinion post undercuts its confidence.

### 6. Say it, then translate it

Every abstraction gets a plain restatement within a line: "The scope is a fixed filter. In
other words, no query string can widen whose rows you see." Not every reader is a Go
engineer. Translate a term in parens rather than avoiding it.

### 7. Show the code sparingly

LinkedIn renders no code blocks. One short line in backticks is fine; anything longer goes in
an image or a link to the repo or gist. The post carries the idea, the repo carries the code.

## Persian posts

Write natively in Persian, not a translation of an English draft (see `bilingual-copy`).
Keep technical terms people actually use in Latin script (`Go`, `PostgreSQL`, `goroutine`)
rather than forcing Persian coinages. Correct ZWNJ and Persian punctuation. When a post goes
out in both languages, write each one for its own audience; the hook usually changes.

## Hook principles (the first two lines)

The hook is the **first two lines**, both above the "…see more" fold. Line 1 stops the scroll,
line 2 re-hooks. Retrieve a pattern from `references/hook-bank.md` before writing one from
scratch.

1. **Promise + stakes in the same breath.** "5 Go libraries" is nothing; "5 Go libraries I
   stopped writing myself" gives a reason to care.
2. **The first four words decide it.** Open on I, you, a number, or a named role, never an
   abstract trend ("Microservices are becoming…").
3. **Name the turn.** "Works on my machine… until the second replica." A flat claim with no
   reversal is a weak hook.
4. **Precision is the hook.** A real, unrounded number beats a round one.
5. **Match the mechanism to the intent, then rotate.** Teaching → number + stakes or
   myth-bust. Arguing → bold declaration or concede-then-pivot. Launch → plain value + 👇.
6. **Two lines, colloquial, open loop.** Claim, whitespace, turn.
7. **Ground every hook in something Ali actually did or holds.** Each hook traces to a real
   number, a real commit, or a stance Ali has stated. No invented provocations.

## Hook process (before drafting any post)

1. Generate **10 candidate hooks**, genuinely different mechanisms: 5 in Ali's voice, 5 in
   named outside creators' registers (Part 2 of the hook bank).
2. **Print the source next to each**: the fact, number, or stance it's built on. A hook with
   no source is cut.
3. **Novelty check.** Compare against the last 3-4 weeks of Ali's posts (ask for them, or read
   the content board via `sfc-helper`). Kill any candidate that repeats a recent mechanism.
4. Present two labeled sections, "Your voice" and "Other people's voices", name each
   mechanism in plain English, say which lever it pulls (reach vs. replies), recommend one,
   and wait for Ali to pick before drafting the body.

**Close the edit loop.** When Ali edits a hook or a draft, diff it against yours, infer the
principle behind each change, and list them back. Ali confirms which generalize; add those to
this skill. Over time, drafts should start where Ali would end.

## Mechanics

- Emoji sparingly: 👉 for the CTA, 👇 for "below". No hashtags unless Ali asks.
- No em dashes in the post. Use a period, a comma, or parentheses.
- Numbered items as `1. Header`, blank line, then commentary.
- Link to the repo or the release, not a homepage.

## Quick self-check before delivering a draft

1. Would a backend engineer stop scrolling for this hook, or is it generic creator-speak?
2. Does every claim carry a real name or number where one exists, and none that was invented?
3. Peer sharing or guru performing? Is there at least one honest cost or caveat?
4. Can a skimmer get the skeleton in 2 seconds?
5. List or take, and is the machinery matched to the choice?
6. Does every abstraction get a plain restatement?
