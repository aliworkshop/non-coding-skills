# Design conventions

These are the concrete design choices for proposal decks. They sit on top of `brand-system` (read that for the full palette, type, and slop bans) and the `pptx` skill (for build mechanics). When a rule here and the brand system agree, the brand system is the source of truth; this file adds the proposal-deck-specific decisions.

## Overall look

- **Clean, light, corporate** — not the dark editorial web look. Light page background (a near-white off-white, not pure `#FFFFFF`), white cards with a soft shadow and a 1px border, generous whitespace. This reads right for conservative clients and for print.
- **One accent doing the chromatic work**: `--brand-primary` from `brand-system`. A green and a goldenrod are allowed as secondary section accents and for the Foundation bar.
- **Wide layout** (13.33 × 7.5). More room, more breathing space.

## Headers — pick two elements, never three

Each slide gets **either eyebrow + title OR title + subtitle — not all three.** Three-part headers feel busy. Default to eyebrow + title across the deck for consistency (the eyebrow is a short section label; the title is the descriptive statement). If a subtitle carries real information, use title + subtitle on that slide instead and drop the eyebrow.

## No footers

No footer ribbons, no "layered system" strips, no credibility lines tacked at the bottom. Structure is: header, then content. Whitespace at the bottom is fine and looks intentional. (The Foundation bar on the roadmap slide is content, not a footer.)

## Color goes on icons, not text

Body text stays dark and uncolored — use the near-black ink, never pure black. Put the color on **icons and small tags**, not on the sentences. This keeps the deck calm and readable. Section headers use a colored icon (e.g. a shield for reliability, a gauge for performance, a calendar for delivery) with a dark text label.

## Case study / Example tags

On the impact slide, prefix each item with a small uppercase tag: **CASE STUDY** (a credible green) for real results, **EXAMPLE** (goldenrod) for illustrative capabilities. The tag is the "mark" that distinguishes proven from possible. Descriptions can run two to three lines — there's usually whitespace to spare, so fuller sentences are good.

## The Foundation bar (roadmap slide)

An always-on band beneath the three stages: tests, CI, monitoring, documentation, security review. Use the **warning-yellow** treatment (soft yellow fill, goldenrod shield icon and label), NOT red. Red reads as a problem or alert; the foundation is a reassurance that quality is built in, not a phase that gets cut.

## Hard bans (these make a deck look AI-generated)

- No accent stripes or color bars — no full-width header/footer bands, no vertical sidebar stripes, no thin colored strip on one edge of a card. Set a card apart with a subtle fill tint or a shadow instead.
- No underline accents beneath titles.
- No gradient text, no glassmorphism/backdrop-blur, no glowing-orb "AI" aesthetic.
- No pure black or pure white — use the off-white background and near-black ink.
- No cream/beige default backgrounds.
- No em dashes anywhere on the slide (they read as an AI tell). Use commas, colons, or "X → minutes" arrows.

## Typography

Honor the client's specified font if there is one. Otherwise use a clean, safe sans. A Persian deck uses the Persian font from `brand-system` (Vazirmatn is the suggestion) and needs the font installed on the machine that renders and presents it, or PowerPoint substitutes a fallback. Per the pptx skill, fonts outside the QA-safe list render approximately in the LibreOffice preview, so give text containers ~10% slack and rely on that slack rather than trusting the preview's exact fit for those fonts.

## Build helpers

`scripts/deck_scaffold.js` already encodes the palette, the rounded-card + shadow helper (remember pptxgenjs mutates option objects in place, so build a fresh shadow object per shape), the react-icons → PNG rasterizer, and a shared eyebrow+title header function. Start from it rather than re-deriving these.

## QA reminder

Text overflow inside cards is the most common defect and is always visible. Check every text box fits before declaring done, using fresh-eyes subagents per the pptx skill.

## Persian decks

Write the copy in Persian (see `bilingual-copy`), set `rtlMode: true` on Persian text runs in
pptxgenjs, align Persian text right, and mirror card order so reading starts at the right.
Numbers and code names that must stay LTR go in their own runs.
