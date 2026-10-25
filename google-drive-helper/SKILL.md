---
name: google-drive-helper
description: Navigate Ali's Google Drive when the Google Drive connector is attached — search, read file contents, look in known folders, and avoid the connector's quirks. Use whenever Ali asks to find a file in Drive, read a Google Doc/Sheet/Slide/PDF, look in a folder, pull form responses, find a Meet transcript, or shares a Drive URL to read. Triggers include "find X in my drive", "read this doc", "pull the responses for X", "search drive for X", "where's that proposal I wrote", "the spreadsheet from last week", "تو درایو دنبال X بگرد". Do NOT use for file organisation (moving, renaming, batch operations).
---

# Google Drive Helper

Reference for finding and reading files in Ali's Google Drive and for avoiding the connector's
traps. Load it, then act on the request.

**Needs the Google Drive connector.** If it isn't attached, say so in one line. Don't fall back
to scraping Drive in a browser.

## Workspace

The connector reaches one Google account: the one it was authorised with. Files owned by other
accounts only appear when they were shared into it (search shows `sharedWithMeTime`). There's no
way to list a folder owned by someone else; only individually shared files are reachable.

When linking back to Ali, use the `viewUrl` the API returns. Don't hand-build URLs.

## Known folders

`TODO(ali):` add folder IDs you use often (forms, response sheets, Meet Recordings, proposals).
When a request names a known folder, search by `parentId =` instead of a fuzzy title search.

| Folder | ID | What's inside |
|---|---|---|
| `Meet Recordings` | `TODO(ali)` | Google Meet transcripts (Google Docs), written only for meetings Ali organised. |

## Tool cheatsheet

| Need | Tool |
|---|---|
| Find files by query | `search_files` (Drive query syntax) |
| Recently touched | `list_recent_files` |
| Metadata only | `get_file_metadata` |
| Read as text | `read_file_content` |
| Download bytes | `download_file_content` |
| Permissions | `get_file_permissions` |
| Create a file | `create_file` |
| Copy a file | `copy_file` |

## Connector quirks

1. **`mimeType = 'application/vnd.google-apps.form'` returns nothing.** Search Forms by title or
   by their folder's `parentId`.
2. **Forms can't be read or downloaded.** Read the linked response sheet instead.
3. **No deep link to one form response.** Only the form's `#responses` summary URL. Offer the
   response-sheet row instead.
4. **Shortcuts vs. files.** Folders can hold shortcuts (`application/vnd.google-apps.shortcut`).
   Resolve to the target ID before reading.
5. **Title search ignores case, returned titles don't.** Echo the real casing.
6. **Unshared folders look empty.** If `parentId =` returns nothing for a folder that should have
   contents, it's probably owned by another account. Say so rather than guessing.
7. **`create_file` only converts plain text to a native Doc.** For an editable Google Doc, upload
   as `contentMimeType: 'text/plain'` (and `text/csv` for a Sheet). Markdown or HTML uploads stay
   raw files with the markup visible. To keep a real `.md` file, pass its native type with
   `disableConversionToGoogleType: true`. Check the returned `mimeType`.
8. **No delete, trash, move, or update.** A wrong `create_file` leaves an orphan Ali has to trash
   by hand, so get the format right on the first call.

## Search syntax

Clauses join with `and`, `or`, `not`, parentheses; strings in single quotes.

| Clause | Example |
|---|---|
| Title contains | `title contains 'invoice'` |
| Title exact | `title = 'My Doc'` |
| MIME type | `mimeType = 'application/vnd.google-apps.spreadsheet'` (not Forms) |
| Folder | `parentId = '<folder_id>'`, `'root'` for My Drive |
| Full text | `fullText contains 'OAuth'` |
| Owner | `owner = 'me'` |
| Shared | `sharedWithMe = true` |
| Date | `modifiedTime > '2026-01-01T00:00:00Z'` |

## Common workflows

### Find X
1. Known folder → `parentId =`.
2. Otherwise title search first, `fullText contains` as fallback.
3. Return 5-10 hits; narrow before dumping 25+.

### What does X say?
`read_file_content` handles Docs, Sheets, Slides, PDFs, and Office files. Forms → the response
sheet. Quote sparingly.

### Pull responses for a form
Find the sheet titled `<form name> (Responses)` and read it. Questions are columns, responses rows.

### That file from last week
`list_recent_files` ordered by `lastModifiedByMe` or `recency`.

### Find the transcript for a call
Given a name and a date (the caller supplies them):

```
parentId = '<Meet Recordings id>' and title contains '<name>'
  and createdTime > '<day start, UTC>' and createdTime < '<day end, UTC>'
```

A transcript is written seconds after the meeting ends, so `createdTime` is the meeting time.
Compute the day's UTC bounds from Ali's local day (see `night-transcript-linker` Step 0). If
several match one day, return all and let the caller decide. Instant meetings are named by a
meeting code, so fall back to the date. This skill finds the file; linking it is the caller's job.

### Save to Drive
Pick the format first (quirk 7): a clean Doc → plain text; the real file → native type with
conversion off. Set `parentId` for a known folder. There's no undo (quirk 8).

## When something new breaks

If a request hits a quirk not listed here, tell Ali what happened instead of guessing. The
connector is undocumented in places.
