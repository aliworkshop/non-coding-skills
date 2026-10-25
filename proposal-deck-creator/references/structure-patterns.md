# Structure patterns

The default proposal deck is three slides: state the problem and the offer, prove Ali can do it,
then show the path. Each slide is title-and-content, no dense paragraphs. Extend only when the
proposal needs it.

## Slide 1 — Executive summary

The job: in one glance, say what this is, why it matters, and what the client walks away with.

- **Problem line** first. One concrete sentence in the client's terms. Shape: "[Client]'s order
  API times out under peak load, and every timeout is a lost sale." Name the real problem, not
  "digital transformation".
- **What** — the mechanics of the offer: scope, milestones, how the work is delivered (weekly
  demos, PRs into their repo, a staging environment).
- **Why** — why this approach, in a sentence or two. For a technical reader, the key design
  decision and the risk it removes. For a business reader, what changes for their customers.
- **Outcome** — the concrete things the client has at the end: a deployed service, tests, docs,
  a runbook, a handover session.

Layout that works: a tinted problem band across the top, then three cards (What / Why /
Outcome) with the Outcome card lightly highlighted.

## Slide 2 — Proof

The credibility slide. Segment by what the readers care about, so each sees their own concern.
For a client build, common columns: **Reliability / Performance / Delivery**. For a partner or
venue pitch: **Your customers / Your operations / Your revenue**. See
`impact-slide-patterns.md` for the content rules.

Layout: three cards, each with a colored icon, a short label, and a few tagged items
(Case study / Example).

## Slide 3 — Roadmap

Shows the work as a sequence with checkpoints, which makes the scope concrete and sets up a
follow-on phase without saying "buy more".

- Three staged cards, for example **Discovery** (read the code, confirm the scope, agree the API
  contract), **Build** (milestones with dates and a demo at each), **Hand-off** (docs, runbook,
  handover session, a support window). Each card has a "What" and a "Deliverable".
- An always-on **Foundation** bar beneath all three: tests, CI, monitoring, documentation,
  security review. It reassures that quality isn't a phase that gets cut. Use the warning-yellow
  treatment, not red.

For a partner or venue pitch, the stages become **Join** (sign up, set up the listing),
**Launch** (first events, first members), **Grow** (repeat events, reporting).

## Common extensions (only when needed)

- **Who does what** — when a client's team or another contractor is involved, show ownership
  per area. Decide with Ali whether it goes on the deck or stays verbal.
- **Scope boundaries** — a short list of what's out of scope. It prevents most scope fights later.
- **Next steps** — a closing slide with the explicit ask and a date.
- **Pricing** — usually NOT on the deck. It goes in the email or contract. Confirm before adding.

## Per-client conventions

If the client has a deck template, a font, or a required structure, honor it. Purpose-first,
lots of whitespace, single-glance clarity works for almost every reader.
