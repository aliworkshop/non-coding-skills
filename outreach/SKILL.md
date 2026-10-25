---
name: outreach
description: >
  Run 1:1 outreach campaigns end-to-end for Ali: source a list, enrich it, triage into
  segments, set up a Trello tracker, draft the messages, and log replies. Typical campaigns:
  venues and businesses for the business side of the consumer app, partners, beta testers,
  freelance/contract leads, and amplification asks for a launch. Use whenever Ali is building
  a list of people to reach out to, tracking outreach, or writing the messages. Triggers:
  "find venues in X", "build a lead list", "enrich this CSV", "look up these companies", "set up
  outreach", "add these people to the outreach list", "who have I reached out to", "sync the
  outreach", "write me an outreach DM", "لیست کافه‌ها رو دربیار", or Ali sharing a batch of names.
---

# Outreach

Two halves of one workflow: **build the list**, then **work the list**. A campaign is one push
with a clear audience and goal: signing up venues in a city, recruiting beta testers, finding
freelance clients, getting a launch reshared.

## Confirm before creating

Before anything structural (the pipeline plan, the tracker, the segments, the message
direction), show the plan with AskUserQuestion and get Ali's yes. Shape is easy to get wrong
and tedious to undo.

## Pipeline design

Every campaign is a series of **enrich → filter** cycles, each using a more expensive tool on a
smaller set. For any fact about a candidate, try in order:

```
1. Extract from data you already have (free)
2. Web search, cheap agents in parallel (cheap)
3. Browser lookup of a profile or site (expensive)
4. Ask Ali (most expensive)
```

The pattern repeats at every level: the campaign, each stage, each include/exclude decision.

### Kickoff alignment (first, before any research)

Lock all of this with Ali:

1. **The wide net.** The starting pool and how it's found: which source, which search terms,
   which city or niche.
2. **The non-negotiables.** Usually two axes gate everything. For venues: type and size
   (e.g. bars and cafés that run events, not chains with central marketing). For freelance:
   decision-maker role and company stage. Everything else is scored, not cut.
3. **The anti-ICP.** "Who looks like a fit but isn't a buyer?" Write it down. Discovering it
   halfway through re-ranks the whole list.
4. **The weights**, if scoring. Set them now; don't let them emerge.
5. **Seed `disqualified.md` from the CRM** first: anyone already on the `crm` board (client,
   live lead, partner) is excluded before scoring or enriching.
6. **Sanity-check the channel.** Is this source even the right well? Sourcing is often the
   binding constraint, not scoring.

Then classify each criterion by cost, sequence cheapest first, and present the pipeline.

### Filtering discipline

- **Cut early only on cheap, unambiguous signals** (obviously a chain, obviously closed,
  obviously a student).
- **Keep anything ambiguous or unknown → enrich → filter on facts.** A missing value is not a
  disqualification.
- **Never filter on a field until it's populated** for everyone left.

### Scoring and gating (bigger lists)

Score from weighted components; soft criteria move the score, they don't eliminate. Run the
expensive step only on candidates already scoring well on the cheap ones.

### Enrichment efficiency

- **Dedupe targets.** Five people at one company → look the company up once.
- **Extract before searching.** Titles and bios often contain the company.
- **Batch web searches** into parallel agents (~10 items each), or a Workflow with structured
  output when Ali has opted into one.
- **The browser is last resort, and never parallel.** One browser connection serves one agent.
  Run browser lookups as one sequential agent in one tab, batches of ~15. Parallelism is for
  web-search agents only.
- **Validate coherence:** the size and role must belong to the business they own or run, not an
  employer or a client of theirs.

### Manual checkpoints

After cheap filters narrow the list, before expensive enrichment. Don't hand Ali a raw list,
and don't wait until the end.

## `disqualified.md`

A living file in the campaign folder, updated the moment Ali says someone's off.

1. **Principles** applied automatically: already in the CRM; the anti-ICP; one contact per
   business; clearly outside the size band.
2. **Individuals** cut for reasons only Ali knows:

| Name | Link | Reason |
|------|------|--------|
| … | … | Already talked, not interested |

