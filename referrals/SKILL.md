---
name: referrals
description: >-
  Run Ali's referral workflow on Trello: open a referral ask with a happy client, partner, or
  beta user, follow up, log the names they share, hand new intros to the CRM, and trace a lead
  back to who referred them. Use whenever Ali mentions a referral or an intro: "ask X for
  referrals", "did X send those names?", "X just intro'd me to Y", "who owes me intros?",
  "sweep the referrals", "thank X for the referral", "کسی رو معرفی کرد؟". Also fires when an
  engagement wraps or a testimonial is published, since those are the best moments to ask.
  Not for the lead's own pipeline (crm) or testimonial asks (testimonials).
---

# Referrals

Happy clients, partners, and early users are the warmest source of the next client or venue.
This skill turns "I know some people who'd want this" into tracked intros.

## Find, don't hardcode

Every run: `trelloReadMember` → `get_me`, find the board named `Referrals`, read its lists.
`TODO(ali):` create the board if missing, with the lists below.

## Board shape

**One card per referrer**, never per referred person. A referrer can produce many intros; they
live in the card's checklist.

```
Not Asked → Asked → Names Given → Intro Made → Converted | Declined | Dormant
```

The card sits in the furthest stage reached across all that referrer's intros.

- **Title:** the referrer's name (and company).
- **Description:** link to their CRM card and engagement card; how the offer came up
  (`offered` — they volunteered — or `asked`).
- **Checklist `Referrals`:** one item per referred person:
  `Name (role, company) — named 5/2` → `intro'd 5/6, <CRM card link>` → `converted 6/1`.
- **Comments:** dated log, `Ask sent (5/1). FU (5/4). Gave 2 names (5/6).`
- **Due date:** the next follow-up. Blank when nothing is pending.

## Cadence

`TODO(ali):` adjust to taste. Defaults:

- **When to ask:** a high-goodwill moment — work delivered and accepted, a client names a win,
  a testimonial goes live, a partner reports results. Not in the middle of a problem.
- **General ask:** start with a short check-in ("how's it going with X?"), then ask on the reply.
  **Offered or asked on a live call:** go straight to the ask.
- **Follow-ups:** +3 days, then +5 days. No reply after that → `Dormant`, and the person's next
  touch goes back to the CRM's nurture cadence.
- **The ask itself** is specific: who exactly Ali can help ("anyone running a venue who's
  tired of managing guest lists by hand", "a team that needs a Go backend built"), and an easy
  path — a forwardable two-line blurb they can send as is.

## Workflows

### 1. Open an ask

Find their CRM card (and engagement card, if paid work). Create the referrals card in
`Not Asked`. Draft the first touch with `email-helper`. **After Ali confirms it was sent:**
move to `Asked` (or keep `Not Asked` if it was only the check-in), set the due date, and take
the next touch: clear the due date on their CRM card and comment there
`Next touch owned by Referrals, due M/D.` See "One person, one next touch" in `crm`.

### 2. Log names

Move to `Names Given`, add one checklist item per person, and draft the next move: an intro
email from Ali, or the forwardable blurb if they'd rather send it. Set a due date in case the
intro doesn't land.

### 3. Intro lands

Hand the new person to `crm` (new card, source label `Referral`, Context names the referrer).
Update the checklist item with the CRM card link and `intro'd M/D`. Move to `Intro Made`. From
here the lead's journey belongs to the CRM; don't duplicate it here.

### 4. Close out

- **Converted:** tick the item `converted M/D`, move the card, and draft a thank-you. That's
  also a good moment for the next ask.
- **Declined** (an active no): move, clear the due date, comment the reason.
- **Dormant** (silence after the follow-ups): move, clear the due date.
- On all three, hand the next touch back: set the CRM card's due date per its own cadence and
  remove the pointer comment's claim with a new comment.

### 5. Sweep

Cards with a due date on or before today, in any non-terminal list. Before drafting, check for
a reply since the last comment (mail connector if connected, or ask Ali). A reply may already
move the stage; apply that first. Check the person's CRM and testimonials cards: if another card
also has a live due date, fix the stale one if it's clearly drift, or ask Ali which owns it.
Report with `skimmable-summary`.

## Rules

- **Drafts aren't touchpoints.** Only advance a card on what actually happened.
- **Never send.** `email-helper` drafts; Ali sends.
- **Append comments, never edit old ones.**
