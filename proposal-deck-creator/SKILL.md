---
name: proposal-deck-creator
description: >-
  Build a short, clean proposal deck for Ali: a freelance or contract proposal to a client
  (backend build, API, integration, architecture review), or a pitch to a partner or venue
  for a bilingual (English/Persian) consumer app with a business side. Use whenever Ali says
  "make a proposal deck for X", "put the proposal in slides", "pitch deck for the venue",
  "turn this offer into a deck", "یه پروپوزال اسلایدی برای X بساز", or shares a client's
  context and asks for a proposal. Defaults to three slides (summary, proof, roadmap) and
  extends as needed. Composes with the brand-system and pptx skills. Do NOT use for general
  talk slides (use keynote) or a one-page landing page (use conversion-copy).
---

# Proposal Deck Creator

Build the short, polished deck a client or partner asks for before committing. The job is
half research (gathering *real*, defensible proof) and half design (a clean, scannable deck).
Do the research first. A beautiful deck full of vague claims fails.

This skill **composes with two others**. Always use them together:

- **`brand-system`** for color, type, voice, and the AI-slop bans. Read it before writing any
  copy or choosing colors.
- **`pptx`** for the build mechanics (pptxgenjs) and the mandatory visual-QA loop. Read its
  `pptxgenjs.md` before building.

## Order of operations (do not skip ahead)

1. **Scope** the proposal with the client's context.
2. **Research** real proof from the sources Ali points to.
3. **Confirm** structure and the featured proof with Ali.
4. **Build** the deck with the pptx skill and the brand.
5. **QA** visually with fresh-eyes subagents.
6. **Save and present.**

Building before the research is done is the most common failure. The proof *is* the
proposal's credibility.

---

## Step 1 — Scope the proposal

Gather from the conversation, a Claude Doc or Trello card Ali names, or pasted notes. Ask for
what's missing, in one message:

- **Who is the client and who reads the deck?** A CTO wants architecture and risk; a founder
  wants outcome and timeline; a venue owner wants what their business gets. The audience
  drives the proof slide.
- **What's the offer?** A fixed-scope build, a phased engagement, a retainer, a partnership.
  Pull the real scope if it exists: milestones, deliverables, what's out of scope.
- **Language.** English, Persian, or both. A Persian deck is written in Persian (see
  `bilingual-copy`) and laid out right to left: mirror the layouts, use a Persian font from
  `brand-system`, and keep code names and numbers that must stay LTR wrapped as LTR runs.
- **Client conventions.** If the client has a template or font, honor it and keep the brand
  accent and voice.
- **What stays off the deck?** Rates and totals usually go in the email or contract, not the
  deck. Confirm before including any number. For how to present a rate, see
  `tactical-negotiation` → `playbooks/freelance-rate-and-scope.md`.

## Step 2 — Research real proof (ask where to look)

Do not invent results, client names, or metrics. **Ask Ali where to look.** Typical sources:

- **Ali's public work.** Open-source Go libraries under `github.com/aliworkshop` (stars,
  adopters, what problem each solves), shipped apps and bots.
- **Past projects Ali can name.** What was built, the constraint, the measured result
  (latency, throughput, uptime, time saved). Only what Ali confirms, and only at the level of
  detail Ali is allowed to share. Work under NDA is described by its shape, never by name.
- **The client's own words.** The email or call notes (`meeting-prep` brief) with their pains
  and constraints. These drive the "why" on slide 1.
- **Product data** for partner pitches: real user, event or signup counts Ali provides.

When the research is broad, spawn one subagent per source in parallel. Have each return
concrete data points with source links and a verified-vs-anecdotal flag.

**Tag every item as a "Case study" or an "Example."** A case study is a real result from real
work. An example is an illustrative capability not yet tied to a client (a demo, a prototype).
Never label an example as proven.

`TODO(ali):` add a short list of the 3-5 projects you're happy to cite, with the one number
each, so this step can start from them.

See `references/impact-slide-patterns.md` for turning research into slide content.

## Step 3 — Confirm structure and featured proof

Before building, show Ali the **menu of proof grouped by what the client cares about** and let
Ali pick which to feature (one to three per section). Also confirm the slide list.

## Step 4 — Build the deck

Default is three slides. Extend when the proposal needs it (scope, milestones, team, next
steps). Per-slide patterns are in `references/structure-patterns.md`:

1. **Executive summary** — the client's problem in one concrete sentence, then what / why /
   outcome.
2. **Proof** — case studies segmented by what the audience cares about, each tagged Case study
   or Example.
3. **Roadmap** — a staged plan (e.g. Discovery → Build → Hand-off) with dated milestones and an
   always-on foundation (tests, monitoring, documentation).

Build with pptxgenjs via the **pptx** skill, starting from `scripts/deck_scaffold.js`. It sets
up the wide layout, the brand palette (from `brand-system` tokens), the icon rasterizer, the
card/shadow helpers, and a shared eyebrow+title header. Apply every rule in
`references/design-conventions.md`.

Write the copy per `brand-system` voice and `writing-style`: sentence case, no em dashes, no
hype words, no exclamation points, concrete over abstract.

## Step 5 — Visual QA (mandatory)

Render to images and inspect with **fresh-eyes subagents** as the pptx skill requires. Check
first for text overflow inside cards, then overlaps, alignment, and edge margins. In a Persian
deck also check text direction and that Latin runs haven't jumped to the wrong side. Fix real
issues, re-render, and stop after one clean pass.

## Step 6 — Save and present

Save the `.pptx` to the client's working folder and say where. Keep the closing note short:
what's in it and the one or two open items (proof still needing sign-off, pricing kept for the
email). Offer a covering email via `email-helper`. Don't send anything.

---

## Reference files

- `references/structure-patterns.md` — per-slide layouts and copy patterns.
- `references/impact-slide-patterns.md` — turning research into the proof slide.
- `references/design-conventions.md` — the design rules for these decks. Read alongside
  `brand-system`.
- `scripts/deck_scaffold.js` — pptxgenjs starter. Copy and fill in the slide bodies.