When Ali cuts someone, check whether the reason implies a new principle ("we already know
someone there" → one contact per business), add it, and apply it to the rest.

## The flow

### 1. Clarify and design

Run kickoff alignment, plus: the goal of the campaign, the target profile, volume needed
(work backwards; attrition is heavy), channels (email, LinkedIn DM, Instagram DM, Telegram,
in person), segments (warmest first), and exclusions. Save the agreed sequence as `recipe.md`
in the campaign folder so the next campaign can start from it.

### 2. Build the list

- **LinkedIn** for people and companies: see `linkedin-sourcing.md` (browser-based).
- **Maps and directories** for venues and local businesses: a web search per area and
  category, then each business's own site or Instagram for contact details.
- CSVs Ali has, contact form submissions, batches Ali pastes in chat.

Save raw leads to `raw/<campaign>_leads_raw.json` so a hundred people don't sit in context.

### 3. Enrich

See `lead-enrichment.md` and `references/bulk-enrichment-playbook.md`. Resolve a field for
everyone before filtering on it.

**Warmth enrichment** before segmenting a warm-network campaign: read the existing DM thread for
each person and classify `they_reached_out` / `replied` / `ghosted` / `never_messaged`. One
sequential browser agent, read-only, never touching a compose box. Whether Ali has met someone
in person is Ali's knowledge: ask.

**Reusing an earlier campaign's shortlist:** treat it as stale. Re-verify role, business, size,
and location before loading.

**LinkedIn gotchas:** a "has following" check reads the intro card only (every profile shows
followers further down). Reconstructed profile URLs often 404; verify they resolve. A same-name
search hit can be the wrong person; confirm against a known signal.

### 4. Triage into segments

Dedupe by URL or email, apply `disqualified.md`, and group. Segments come from the warmth data,
not guesses: people Ali knows → met once → warm thread → cold. Present the triaged list as a
checkpoint.

### 5. Set up the tracker

Once the list is confirmed, build the Trello tracker: see `tracker-setup.md`.

### 6. Draft the scripts

A **base script** per campaign: one core message with a numbered `{Personalization}` menu of
openers (1 = "it's been a while", 2 = "great meeting you at X", 3 = "saw your new place
opened", 4 = "this seemed relevant"). Draft warmest-segment first, one at a time, so Ali can
steer.

Then a **per-prospect script on every card**: read the card's Context, pick the single
best-fit opener **verbatim**, and put the finished message in the card description in a plain
text code block. Ali fills in the literal "X". Add one italic line above saying which option
and why. Details in `references/per-prospect-scripting.md`.

Words: `email-helper` for voice, `conversion-copy` (`channel-outreach.md`) for hooks, CTAs and
the follow-up ladder, `bilingual-copy` for Persian. This skill owns who, when, which segment,
which channel.

### 7. Send, log, review

**Draft, never send.** Ali sends and reports back. For an email batch with a mail connector:
draft one, let Ali edit it, diff the edit, apply it to the rest.

**Logging a batch send:** for every card that went out, comment `Ask sent (M/D).`, set the
due date to the FU1 date (the same date across the batch, so they surface together), and keep
the channel as a label, not in the comment.

**Logging activity:** find the card, move it to the stage reached, append a dated comment.
Never edit old comments.

**Syncing a live campaign:** sweep every reply channel, then advance each card one step along
the campaign's own lists. See `references/outreach-sync.md`.

**Check before drafting a reply.** Ali often answers live. Read the actual thread; if Ali has
already replied, the job is logging it, not drafting a duplicate.

**Draft replies from the campaign's own reply templates** (no / soft no / yes / question), even
when the incoming message doesn't fit cleanly. Bespoke copy is the exception.

**Status review** with `skimmable-summary`: Replied · Awaiting · Converted, follow-ups and next
segments in the closer.

## Variant: amplification asks

Asking well-connected people to reshare a launch post rather than to sign up themselves. Its
own small tracker (`Asked → Replied → Shared → No`). Confirm the post is live before sending.
Warmest first, and let warmth shorten the message: someone who already shared unprompted gets
a two-line thank-you plus the link. Before nudging, check the post's reshares; the tracker can
lag reality.

## Relationship to other skills

- **crm** — when a contact converts (books a call, a venue wants onboarding), give them a CRM
  card. The tracker card gets a final `Added to CRM (M/D)` comment, moves to its done list, and
  loses its due date. The CRM owns them from there.
- **email-helper**, **conversion-copy**, **bilingual-copy** — the words.
- **trello-helper** — ad hoc cards outside a campaign.
