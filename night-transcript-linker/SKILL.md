---
name: night-transcript-linker
description: Scheduled evening job that links each day's Google Meet transcripts to the matching Trello cards (or to a Claude Doc meeting log). Use when running the nightly transcript task, or when Ali asks to "link today's transcripts", "attach the call transcripts", "ترنسکریپت‌های امروز رو لینک کن". Idempotent; safe to re-run.
---

# Night Transcript Linker

Links each of today's Google Meet transcripts to the Trello card for that meeting. It must be
**idempotent**: re-running it skips anything already linked.

Needs the Google Drive connector (for transcripts) and the Trello MCP. Google Calendar is
optional; when connected it tells you which meetings happened today. If Drive isn't connected,
stop and say so.

**Timezone rule (read first).** "Today" is Ali's local day, not UTC. Run it late in the evening,
after the day's calls have ended and transcripts have landed. Late in the evening UTC may
already be tomorrow, so every filter uses the local day.

## Step 0: Today's local date and its UTC window

Use Python's `zoneinfo`; `date -d` with `TZ` is unreliable across runtimes. Take the zone from
the session context if one is named, else the Mac's local zone:

```bash
python3 -c "
from datetime import datetime, timedelta
from zoneinfo import ZoneInfo
import os
tz = ZoneInfo(os.environ.get('TZ_NAME')) if os.environ.get('TZ_NAME') else datetime.now().astimezone().tzinfo
today = datetime.now(tz).date()
start = datetime(today.year, today.month, today.day, tzinfo=tz)
end = start + timedelta(days=1)
u = ZoneInfo('UTC')
print('TODAY=' + today.isoformat())
print('WINDOW_START_UTC=' + start.astimezone(u).strftime('%Y-%m-%dT%H:%M:%SZ'))
print('WINDOW_END_UTC=' + end.astimezone(u).strftime('%Y-%m-%dT%H:%M:%SZ'))
"
```

Set `TZ_NAME=<zone>` when the session names one. Sanity check: the bounds are exactly 24 hours
apart.

## Step 1: Today's meetings

- **Calendar connected:** list today's events with external attendees. Each one is a meeting to
  link.
- **Otherwise:** search Drive's Meet Recordings folder (ID in `google-drive-helper` → Known
  folders) for transcripts created in the window. Each transcript is a meeting.

If there are none, stop: "No meetings today ($TODAY), nothing to link."

## Step 2: Find the card

For each meeting, search Trello for a card whose title or description names the attendee or
company and whose due date is today (or that's linked from the calendar event). If none is
found, the meeting goes to the closer. Don't create cards here.

`TODO(ali):` if you'd rather keep a running meeting log in a Claude Doc instead of cards, name
the doc and this step appends a dated line there instead.

## Step 3: Skip what's done

If the card's description or comments already contain a `docs.google.com` link under
`Transcript`, skip it.

## Step 4: Find the transcript

Use the `google-drive-helper` pattern:

```
parentId = '<Meet Recordings id>' and title contains '<first name or company>'
  and createdTime > '<WINDOW_START_UTC>' and createdTime < '<WINDOW_END_UTC>'
```

- Strip suffixes from the card title ("- Intro call", "- Session 3") and search by the first
  name or company.
- Only meetings Ali organised are transcribed. Instant meetings are named by a code and won't
  name-match; list them in the closer.
- Several matches for one card: pick the one whose time is closest to the event's start when
  the calendar is available. Otherwise list them and don't link.

## Step 5: Link it

Add a comment to the card (keeps the description clean and shows the date):

```
Transcript: [<transcript title>](<viewUrl>)
```

Use the `viewUrl` from Drive as-is.

## Step 6: Report

Format per `skimmable-summary`. Only the section map:

Title: `# Transcript Linker — {Weekday, Mon D}`.
Stat line: `{N} linked · {N} skipped · {N} no-match`.

- ✅ Linked — [card]({card url}) → {transcript title}; empty: "Nothing new to link."
- ⏭️ Skipped — {card} — already had a transcript; empty: "None already linked."
- 🔴 Needs Your Attention [closer] — meetings with no card, no transcript yet, or several matches.

If a tool errors or returns an unexpected shape, stop and report instead of guessing.
