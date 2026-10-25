# Per-Prospect Scripting & Channel Formats

Downstream of tracker setup (step 6): turning the base script and personalisation menu into a
ready-to-send message on **every** card, then drafting the sends.

## The per-prospect loop

For each card: read its **Context** → pick the single best-fit `{Personalization}` option
**verbatim** → write the finished script into the card description as a plain text code block →
add a one-line italic note with the option and why.

Ali fills in the specifics (the literal "X", any tweaks). **Pick the option; don't rewrite it.**
Rewording an opener Ali is about to edit is wasted work.

## Segment → default opener

| Segment | Default opener |
|---|---|
| 1 — know them | "It's been a while, hope things are going well!" |
| 2 — met once | "Great meeting you at X!" |
| 3 — warm thread | judgment (below) |
| 4 — cold | "This seemed relevant to you so I thought I'd share." |

- **Segment 3** depends on the actual thread: a recent exchange → "great talking"; warm but old
  → "it's been a while"; one-sided → "seemed relevant".
- **A recent change beats the segment.** A new venue opening, a new role, a launch → "Congrats on
  X!" is the strongest opener, even cold.
- **Persian contacts** get the Persian version of the menu, in the register they'd expect
  (see `bilingual-copy`). Write the Persian openers once on the scripts card; don't translate per
  card.

## Follow-up and salvage templates

- **Follow-ups open inline** in the existing thread: `Hey {Name}, just wanted to follow up.` No
  sign-off. Only the name varies.
- **One follow-up body serves the whole list.** Don't spin per-person variants.
- **"Replied then went quiet" gets its own salvage template**: a pass-along plus an open door,
  opened with their name.

## One campaign, several channels

The channel label changes the format:

- **DMs (LinkedIn, Instagram, Telegram) and text:** plain text, the **raw visible link**.
- **Email:** three extras — an **email address in Context**, a `**Subject:**` line at the top of
  the block, and a **hyperlinked CTA** (`[→ Book a 15-min demo](url)`) instead of the raw link.
  Keep it in the code block anyway; the real hyperlink is built when the draft is made.

## Subject line register matches the send

- **Personal 1:1 email:** plain and personal ("Quick question about Cafe Nur's events").
- **Broadcast:** the benefit headline belongs there, never on a 1:1.

Craft details live in `conversion-copy`.

## Finding an email address

Cheapest first:

1. The business's own site, Instagram bio, or Google Maps listing.
2. The mail connector, if connected: search the name or domain (also confirms it's current).
3. The `crm` board, including `Archived`.
4. Ask Ali.

Watch for stale addresses from an old card. Flag them, don't silently use them.

## Drafting

Defer the mechanics to `email-helper`. **Draft, never send.** With a mail connector: draft one,
get Ali's edit, diff it, apply the diff to the batch. Without one: give each message in a code
block, grouped by channel, ready to paste.

## Logging the sends

Once Ali confirms a batch went out: comment `Ask sent (M/D).` on each card and set the same FU1
due date across the batch (see SKILL.md, "Logging a batch send").
