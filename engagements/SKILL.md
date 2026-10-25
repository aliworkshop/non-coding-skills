---
name: engagements
description: >
  Track Ali's paid client engagements (freelance and contract backend work) on Trello, from
  signed to delivered. Use whenever Ali mentions creating, updating, or wrapping paid work:
  "open an engagement for X", "X signed", "X paid the invoice", "log hours/milestone for X",
  "mark X as delivered", "what's active right now", "did X pay yet", "wrap up X". Also fires
  when the crm skill reports a deal won. The CRM tracks the relationship; this tracks the work.
---

# Engagements

One card = one paid, scoped piece of work. A client who comes back for a second project gets a
second card. The CRM card is the person; the engagement card is the job.

## Find, don't hardcode

Every run: `trelloReadMember` → `get_me`, find the board named `Engagements`, read its lists,
labels, and custom fields. `TODO(ali):` create the board if it doesn't exist yet, with the
lists below.

## Board shape

```
Signed → Active → Delivered | On Hold | Cancelled
```

| List | Meaning | Moves here when |
|---|---|---|
| **Signed** | Agreed (signed scope or paid deposit), work not started | The deal is confirmed in writing |
| **Active** | Work in progress | The first working session or the first commit for the client |
| **Delivered** | Scope is done | The last milestone is accepted |
| **On Hold** | Paused, not killed | 30+ days with nothing moving and no next step booked |
| **Cancelled** | Ended early | Cancellation agreed; note any refund |

## Card format

- **Title:** `E### - <Client>` — a 3-digit number in order of start date, then the company (or
  the person, for an individual). The prefix keeps a sort by title chronological. Next number =
  the highest existing `E###` + 1.
- **Custom fields** (create once if missing, with Ali's OK): `Price`, `Paid` (Unpaid / Partial /
  Paid), `Start`, `End`. Leave `Price` blank rather than guessing; a blank flags itself, a wrong
  number spreads.
- **Labels:** the kind of work, e.g. `API`, `Integration`, `Consulting`, `Maintenance`.
  Read the board's labels; don't invent new ones without asking.
- **Due date:** the next milestone or delivery date.
- **Description:**

```markdown
**Payment:** <invoice link or how it was paid> — <status, date, amount>

## Scope
- <deliverable, with size: "REST API for X, 6 endpoints", "10 h consulting block">
**Out of scope:** <what was explicitly excluded>

## Milestones
- [ ] <milestone> — <date>

## Links
- Repo / PR / doc / CRM card

## Wrap-up
- Results: _TBD at wrap_
- Next work: _TBD at wrap_
- Referral: _TBD at wrap_
- Review/testimonial: _TBD at wrap_
```

- **Comments:** a dated log, short: `Kickoff call (5/2). Milestone 1 delivered (5/14). Invoice 2 sent (5/15).`

**Scope records what was sold.** If the client asks for more, that's a change request: a new
milestone with its own price, or a new card. Don't quietly widen the scope on the card. See
`tactical-negotiation` → `playbooks/freelance-rate-and-scope.md` for how to say it.

## Workflows

### 1. Open (deal won)

From the `crm` handoff or Ali's word: create the card in `Signed` with the next `E###`, fill
Scope from the agreed email or proposal (not from memory), link the CRM card, set Price only if
the agreement names it. Show it to Ali before creating.

### 2. Update

Log a comment, tick milestones, move the card when its state actually changed, update `Paid`
when payment lands. If a payment connector is connected (see `stripe-helper`), read the invoice
status from it; otherwise ask.

### 3. Wrap

When the last milestone is accepted: move to `Delivered`, fill Wrap-up once (results in
concrete terms, what's next, any referral or testimonial ask), and hand the relationship back
to `crm` — the client card moves to `Nurture` with a check-in ~3 months out, unless another
engagement is still active. Testimonial and referral asks go to the `testimonials` and
`referrals` skills.

### 4. Sweep

Read `Signed` and `Active`. Flag: milestones past due, cards in `Active` with no comment for 2+
weeks (candidate for `On Hold`), delivered work with `Paid` not `Paid`. Report with
`skimmable-summary`.

## Rules

- **Confirm before any write** beyond a comment.
- **The agreement is the source of truth** for scope and price, not a summary of it.
- **Never record a standard rate when a different amount was paid.** Note the reason.

## References

- `references/pricing-principles.md` — where a price comes from and the judgment rules.
- `references/offer-scopes.md` — deliverable shapes for recurring kinds of work.
