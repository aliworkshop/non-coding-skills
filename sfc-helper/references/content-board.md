# The content board (Trello)

Posts live as cards on a Trello board. Find it by name each run (`trelloReadMember` → `get_me`,
then list boards); never hardcode ids. Card-writing mechanics (UTC dates, positions, labels)
follow `trello-helper`.

> TODO(ali): create the board (suggested name: `Content`) with the lists and labels below, or
> point this file at the board you already use and rename the lists here to match.

## Lists

| List | Meaning |
|---|---|
| `Backlog` | Ideas with a brief, not scheduled |
| `Scheduled` | Has a post date (the card's due date) |
| `Drafted` | Draft written in the description, ready to post |
| `Posted` | Published; due date = the date it went out |

**The list is the status.** Don't infer status from labels.

## Labels

- **Channel**: `LinkedIn`, `Telegram`, `YT Community`.
- **Language**: `en`, `fa`.
- **Type** (one per card): `Thesis`, `How-to`, `Education`, `Use case`, `Resource`, `Share`,
  `Promo`, `Listicle`, `Builder Log`, `Journey`.

Use only labels that exist on the board. Ask before creating new ones.

## Choosing a type

Judge the brief, not the title.

- **Thesis** — argues a point of view someone could disagree with.
- **Education** — explains a concept neutrally ("how goroutine scheduling works").
- **How-to** — steps the reader follows to get a result.
- **Use case** — a concrete, anonymized before → after.
- **Resource** — hands over a reusable asset (a checklist, a template, a snippet).
- **Share** — points to content elsewhere (a video, a talk, a README).
- **Promo** — an event, release, or offer with a clear ask.
- **Listicle** — built around an enumerated set.
- **Builder Log** — behind the scenes of something Ali is building or shipping.
- **Journey** — a personal arc over time.

Tie-breakers: a story that pays off in a belief is **Thesis**, not Use case. A shared asset the
reader keeps is **Resource**; one that sends them elsewhere is **Share**.

## Dedupe before creating anything

Read the board and check two windows:

- **Backlog and Scheduled**: is the idea already there? Then rebrief and reschedule *that* card.
  Don't create a second one.
- **Posted in the last ~4 weeks**: is the topic recent? Then wait. A topic posted more than ~4
  weeks ago is fair game to rerun.
- **Hook freshness**: don't repeat the opener mechanism of the last several posts.

Check per language: the same idea in `en` and `fa` is two cards, not a duplicate.

## Brief format (card description)

```
**Angle:** <the hook / thesis in one or two lines>
**Reader:** Practitioner / Decider
**Key points:**
- <2-4 bullets of substance>
**Source:** <anonymized origin, e.g. "dbcore commit a1b2c3", "course session 7", "work: payments retry bug">. <Honesty note on any number>
**CTA:** <only if relevant>
```

## Repurpose cards

The description holds the **verbatim original copy in a fenced code block** instead of a brief,
with a media note on top if the source had an image or video. Set the target channel label.

## Creating cards

- Create in `Backlog` (no due date) or `Scheduled` (due date = post date, 09:00 local → UTC).
- When creating a week at once, set `pos` 1, 2, 3… in date order.
- Propose the lineup first; create only after Ali approves.
