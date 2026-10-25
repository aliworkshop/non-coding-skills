---
name: trello-helper
description: >
  Create and manage Ali's tasks, follow-ups, and reminders on Trello. Use whenever Ali says
  "add a card", "make a task for X", "remind me to", "put this on the board", "track this",
  "move X to done", "what's on the X board", "break this into a checklist", "یه کارت بساز",
  "یادم بنداز", or turns the end of a conversation into to-dos ("add these as tasks"). Also
  use when another skill finishes with follow-ups that belong on a board. Uses the Trello MCP.
---

# Trello Helper

Trello is where Ali's to-dos live. This skill turns a sentence into a well-formed card, keeps
boards tidy, and answers "what's on the board" questions.

## Find, don't hardcode

Board and list ids change; never write them into this skill. Each run:

1. `trelloReadMember` → `get_me` for Ali's member id and `prefs.timezone`.
2. List Ali's boards and pick by name. If two boards could fit, ask which one, once.
3. Read the board's lists and pick by name. Typical flow: `To Do` / `Doing` / `Done`. When a
   board uses different names, use what's there.

Quick captures with no obvious board go to the **Inbox** (`trelloWriteInbox`), not a guessed
board. Ali can triage it later.

## Writing a card

A card is a promise to future Ali, written so it still makes sense in two weeks.

- **Title: verb first, specific, short.** `Add keyset paging to dbcore List`, not `dbcore` or
  `Paging stuff`. In Persian when Ali spoke Persian: `پیاده‌سازی صفحه‌بندی keyset در dbcore`.
  Keep repo, package, and branch names in their original form.
- **Description: the why and the done-condition**, two or three lines. What breaks or stays
  missing without it, and how to know it's finished. Link the source (PR, issue, Claude Doc,
  chat) when there is one.
- **Checklist** when the work has more than two separable steps. Each item is one action. Don't
  checklist a one-step task.
- **Due date** only when Ali gave one or the task obviously has one. Don't invent deadlines.
  Convert local time to UTC ISO 8601 before writing; a date with no time defaults to 09:00
  local. Read the date back in local time with the zone named: `2026-10-28 09:00 (GMT+3:30)`.
- **Labels** only from the board's existing set. Don't create new labels without asking.

### Several cards at once

When turning a list of to-dos into cards, set `pos` to 1, 2, 3… so they keep their order, and
create them in one batch. Show the plan first (board, list, titles) and wait for a yes when
there are more than three cards or when they go to a shared board.

## Moving and closing

- "Done with X" → find the card by title, move it to the board's done list, and confirm with
  its link. If several cards match, list them and ask.
- Never archive or delete a card unless Ali says archive or delete. Moving to Done is not
  archiving.
- On shared team boards, don't reassign or move someone else's card without asking.

## Reading the board

For "what's on X" or "what's left", read the board and answer with the `skimmable-summary`
format: sections per list, cards as linked one-liners with due date and checklist progress,
and overdue or blocked cards in the closer.

## Reporting back

After any write, reply with one line per card: linked title, board → list, due date in local
time. Report what Trello returned, not what was intended. If a write failed, say which and why.
