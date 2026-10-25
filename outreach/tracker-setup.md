# Tracker Setup (Trello)

Use this when step 5 of the outreach flow calls for a tracker. Each campaign gets its own
Trello board: one card per contact, one list per stage, and a pinned card holding the scripts
and the segment legend.

## Confirm the plan first

Show the proposed shape with AskUserQuestion before building:

- **Board name:** `Outreach — <campaign>` (e.g. `Outreach — Venues Q1`)
- **Lists:** `To Contact` → the campaign's milestones → `Added to CRM` / `No`
- **Labels:** segments (`1 Know them`, `2 Met once`, `3 Warm thread`, `4 Cold`) and channels
  (`Email`, `LinkedIn`, `Instagram`, `Telegram`, `In person`)
- **Card shape:** below

If Ali has already said exactly what they want, just build it.

## Board

Create the board and lists with the Trello MCP, then read them back to confirm. Set list
positions with sequential `pos` values so the order sticks.

### Lists = milestones only

Only meaningful forward progress. "Sent, no reply yet" is a card in `Contacted` with a due date,
not its own list.

- **Venues / partners:** `To Contact` → `Contacted` → `Replied` → `Demo Booked` → `Onboarded`
- **Freelance leads:** `To Contact` → `Contacted` → `Replied` → `Call Booked`
- **Beta testers:** `To Contact` → `Invited` → `Joined` → `Gave Feedback`
- **Amplification:** `To Ask` → `Asked` → `Replied` → `Shared`

**Always include** `Added to CRM` (the hand-off when a contact graduates to the `crm` board) and
`No` (terminal).

### Card shape

- **Title:** the person or business: `Cafe Nur (Sara)`.
- **Labels:** one segment, one channel.
- **Due date:** the next planned touch. On a batch send, the same FU1 date for the whole batch
  so they surface together. Blank = nothing planned (intentional; never backfilled).
- **Description:**

```markdown
## Context
Role, business, size, location, how Ali knows them, personalisation hooks, links.
Email / handle: …

## Script
_Option 3 — their new place just opened._
```text
<the finished message>
```
```

- **Comments:** the dated follow-up log only: `Ask sent (7/10). FU1 (7/14). Replied (7/15).`
  Background never goes in comments.

When seeding from an enriched list, write the enrichment into each card's Context and leave
comments empty.

## The scripts card

Pin a card at the top of the first list titled `📌 Scripts & segments`, holding:

- the campaign goal and the conversion event (signed up, booked a demo, shared the post),
- the base script with its numbered personalisation menu,
- the reply templates (yes / soft no / no / question) and FU1, FU2, and salvage templates,
- the segment legend:

```
| Segment | Meaning |
|---------|---------|
| 1 | Know them personally |
| 2 | Met once |
| 3 | Warm thread, never met |
| 4 | Cold |
```

## Segment schemes

Pick the one that matches how Ali wants to prioritise:

- **Relationship proximity** — know them → met once → warm thread → cold
- **Area × type** — for venues: neighbourhood first, then type (bars, cafés, galleries)
- **Channel** — existing DMs → LinkedIn only → cold email
- **Heat tier** — warm intros → known but not close → cold

The number of segments matches the number of distinct openers Ali will use.
