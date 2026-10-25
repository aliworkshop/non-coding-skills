# Thumbnails

The complete thumbnail strategy, visual identity, composition, and workflow.

## What thumbnails do

Thumbnails are the second half of the click. The title is the verbal hook; the thumbnail is the visual one. They have to work together, but the thumbnail shouldn't repeat the title — it should complement it by raising curiosity the title resolves (or vice versa).

The audience is developers. Developer thumbnails win on clarity and specificity: one recognizable technical subject, one honest claim, readable at thumb-size.

## Visual language for a developer audience

| Element | Works | Doesn't |
|---|---|---|
| Primary hook | A concrete result ("2s → 40ms"), a named failure ("LEAK"), a recognizable logo (Go gopher, Postgres) | Vague hype ("GAME CHANGER"), shocked faces with no subject |
| Visuals | A tight crop of real code or a terminal, a graph with one outlier, Ali's face with a single object | A full IDE screenshot nobody can read, generic circuit-board backgrounds |
| Emotional pull | Curiosity, "I've hit that bug", capability | FOMO and fear stacked on nothing |

## The 3-filter framework (applied to thumbnails)

Every thumbnail that ships passes all three filters in order:

1. **Would the avatar pause their scroll for this image?** Would they recognize the subject as relevant to their world?
2. **Does it capture attention with at least 2 click-driver principles stacked?**
3. **Is it specific enough to be ownable?** A generic robot brain dies. A Go gopher next to a flame graph with one red spike lives.

This is the visual application of the 3-filter framework. For sentence-level work on the thumbnail's hook text, the visualize / falsify / unsignable filter from `conversion-copy` still applies — same canonical home.

## Visual identity

### Color palette
> TODO(ali): set the channel's palette once and keep it. Until then: dark background (near-black or deep navy), off-white text, and ONE saturated signal color (Go cyan `#00ADD8` fits the topic) only for the hook. Saturation everywhere = saturation nowhere.

### Lighting & aesthetic
High-contrast, clean, uncluttered. Code crops use a large font and a dark theme so they read at thumb-size. If brand colors exist, take them from the `brand-system` skill.

## Composition principles

