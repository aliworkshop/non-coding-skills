---
name: brand-system
description: >-
  Ali's brand and design system: color and type tokens, voice, components, icons, logos, and
  the bans that keep a surface from looking AI-generated, with Persian/RTL support. Use
  whenever Claude designs, mocks up, or reviews anything that should look or sound like Ali's
  brand or one of Ali's products: landing pages, app or product pages, decks, social
  graphics, HTML emails, motion graphics, event or talk slides. Triggers: "make this on
  brand", "what colors / font do I use", "design a landing page", "make a banner / hero /
  card", "slide template", "brand this graphic", "match my style", "طراحی با برند خودم".
  graphic-builder, animation-builder, keynote and proposal-deck-creator load it for tokens.
  It's a template: values marked TODO(ali) are placeholders until Ali sets them.
---

# Brand System

One source of truth for how Ali's surfaces look and sound. Every visual skill reads its tokens
from here instead of keeping its own copy. Change a value here and every skill inherits it.

**This is a template.** The structure, rules, and bans are real and apply now. The color values,
fonts, logos, and default reader are placeholders marked `TODO(ali):` in this file,
`references/colors_and_type.css`, and `assets/README.md`. Until Ali fills them in:

- Use the placeholder tokens as they are. They're a neutral, consistent palette, so drafts still
  look like one system.
- Don't invent a brand: no made-up logo, tagline, colors presented as "Ali's", or testimonials.
- If a surface is going public, say once that the brand tokens are still placeholders.

## How this skill is organized

This file is the **universal core**: tokens, type, voice, icons, logos, the bans, and the
AI-slop check. Surface-specific composition lives in `references/`:

