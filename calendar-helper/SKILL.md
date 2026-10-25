---
name: calendar-helper
description: >
  Create, reschedule, and delete events on Ali's Google Calendar (when the Google Calendar
  connector is attached), and keep the matching Trello card in step when one exists. Use
  whenever Ali wants something on the calendar, an event moved, or one cancelled. Triggers:
  "schedule X", "put X on my calendar", "book a call with Y next Tuesday", "another session
  with X next Saturday", "reschedule the X meeting", "move my X call to Friday", "cancel the X
  event", "block off Wednesday morning for X", "جلسه با X رو بذار تو تقویم", "جلسه رو جابجا کن".
  Fires even when "calendar" isn't said, if the request is about scheduling. Also picks times
  to propose to someone.
---

# Calendar Helper

Ali's calendar assistant. It creates, moves, and deletes events the way Ali would: by looking
at past similar events for the naming, length, attendees, and Meet setting, and by keeping the
related Trello card's due date in step.

The core rule: **never create an event from scratch when a reference exists.** Search calendar
history first, and let what's already there decide the shape of the new event.

## Needs

- **Google Calendar connector.** If it isn't connected, say so in one line and offer the next
  best thing: an `.ics` file Ali can open, or the event details to paste. Don't pretend an event
  was created.
- **Trello MCP** for paired cards (optional).
- **Timezone.** Read it from the session context, else from the Mac (`date +%Z`, `date +%z`).
  Write events in that zone. When an attendee is clearly elsewhere, show both zones in the
  report. Never assume a zone that wasn't read from somewhere.

## Does / doesn't

**Does:** create events with defaults from past similar events; increment numbered titles
("Session 2" → "Session 3"); reschedule and delete; shift the paired Trello card's due date;
pick times to propose.

**Doesn't:** write rich descriptions from other context (copy the reference's description,
or leave it empty); create cards for personal blocks or appointments; send emails itself
(drafts go through `email-helper`).

## Creating an event

### 1. Parse the request

Who (names, emails), what (call, interview, workshop session, review, focus block), when
(resolve "next Saturday" against today in Ali's zone), duration if given, recurrence if implied.

### 2. Find a reference event

Search past events with `list_events`:

- **Attendee + topic** is the strongest signal ("another session with Sara" → past events with
  their email).
- **Topic alone** when no one is named ("schedule the next course session").
- **Same slot in earlier weeks** for a recurring block.

Take the most recent match. From it, copy: title pattern, duration, time of day (only if the
request didn't give one), attendees, Meet on/off, color, description.

**Descriptions are guest-visible.** Every attendee sees the invite. Keep it to the meeting's
purpose. Internal notes (rates, prep, who to chase) never go there; they go on the Trello card.
If a reference description carries an internal line, drop it when copying.

### 3. Check for a paired Trello card

If the event is tied to tracked work (a client call, a workshop session, an interview), search
Trello for a card with the person's or company's name. If one exists, set its due date to the
event's start (converted to UTC) and add the event link to the description. If none exists and
the event is clearly client or course work, offer to create one through `trello-helper`.
Don't create cards for personal events.

### 4. Create, then report

If the request is unambiguous, create the event, then report: event link, time in Ali's zone
(and the attendee's zone when different), attendees, Meet URL, and one line naming the
reference used. If no reference was found, say "no reference event, used defaults" so Ali
knows to check it.

Ask (one question, `AskUserQuestion`) only when: a name matches several people, references
conflict (60 / 90 / 60 min — don't average), duration is unknown with no reference, or the
date can't be resolved. Color, Meet, and notifications have safe defaults; don't ask.

## Title patterns

Detect and increment numbered titles:

- `Ali / Sara - Go Workshop (Session 1)` → `(Session 2)`
- `AI Engineering — Session 6` → `Session 7`
- `Release review #12` → `#13`

Generic recurring titles ("Weekly Sync") are reused unchanged.

## Rescheduling

1. **Find the event** (attendee, keyword, or date range). Several matches → ask.
2. **Check its current state first.** A booking tool may already have moved it; then there is
   nothing to write on the calendar and the real work is the cascade below.
3. **Update** start and end with `update_event`. Keep everything else.
4. **Cascade:** shift the paired Trello card's due date, and any prep or follow-up card tied to
   the old date (prep = the day before, follow-up = the day after). Leave completed cards alone.
   If the new time is within 24 hours, offer a short note to attendees via `email-helper`;
   otherwise the updated invite is enough.
5. **Report** the updated event and everything that moved.

## Deleting

1. Find the event as above.
2. **Confirm first** if there are external attendees, since they get a cancellation email.
   Solo blocks are deleted without asking.
3. `delete_event` with notifications on when attendees exist.
4. Ask whether the paired Trello card should move to Done, be archived, or stay. Never archive
   without a yes.
5. Report.

## Defaults with no reference

- Duration: ask for external meetings; 60 min for solo blocks.
- Notifications: all when attendees exist, none otherwise.
- Meet: on when attendees exist.
- Color and description: default and empty.

## Picking times to propose

When Ali needs to offer someone times:

- **Cluster, don't scatter.** Put calls next to existing meetings so focus time stays whole.
- **Back-to-back is fine up to ~90 minutes.** After that, leave 30 minutes.
- **Buffer after high-stakes calls** (client, interview, review): 30 minutes. Casual chats can
  stack.
- **Respect Ali's day shape.** `TODO(ali):` focus hours and no-meeting windows. Until filled
  in, avoid early mornings and propose mid-afternoon.
- **Rescheduling? Re-offer the original time of day** on the new day.
- **Three options, ranked.** More than three turns a reply into a decision.
- **Write the timezone out** when the other side may be elsewhere.

Then draft the message with `email-helper`.

## Edge cases

- **Recurring** ("every other Tuesday") → `RRULE`; confirm the interpretation in the report.
- **All-day** ("block off Friday") → all-day event.
- **Ambiguous name** → offer the top 2-3 matches by recency.

## Rules

- Mirror the reference; don't reinvent it. Keep its quirks.
- Mirror structure, not state. A finished card's ✅ or Done list doesn't carry over to a new one.
- Report what the tools returned, not what was intended.
