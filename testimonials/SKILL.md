---
name: testimonials
description: >-
  Run Ali's testimonial and social-proof workflow on Trello: ask a client, partner, or beta
  user for a testimonial, polish their raw words into pull-quotes, get approval, track where
  it's published, and nudge the ones that stall. Also covers turning app store reviews and user
  messages into usable quotes. Use whenever Ali mentions a testimonial, review, quote, or
  social proof: "ask X for a testimonial", "polish X's feedback", "did X approve?", "which
  testimonials are stuck?", "I put X's quote on the site", "turn these reviews into quotes",
  "نظر مشتری رو آماده کن". Not for referral asks (referrals) or the lead pipeline (crm).
---

# Testimonials

Real words from real people are the strongest copy on any landing page or listing. This skill
gets them, keeps them verbatim enough to be honest, and tracks permission.

## Find, don't hardcode

Every run: `trelloReadMember` → `get_me`, find the board named `Testimonials`, read its lists.
`TODO(ali):` create the board if missing, with the lists below.

## Board shape

One card per person.

```
Not Asked → Asked → Response In → Approved → Published | Declined
```

- **Title:** `Name (company or "beta user")`.
- **Description:** links to their CRM and engagement cards; the source (`client`, `partner`,
  `beta user`, `store review`); the permission level once known (full name + company / first
  name + role / anonymous).
- **Comments:** dated log. `Ask sent (5/13). FU1 (5/16). Response in (5/20). Approved (5/22).`
- **Due date:** next follow-up. Blank after `Approved` or `Declined`.
- Sections added to the description as the work moves: `## Raw` (their words, verbatim),
  `## Drafts` (polished variants), then `## Testimonial` (the approved version only, with
  attribution).

## Where responses come from

- A reply to the ask email or message (the default; no form needed).
- A form, if Ali uses one. `TODO(ali):` link the form and its response sheet here if so.
- App store / Play reviews and messages from users: these are already public or already sent,
  but **quoting them on a site still needs permission** unless the store's own widget shows
  them. Ask before reusing a private message.

## Cadence

`TODO(ali):` adjust. Defaults: ask right after work is accepted or a user reports a win.
Follow up at +3 and +7 days. On the second follow-up, offer a pre-drafted quote they can approve
with one word. No reply after that → `Declined` (ghosted), noted as such.

**The ask** makes it easy: three short questions — what was it like before, what changed,
would you recommend it and to whom — plus "a couple of sentences is plenty". In Persian when
the person writes in Persian.

## Workflows

### 1. Open an ask

Find their CRM card. Create the card in `Not Asked`. Draft the ask with `email-helper`. After
Ali confirms it was sent: move to `Asked`, set the due date, and take the next touch (clear the
CRM card's due date and comment `Next touch owned by Testimonials, due M/D.`).

### 2. Response in → polish

Paste their words verbatim into `## Raw`. Polish into **3 variants** per
`references/polish-framework.md` (short, medium, and one shaped for a specific surface).
Move to `Response In`. Draft the approval request with the variant Ali picks.

### 3. Approval

On "yes": move to `Approved`, replace `## Drafts` with `## Testimonial` (approved text and
attribution only), keep `## Raw` below as the record. If they edited it, apply their edits and
confirm the final text before approving.

### 4. Published

Move to `Published`, comment where it went (site, store listing, deck, post) and when. This is
the best moment for a referral ask: suggest running `referrals`, don't start it silently. Hand
the next touch back to the CRM card (or to `referrals` if that starts).

### 5. Declined

Move, clear the due date, comment why (said no / ghosted). Hand the next touch back to CRM.

### 6. Sweep

Cards with a due date on or before today. Check for a reply first, then draft the follow-up.
Check sibling cards in CRM and referrals for a live due date (one person, one next touch).
Report with `skimmable-summary`.

## Pre-drafting a quote

Only when there's no response to polish. Ground every beat in what the person actually said:
an email, a chat, a call transcript Ali has. If they gave the "before" but never the "after",
keep the after qualitative instead of inventing a number. Don't amplify their language
("nice to have" doesn't become "a relief"). If results are thin, hold the ask rather than
manufacture a win.

## Rules

- **Never publish without explicit approval** of the exact text and attribution.
- **Verbatim first.** Polish trims and orders; it doesn't add claims.
- **Drafts aren't touchpoints.** Only advance a card on what actually happened.
- For a high-stakes placement (a landing page hero), run the quote through `conversion-copy`.
