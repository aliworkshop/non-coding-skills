---
name: youtube-strategy
description: >-
  Turn a pain point, topic, or rough idea into a compelling YouTube package — title, thumbnail, intro hook, motivation/story, outro, and video description — for Ali's channel (Go, backend systems, open-source libraries, AI engineering, in English or Persian). Use any time Ali is writing, brainstorming, or iterating on YouTube content. Triggers include "title ideas", "punch up this title", "thumbnail ideas", "design the thumbnail for X", "package this video", "write the intro/hook", "draft the motivation", "write the outro", "iterate on the script", "Ed Lawrence-style intro", "write the (YouTube) description", and casual mentions like "title this for me", "thumbnail this", "I'm making a video about X", or "help me write the open". Do NOT use for LinkedIn posts (use linkedin-voice), newsletters (use newsletter-writer), or sales copy (use conversion-copy or sales-letter-writer) — this skill is specifically for YouTube packaging and scripting.
---

# YouTube Strategy

Generate compelling YouTube packages — titles, thumbnails, hooks, motivation/story sections, and outros — that earn the click and the watch from Ali's target viewer without being clickbait.

## Avatar (canonical source)

The current viewer definition lives in a channel strategy doc (a Claude Doc or a pinned card on the content Trello board) that Ali points to. Read it fresh as the first move on every YouTube task; it changes, and assumptions baked into this skill go stale.

> TODO(ali): create that doc and link it here. It should hold: who the channel is for (e.g. Go developers moving into backend/AI engineering, Persian-speaking engineers, or both), the channel language(s), 3-5 pains in the viewer's own words, current subscriber count, and what the channel is for (reach, the course, freelance leads, open-source adoption).

Until it exists, default to: working software engineers who know some Go or backend basics and want production-grade depth. Say that you used the default.

When the strategy doc disagrees with anything in this skill or its references, the doc wins.

## The 3-filter framework

Every title, thumbnail, hook line, motivation beat, and outro line passes three filters:

1. **A real avatar would search/click/pause-scroll for this.** Discoverable, recognizable, relevant to their world.
2. **It captures attention** with at least 2 click-driving principles stacked.
3. **It's specific enough to be ownable.** A competitor, generic creator, or Anthropic's homepage couldn't sign the same line or use the same image.

For sentence-level work — "does this exact phrasing land?" — defer to the visualize / falsify / unsignable filter from the `conversion-copy` skill. That's the canonical home for the line-by-line filter. This skill applies it; doesn't restate it.

## Iteration order (top-down)

Lock the higher-level decisions first. Each level constrains the next.

1. **Title** — the verbal hook
2. **Thumbnail** — the visual hook (paired with the title)
3. **Script:**
   - **Intro / hook** — first 10 seconds (~25 words)
   - **Motivation / story** — next 30 seconds (relevance + credibility)
   - **Body** — the substance the title promised
   - **Section cards** *(optional, when the body is chaptered)* — full-frame chapter slates at each section boundary; inherit the thumbnail's visual world
   - **Outro** — the next-video bridge (~10-15 seconds)

Skipping levels leads to wasted iteration. A locked title makes thumbnail concepts faster to generate; a locked title + thumbnail clarifies what the intro promises.

### Visual beats are annotated inline

Scripts notate visual moments as sub-bullets at the line that triggers them:

- `\[ANIMATION\] <what happens on screen>` — motion graphics, B-roll overlays, morphs, builds
- `\[CARD\] <what appears on the chapter slate>` — full-frame section intro slates

The annotation describes *content* — subject, glyph, label, motion only if essential. Don't redefine the visual system at this level. Type, palette, lighting, and motion language are locked at the thumbnail (`references/thumbnails.md`) and propagate down to every card and animation. If a `\[CARD\]` and a `\[ANIMATION\]` land on the same beat and carry the same visual idea, drop one — spend each visual beat once.

## Two non-obvious iteration moves

These come from real sessions. Both apply when the work feels stuck.

### Iterate the first hook line alone, before the full hook

The first line of the intro carries the most weight — it has to anchor in real customer language and pass the filter on its own. Lines 2 and 3 keep shifting until line 1 is locked. Don't try to perfect a full hook in one shot when line 1 is still wrong. See `references/intros.md`.

### Pull verbatim customer language before drafting

Hooks fail when language is invented; they land when it's real. Before generating hook candidates (or motivation copy), pull verbatim phrases from:
- **Comments** on Ali's previous videos and posts (ask Ali to paste them, or read them with a browser tool if connected)
- **Questions engineers actually ask**: GitHub issues on the `aliworkshop` repos, Stack Overflow, r/golang, Telegram groups
- **Course questions** from students of the AI engineering sessions
- **Ali's own notes**: the Trello card or doc where the video idea was captured

Pull at minimum 3 verbatim phrases before drafting. Quote the source for each candidate so the grounding is auditable.

## Routing — when to load which reference

| Task | Reference |
|---|---|
| Generate / sharpen titles | `references/titles.md` |
| Generate / sharpen thumbnails | `references/thumbnails.md` |
| Write or iterate on the intro hook (Ed Lawrence-style) | `references/intros.md` |
| Write motivation/story section or outro | `references/script-body.md` |
| Write the video description (CTA, summary, links, chapters) | `references/descriptions.md` |
| Sentence-level filter on a single line | `conversion-copy` skill (canonical) |

For paired packaging (title + thumbnail together), load both `titles.md` and `thumbnails.md`. For a full script pass, load `intros.md` and `script-body.md`.

## Output format (high-level)

When the task spans multiple levels (e.g., "package this video"), generate top-down: title → thumbnail → intro → motivation → outro. Each level explicitly references the level above so the package coheres.

When the task is one level only (e.g., "give me title ideas"), use the output format inside the relevant reference doc.

## Channel positioning context

The audience is developers, so technical specificity is a feature, not a turn-off: a function name, a benchmark, or a code snippet on the thumbnail can be exactly the click. What developers punish is hype and vagueness. See `references/thumbnails.md` for the visual language.

**Language.** If the channel (or a given video) is Persian, write titles, hooks, and descriptions natively in Persian (see `bilingual-copy`). Keep technical terms engineers actually search for in Latin script (`Go`, `goroutine`, `PostgreSQL`); Persian viewers search with them too. A bilingual channel needs a title per language, not a translated one.

## When in doubt

Prefer the choice that:
- Uses a real number over a vague claim
- Names a specific entity (company, person, mechanism, logo) over a category
- Is grounded in language a real engineer actually used (a comment, an issue, a question in class)
- Stacks fewer principles cleanly over more principles awkwardly
- Respects the viewer's intelligence and time

Lead with substance. The viewer is sophisticated. They click on packages that promise real, specific information — not on packages that try to manipulate them.