### The 40% rule
The primary subject (Ali's face, the logo, or the one code line/number) must occupy at least 40% of the frame height. ~80% of YouTube views happen on mobile — if it's not readable at thumb-size, it doesn't exist.

### Visual hierarchy (1-2-3)
Build every thumbnail in three layers:
1. **The hook** — ONE high-contrast focal point (a "Hired" stamp, a competitor logo, a shocking data outlier).
2. **The text** — 3 words maximum. Clean, heavy sans-serif.
3. **The context** — subtle geometric grids or a professional environment in the background.

### The squint test
Squint at the design. If the core message is lost, it's too cluttered. Remove elements until only the click remains.

## Typography

- **3 words maximum.** No exceptions.
- **Never repeat the title.** The thumbnail text should *complement* the title by asking a question the title answers, or stating a claim the title qualifies.
  - Title: *"Why Your Goroutines Leak"* → Thumbnail: *"STILL RUNNING?"*
  - Title: *"Build an AI Agent That Survives a Crash"* → Thumbnail: *"KILL -9"*
- **Fonts.** Editorial, heavy sans-serif (Montserrat Black, Bebas Neue). Monospace is fine for a code fragment; avoid glitch or "futuristic" fonts, which read as hype.

## Psychological hooks for thumbnails

The 19 click-drivers in `references/titles.md` apply visually too. The most relevant translations:

- **Curiosity gap** — Show a paradox the viewer needs to click to resolve. A latency graph that drops off a cliff. A green test badge on code that is obviously wrong.
- **Counterintuitive subversion** — Visual contradiction. `go vet` passing on a leak. A one-line diff labeled "10x".
- **Specific real numbers** — One large, defensible number on the thumbnail (`40ms`, `0 allocs`, `1 line`), measured, never invented.
- **Stakes** — Visual symbols of consequence: a red alert, a pager, a crashed process, the word "LEAK" or "DOWN".
- **Authority subversion** — Use a respected reference (the Go logo, the Postgres elephant, a well-known library) and break the expectation with the claim.
- **Direct address** — Ali looking into the camera, eye contact at portrait scale (only if Ali shows face on the channel).

For developers, a real, readable technical artifact (a number, a line of code, a graph) does what credibility props do for other audiences: it signals substance before the viewer reads a word.

## Technical delivery

- **Resolution.** 1280x720 minimum. 1920x1080 preferred.
- **Export format.** `.png` to avoid compression artifacts on text edges. `.jpg` softens the typography enough to look amateur.
- **Contrast ratio.** Aim for 4.5:1 minimum between text and background.
- **Safe zone.** Keep all text, faces, and critical icons away from the bottom-right corner — that's where the YouTube duration timestamp lives and will obscure anything underneath.

## Thumbnail workflow

### Step 1 — Capture intent
Confirm:
- **What's the video about** in one sentence
- **The title** (if known) — thumbnail text complements it. If the title isn't decided, propose paired title + thumbnail concepts together.
- **Strongest visual asset available** — a specific company logo, chart, face, stamp/seal, screenshot of a real artifact?
- **Constraints** (face required vs. no face, on-screen number must be defensible, etc.)

If anything is unclear, ask one question.

### Step 2 — Generate 3-5 concepts
Each concept:
- Stacks 2-3 click-driver principles
- Has a different visual archetype from the others (one logo-led, one portrait, one data-outlier, etc.)
- Passes the 3-filter framework
- Passes the squint test (one focal point, ≤3 words, readable thumb-sized)

### Step 3 — Annotate each
- **Subject** — primary image (Ali's face / logo / chart / code line)
- **Hook text** — the ≤3-word phrase
- **Principle stack** — which click-drivers are doing the work
- **Description** — one sentence on the visual: layout, signal color, paradox or contrast, what the eye lands on first

### Step 4 — Rank and recommend
Pick the top 1-2 to ship first. Strongest concepts usually combine institutional credibility (logos, tickers, masthead framing) with one specific defensible number or one shocking visual paradox.

## Output format

### Thumbnails only

```
**Topic:** <one-sentence restatement>
**Title (assumed):** <the title the thumbnail is paired with>
**Avatar:** <who's the target click>

**Thumbnail concepts:**

1. <Hook text> (≤3 words)
   - Subject: <primary image>
   - Principles: <stack>
   - Description: <1-sentence visual brief>

2. ...

**Top picks to ship first:** <1-2 concepts + brief reason>
```

### Paired (titles + thumbnails together)

```
**Topic:** <one-sentence restatement>
**Avatar:** <who's the target click>
**Outcome:** <what the viewer walks away with>

**Paired packages:**

1. **Title:** <Title>
   - Title principles: ...
   - Thumbnail hook text: <≤3 words>
   - Thumbnail subject: <primary image>
   - Thumbnail principles: ...
   - How they work together: <1 line on the title→thumbnail handoff>

2. ...

**Top pick to ship first:** <1 package + reason>
```

## Guardrails

- **Real numbers, not invented ones.** A fabricated number kills credibility on a thumbnail just as fast as in a title.
- **Avatar appropriateness.** Serious and specific, still using the click-driver principles. Developers punish hype faster than any audience.
- **The thumbnail is not a title.** If the thumbnail text is longer than 3 words or repeats the title, it's broken. Cut.
- **One focal point.** If the squint test fails, the thumbnail is doing too much.
- **Mobile first.** ~80% of views are mobile. If it's not readable at thumb-size, it doesn't matter how good it looks at full size.
- **Readable code only.** A code crop must be legible at thumb-size: 1-3 lines, large font. A full editor screenshot is noise.
- **Don't over-stack.** 2-3 principles per thumbnail is the sweet spot.

## Production note for end-screen pairing

When the video ends with a next-video CTA (see `references/script-body.md`), the thumbnail of that next video should be ready and visible at the moment the verbal CTA hits. Visual + verbal land at the same moment, or the click is lost.