| If you're building… | Load |
|---|---|
| A website, landing page, product page, HTML email | `references/web-composition.md` + `references/components.md` |
| A still infographic (social image, PNG one-pager, cheatsheet) | `references/infographic-composition.md` |
| An embedded figure in a blog post, slide, or doc | `references/infographic-composition.md` (`graphic-builder`'s embedded mode strips the social packaging) |
| A motion-graphic clip (B-roll, intro card, lower-third, MP4) | `references/animation-motion.md` |
| An event or talk slide (QR + headshot, 16:9) | `references/event-slide-composition.md` |
| Any voice or copy decision | `references/voice-and-tone.md` |

**Same brand, different rhythms.** A website's hero stack (eyebrow → H1 → subhead → CTA) does
not transfer to a 2-second social still or a 4-second B-roll clip.

## When you fire

1. **Identify the surface** and load the matching reference file.
2. **Read this whole file** for tokens, bans, and voice.
3. **Match an existing pattern before inventing a new one.**

## Universal tokens

### Colors

Defined in `references/colors_and_type.css`. Refer to them by token, never by hex, so a change
there reaches every surface.

| Token | Role |
|---|---|
| `--brand-primary` | **The** brand accent. CTAs, links, focus rings, eyebrows, the default accent in stills. |
| `--brand-secondary` | Used sparingly: wordmark, rare accents. |
| `--brand-accent` | "Available" / "free" / live / success dots. |
| `--brand-warning` | Prices, ratings, badges, the Foundation bar on roadmaps. |
| `--brand-error` | Pain-point cards, form errors, the AI sender in chat graphics. |
| `--brand-success` | Form success states. |
| `--brand-base-100` | Page background on dark surfaces. Never pure `#000`. |
| `--brand-base-200` / `-300` | Card surface / borders and dividers. |
| `--brand-overlay-accent` | Brighter primary for captions over video footage. |

Foreground text uses **opacity on white** on dark surfaces and **opacity on `--brand-base-100`**
on light ones (`--fg-1` … `--fg-7`). The light-surface background is `#FAFAF7`, not pure white.

`TODO(ali):` pick the five chromatic values and the dark base. Constraint that keeps it a system:
one primary doing the work, the rest supporting. Check primary text contrast ≥ 4.5:1 on both
backgrounds.

### Type

| Role | Token | Default (placeholder) |
|---|---|---|
| Headings, eyebrows, badges, button labels | `--font-display` | `TODO(ali)`; Vazirmatn until set |
| Body, links, nav | `--font-body` | `TODO(ali)`; Vazirmatn until set |
| Code, meta, durations, small labels | `--font-mono` | JetBrains Mono |
| **Persian text (any role)** | `:lang(fa)` rule in the CSS | **Vazirmatn** (suggestion) |

**Persian typography.** Vazirmatn is a suggestion, not a decision: it's free on Google Fonts,
has good weights for display and body, and includes Latin glyphs, so mixed text stays in one
family. Whatever Persian face is chosen:

- **No letter-spacing** on Persian. Tracking breaks the joins between letters.
- **No uppercase, no small caps.** Persian has no case. Eyebrows in Persian get weight and color,
  not `text-transform`.
- **More leading:** about 1.8 for body and 1.4 for headings. Persian ascenders and descenders
  need the room.
- **Direction:** `dir="rtl"` on the root of a Persian surface. Use logical CSS properties
  (`margin-inline-start`, `inset-inline-end`) so layouts mirror without a second stylesheet.
  Wrap Latin runs (product names, code, LTR numbers) in `<bdi>`.
- **Digits:** choose Persian (`۱۲۳`) or Latin digits per surface and keep it consistent. Code,
  versions, and anything a user types back stay Latin.

### Radii

- `--radius-box`: `0.25rem` — code blocks
- `--radius-lg`: `0.5rem` — small chips
- `--radius-xl`: `0.75rem` — status badges, FAQ items
- `--radius-card`: `1rem` — **cards**, the dominant corner
- `--radius-field`: `2rem` — pill buttons and inputs (web only)

### Iconography

No icon font. All icons are **inline SVG**, `viewBox="0 0 24 24"`, stroke `1.5`,
`currentColor`, round caps and joins: **Heroicons outline**. A small filled subset exists for ★,
♥, •, and social marks.

- Inline UI icons: `20px`–`22px`. Card centerpieces: `48px`. Flow arrows in stills: stroke
  `2.5`–`3`, since 1.5 reads as a hairline at 22–32px.
- Tint through `color:` on the parent, never a stroke override.
- In RTL layouts, directional icons (arrows, chevrons) flip; non-directional ones don't.
- Paths for the common set are in `references/icons.md`. Don't draw new SVGs from scratch; copy
  the Heroicons outline path.

### Logos

See `assets/README.md`. `TODO(ali):` no logo files are bundled yet. Until they exist, set the
brand name in `--font-display` weight 700 where a logo would go, and never invent a mark.

### Drop-in CSS

For any HTML deliverable, paste `references/colors_and_type.css` at the top. It defines every
token, the base element styles, and the Persian/RTL rules.

## Voice & tone (half the brand)

Copy follows `writing-style`, cut down for a page: direct second person, short declarative
sentences, concrete over abstract, sentence case, one CTA that reads like the next thing you'd
say, with a trailing `→` (`←` in RTL). The full guide with the forbidden-word list is
`references/voice-and-tone.md`.

## Absolute bans (match-and-refuse)

If you're about to write any of these, rewrite the element with a different structure.

**Visual / structural**
- **Glassmorphism, backdrop-blur, skeuomorphism.**
- **The gradient-heavy "AI" look:** glowing orbs, sparkle particles, neon edges.
- **Gradient text** (`background-clip: text`). Emphasis comes from weight, size, or one accent.
- **The hero-metric template:** big number + tiny label + stats row. Spell real numbers inline.
- **Stock photos and decorative illustrations** with no semantic role.
- **Side-stripe borders:** colored `border-left`/`border-right` > 1px as accents.

**Motion**
- **Bounce, spring, elastic, scale-overshoot.** Web motion is 150–200ms color transitions.

**Color**
- **Pure `#000` or `#fff`** (except the QR card on event slides).
- **A sixth chromatic color.** The palette is closed; extend through opacity, not new hues.

**Copy**
- Hype words, exclamation points outside small UI states, generic CTAs ("Click here",
  "Submit", "Learn more"), emoji on marketing surfaces, em dashes, Title Case headings.
- **Placeholder testimonials, invented numbers, or implied partners.** Real and permitted, or
  absent.

## The AI-slop check

Run two altitudes before shipping:

- **First-order:** would a generic AI or SaaS homepage look like this (orb, gradient hero,
  "Unlock the power of…", icon stat cards)? If yes, rework.
- **Second-order:** would a "not-generic" developer-founder site look like this (dark editorial,
  one blue accent, big bold sans, underlined hero phrase)? That lane is crowded too. Break the
  pattern with a structural choice (no hero, single-column long-form, terminal-style type) or a
  copy choice (a specific number or anecdote in the H1 instead of a slogan).

## Universal checklist

1. ☐ Surface identified; the right reference file loaded.
2. ☐ Background is `--brand-base-100` (dark) or `#FAFAF7` (light), never pure black or white.
3. ☐ Body text uses the opacity scale on the right base.
4. ☐ Headings in `--font-display`, tracking adjusted for size (zero tracking for Persian).
5. ☐ One accent doing the chromatic work (`--brand-primary`).
6. ☐ Icons are inline Heroicons outline, stroke 1.5 (2.5–3 for arrows in stills), flipped in RTL.
7. ☐ Copy: second person, sentence case, no hype words, no exclamation points, no emoji, no em dashes.
8. ☐ Persian surfaces: `dir="rtl"`, Persian font loaded, Latin runs wrapped, digits consistent.
9. ☐ No gradients except the hero glow and card thumbnail tiles (web).
10. ☐ No placeholder testimonials or numbers left in anything going public.

## Reference files

```
SKILL.md                         ← universal core (this file)
references/
  colors_and_type.css            ← drop-in tokens, base styles, Persian/RTL rules
  voice-and-tone.md              ← copy rules, forbidden words, CTA microcopy, hero pattern
  components.md                  ← annotated HTML for canonical web components
  icons.md                       ← inline-SVG icon paths
  web-composition.md             ← hero, header/footer, hover/focus
  infographic-composition.md     ← display type, color at scale, light-bg palette, chat colors
  animation-motion.md            ← motion principles, easings, overlay accent
  event-slide-composition.md     ← event / talk slide layout, QR rules
assets/
  README.md                      ← logo file index (TODO: add logos)
```
