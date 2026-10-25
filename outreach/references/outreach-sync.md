# Outreach Sync

Running a *sync* on a live campaign: check every channel for new replies and conversions, then
move each contact one step forward. Triggered by "sync the outreach", "check for replies", "who
signed up", "did anyone respond", "move the outreach forward".

**The board defines the campaign — read it before you sync.** Don't hardcode a funnel:

- **The lists** are the state machine. Their order is the path a contact travels.
- **The channel labels** say which reply channels are in play. `Email` → the mail connector if
  connected; `LinkedIn` / `Instagram` → the DM inbox in the browser; `Telegram`, text, or in
  person → you can't read those, so ask Ali what came in.
- **The scripts card** holds the decision tree and the exact copy for each move. Use it
  verbatim; adapt only channel wrapping (an email greeting and sign-off).
- **The campaign goal** on the scripts card names the conversion event and its **source of
  truth** (sign-ups in the app's admin, a booking calendar, a form). Pull that first; the board
  and the inbox are not authoritative for who converted.

## The loop

1. Read the board: lists, labels, scripts card.
2. Pull the conversion source, filtered to real conversions, and reconcile: move only cards not
   already in the conversion list. If Ali has to export it, ask for the export.
3. Sweep each active reply channel for new inbound (below).
4. For each card with a new signal, advance one step and fire the matching script.
5. Log a comment, and set or clear the due date by behaviour (below).

## Behaviour → movement

- **Converted:** move to the conversion list. If the campaign has a post-conversion ask
  (share, refer, a next step), draft it and set its due date.
- **Warm** (positive reply, a question, "is this legit?"): move to `Replied`, draft the reply
  from the scripts card, set a follow-up date (same date across the batch).
- **Cold** (declines, "already have something"): move to `Replied` or `No`, and fire the salvage
  ask if the campaign has one ("know anyone who'd want this?").
- **Replied then went cold:** queue the salvage template for the next touch instead of a second
  hard nudge, and note the swap in a comment.
- **Terminal** (the end of any branch of the script tree): clear the due date so the card drops
  out of the sweep. If they graduate to a real conversation, move to `Added to CRM` and create
  their `crm` card.

Two rules that keep the log honest:

- **Record the actual reply channel** when it differs from the card's label.
- **Draft, never send.** Only move a card to a "sent" stage after Ali confirms it was sent.

## Channel sweeps

**Mail** (if connected): one search over the window since the asks went out, then read each full
thread before logging. Snippets truncate and mislead.

**LinkedIn / Instagram DMs** (browser): don't open profiles one by one. The inbox is
recency-sorted, so a reply floats up with the contact as the last sender, while un-replied asks
show your own message last ("You:"). Flag every thread whose latest message isn't yours.

- The list virtualises: scroll the conversation list and load more until the campaign-day
  cluster is covered.
- A single DOM snapshot can show many blank recycled rows. Accumulate names across small scroll
  steps instead of trusting one read.
- One sequential tab only. Never run parallel browser agents.

A thread ending in your own message that is a reply to *their* reply is already-handled
activity: log it, don't draft again.

## Trello writes

Batch card moves and comments, but read the board back afterwards and report what Trello
returned, not what was intended.
