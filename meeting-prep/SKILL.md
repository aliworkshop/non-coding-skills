---
name: meeting-prep
description: >
  Prepare Ali for an upcoming meeting or call: a client or freelance discovery call, a job
  interview (either side of the table), a partner or business pitch, a 1:1 with a lead, or a
  technical review. Use whenever Ali says "prep me for my call with X", "I have a meeting
  with X", "interview tomorrow at X", "what should I know before talking to X", "برای جلسه
  با X آماده‌ام کن", or names a person or company next to a time. Produces a one-screen
  brief: who they are, what they likely want, what Ali wants, the questions to ask, and the
  traps to avoid.
---

# Meeting Prep

Do the background work before the meeting so the meeting itself is spent on what only the
other side can tell Ali. Facts that a search can find shouldn't take up call time.

## Step 1: Pin down the meeting

Get, from Ali or the context, in one question if anything's missing:

- **Who**: person, company, their role.
- **Type**: client discovery · job interview (Ali interviewing or being interviewed) ·
  partner/business pitch · 1:1 or team review · technical design review.
- **Ali's goal**: what a good outcome is ("get a scoped quote request", "land the offer at
  ≥ X", "agree on the API contract", "get the venue to sign up").
- **When**, and how long.

## Step 2: Gather, in parallel

- **Web:** the company's site, product, recent news, funding or size, tech stack (job posts
  and engineering blogs reveal it), the person's public profile and recent posts or talks.
- **Ali's own trail:** search Trello for cards mentioning the person or company. If Ali pasted
  an email or chat thread, read it for their exact asks and dates.
- **For technical reviews:** read the PR, design doc, or Claude Doc being reviewed, and the
  code it touches if it's local. Note the decisions that are still open.

Check claims across two sources when they matter (size, funding, role). Mark anything
unverified as such. Never invent a fact about a person.

## Step 3: Write the brief

One screen. In the language Ali asked in.

```
# <Person> (<Company>) — <type>, <Weekday Mon D, HH:MM>

**Goal:** <Ali's outcome in one line>

**Who they are**
- 2-4 bullets: role, company, what they're building, anything recent and relevant.

**What they probably want**
- 1-3 bullets, inferred from the thread or their situation. Mark guesses as guesses.

**Questions to ask**
1. 4-6 questions, highest-value first. Open "what/how" questions that surface their real
   constraint (budget, deadline, who decides, what they tried before).

**Watch for**
- 1-3 traps: scope creep, an unclear decision-maker, a rate anchored low, a stack mismatch.

**Sources:** links.
```

### Type-specific additions

- **Client discovery / freelance:** add *Scope signals* (what's in, what's vague) and the
  questions that turn vague into a quote. Don't quote a rate in the brief unless Ali set one.
  For pricing moves, point to `tactical-negotiation` → `playbooks/freelance-rate-and-scope.md`.
- **Job interview, Ali as candidate:** add *Stories to have ready* (2-3 from Ali's real work:
  backend systems, open-source libraries, products shipped) matched to what the role asks
  for, and *Questions for them* about team, on-call, how decisions get made. Salary moves
  come from `tactical-negotiation` → `playbooks/salary.md`.
- **Job interview, Ali as interviewer:** add a short rubric (3-4 signals the role needs) and
  questions that test each one. Skip trivia.
- **Partner / business pitch:** add *Their win* — what they get, in their terms, in one
  sentence. Use `conversion-copy`'s filter on it.
- **Technical review:** add *Open decisions* with Ali's current position and the strongest
  counter-argument for each. For a disagreement, see `tactical-negotiation` →
  `playbooks/tech-disagreement.md`.

## Step 4: Offer the follow-up

End with one line offering to turn the outcome into Trello cards (`trello-helper`) or a
follow-up email (`email-helper`) after the meeting. Don't create anything yet.
