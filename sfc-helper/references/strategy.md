# Strategy (distilled)

The live source of truth is a content strategy doc (a Claude Doc or a pinned card on the content
board) that Ali points to. Read it too; this file is the fast version and may drift.

> TODO(ali): fill in the facts below once, then keep them current in the doc. Until then, say
> "using default strategy" when proposing.
> - **Goal of posting**: open-source adoption, the course, freelance/consulting leads, hiring, a
>   product launch, or reputation. Pick one primary.
> - **Readers**: e.g. Go/backend engineers (English), Persian-speaking engineers (Persian), and
>   possibly founders/CTOs who might hire.
> - **Channels and languages**: LinkedIn (en/fa?), Telegram channel name, YouTube Community.
> - **Standing CTA**: the repo, the newsletter, the course, a consulting page.
> - **Territories Ali owns**: topics Ali can speak on from real work.

## Default readers (until the doc says otherwise)

- **Practitioners** — backend engineers who write Go or want to. They care about *how*: patterns,
  bugs, performance, production lessons, honest trade-offs. Authority posts are for them.
- **Deciders** — leads, CTOs, founders who might adopt a library, hire, or contract. They care
  about risk, speed, and judgment. Reach posts with a clear stance are for them.

Persian posts often reach a different crowd from English ones. Treat each language as its own
audience with its own backlog, not a translation queue.

## The barbell content model

Weight both ends, starve the vague middle.

- **Authority end (practitioners):** a real bug and its fix, a benchmark, a pattern with its
  trade-off, a library release with the problem it removes, a course step.
- **Reach end (deciders and broad):** a clear, falsifiable stance ("microservices from day one is
  a tax", "AI writes code; someone still has to own it"), a lesson from shipping.
- **Kill the middle:** abstract analogies aimed at no one, feature roundups, generic AI news
  takes with nothing from Ali's own work.

## What to expect from the data (hypotheses until Ali's analytics confirm them)

- Reach and engagement rate are often decoupled; check both.
- A broad hook with real substance tends to win on both. Make it the heaviest slice.
- Comments drive distribution. Posts that end with a question engineers can answer from their own
  work pull more.
- Likely losers: feature listicles, abstract analogies, off-topic posts.

Replace this section with what `linkedin-post-analytics` actually shows once a few runs exist.

## Cadence and sequencing

Laying out a week lives in `references/scheduling-principles.md`. Don't re-derive cadence here.

**One post, one reader:** a post targets practitioners or deciders, never both.
