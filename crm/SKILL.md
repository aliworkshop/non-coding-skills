---
name: crm
description: >
  Read, update, and act on Ali's CRM on Trello: freelance/contract leads, paying clients, and
  partners or venues for the business side of the consumer app. Use whenever Ali mentions
  leads, contacts, clients, partners, venues, the pipeline, or follow-ups, even casually:
  "check my CRM", "update the CRM", "add this person", "any updates on leads?", "who should I
  follow up with", "move X to clients", "did anyone reply?", "سرنخ‌ها چی شدن", or a person's
  name in a sales or partnership context. Also fires when Ali shares an inbound email or
  message that looks like a lead, and when a meeting gets booked.
---

# CRM

The CRM is one Trello board. Each person or account is a card; each list is a stage. A card's
due date is its **next touch**. That one rule is what makes "who needs a follow-up" a single
query.

Three kinds of relationship live here, told apart by label:

- `Freelance` — someone who might hire Ali for backend or contract work.
- `Partner` — a venue, business, or partner for the business side of the consumer app.
- `Beta` — a user or tester worth staying close to.

`TODO(ali):` confirm the board name and which of these Ali actually tracks. Until then, find
the board named `CRM` and ask once if it doesn't exist.

## Find, don't hardcode

Every run: `trelloReadMember` → `get_me` (member id, timezone), find the `CRM` board by name,
read its lists and labels. Never write ids into this skill.

## Board shape

Lists, left to right:

```
Lead → Talking → Proposal Sent → Client → Nurture | Lost | Archived
```

- **Lead** — contact made or inbound arrived, nothing booked.
- **Talking** — a call is booked or a real back-and-forth is live.
- **Proposal Sent** — a scope or quote went out.
- **Client** — paid or signed; work is active. The work itself is tracked by `engagements`.
- **Nurture** — past clients and partners worth a check-in every few months.
- **Lost** — not this round. A due date marks the re-engagement date, if any.
- **Archived** — terminal. No due date, never surfaced in a sweep.

If the board's lists differ, use what's there and map to these stages in your head.

## Card format

- **Title:** the person, and the company if there is one: `Sara Ahmadi (Cafe Nur)`.
- **Description:** a `## Context` section: who they are, what they want, how they found Ali,
  links (site, LinkedIn, the email thread). Background goes here, never in the notes.
- **Notes:** a comment per touchpoint, short and dated, pipeline actions only:
  `Warm DM (3/4). FU (3/11). Replied, asked for rates (3/12).`
  `Call 3/13. Sending scope (3/14).`
  No business details, no budget, no call content in notes. Those go in Context or in the
  meeting brief (`meeting-prep`). Never edit an old comment; add a new one.
- **Due date:** the next planned touch. Notes log what happened; the due date says what's next.
  Don't write "FU in April" in a note, set the date.
- **Labels:** relationship kind, plus the source (`Referral`, `Inbound`, `LinkedIn`, `Personal`).

### One account, one point person

When several people at one company are involved, keep one card anchored on the **point
person**: whoever decides or champions. Only that person's touchpoints move the due date.
Name the others in Context so a future session doesn't need to re-read the thread.

### One person, one next touch

A person can also have a card in `referrals` or `testimonials`. Exactly one of those cards owns
the next outbound touch and carries a due date. The others leave it blank and add a comment
like `Next touch owned by CRM, due 7/28.` Two live dates for one person means two follow-ups
landing days apart, which reads as spam.

## Workflows

### 1. Sweep: who needs a touch?

Read every card on the board with a due date on or before today (in Ali's timezone), plus any
`Nurture` card with no activity for 4+ months. For each, read the latest comments and, if a mail
connector is connected, the latest thread with that person. Then:

- If they replied and it isn't logged yet, log it and propose the next step.
- If the ball is with them and the date has come, draft the follow-up with `email-helper`,
  using the cadence in `references/follow-up-guidance.md`.
- If a message was sent today, don't draft another.

Report with `skimmable-summary`: Due · Replied · Moved · Nurture check-ins, with drafts and
decisions in the closer. Nothing is sent and no card moves until Ali says so.

### 2. Add a lead

From a pasted email, message, or a sentence from Ali: create the card in `Lead`, Context from
what was shared, first comment is only the trigger (`Inbound email (6/2). Replied, offered
call (6/2).`), due date per the cadence. Check for an existing card first, by name and email.

### 3. Log activity

Find the card, add a dated comment, move it to the stage it has actually reached, reset the due
date. Status reflects the furthest *confirmed* stage.

### 4. Won: move to Client

Move the card to `Client`, add `Won (M/D).`, and hand the work to the `engagements` skill to
open an engagement card. When the work wraps, the card moves to `Nurture` with a check-in date
~3 months out.

### 5. Lost or disqualified

`Lost` with a re-engagement due date (default +6 weeks; longer if they gave a timeline).
Disqualified (not a fit at all) goes straight to `Archived` with no date.

## Rules

- **Confirm before writing** anything beyond a single comment or date change. Show the plan
  for batches.
- **Never send.** Draft only. Ali sends, then the card gets logged.
- **Read the real thread** before drafting or logging. Summaries lag.
- **Don't invent** a stage, a reply, or a price. Unknown stays unknown.

## References

- `references/follow-up-guidance.md` — cadence defaults by situation, and what each follow-up says.
- `email-helper` — the words. `meeting-prep` — briefs before calls. `engagements` — the paid work.
- `outreach` — campaigns. A campaign contact who books a call gets a CRM card; the campaign
  tracker keeps only a breadcrumb.
