---
name: sfc-helper
description: Strategy-aware short-form content (SFC) ideation for Ali's posts on LinkedIn, Telegram channels, and YouTube Community, in English or Persian. Mines raw material Ali already has (recent git activity on the open-source repos, Trello cards, Claude Code memory and notes, course sessions, analytics findings), audits each idea against the content board, turns it into hooks on request, and on approval stages it as a card on the Trello content board. Use whenever Ali wants post ideas, asks "what should I post", wants to plan or fill the content calendar, wants hooks for a specific idea, wants to repurpose a proven post, "برای کانال چی پست کنم", or wants to turn analytics into scheduled posts. Trigger even without the word "SFC" ("brainstorm posts", "plan my week of content", "what's worth posting"). Do NOT use for drafting the full text of one post (linkedin-voice) or analyzing past performance (linkedin-post-analytics); this is the ideation and scheduling layer between them.
---

# SFC Helper

Turn Ali's work, notes, and post analytics into staged short-form content, ending in cards on
the Trello content board that Ali can act on. This skill decides *what* to post and *why*, maps
it to the strategy, and stages it. It doesn't write finished copy and doesn't pull analytics.

## How this skill composes with others

- **`linkedin-post-analytics`** produces the numbers. Use its latest findings as input; don't
  recompute them.
- **`sfc-helper`** (this skill) takes raw material → audits it against the board → (optionally)
  turns it into hooks → stages it as a card.
- **`linkedin-voice`** drafts the full post. This skill stops at *briefs* (angle and key
  points). For Persian posts, `bilingual-copy` checks the final text.
- **`trello-helper`** owns the mechanics of writing cards (finding the board, dates in UTC,
  labels). Follow its rules when creating or moving cards.

The card holds a brief; the draft gets written later, close to posting, so it's fresh.

## Where raw material comes from

Ali's content comes from Ali's work, not from trends. In order of value:

1. **Recent git activity on public repos.** What changed in the `aliworkshop` libraries, a
   release, a hard bug fixed:
   ```sh
   find ~/go/src/aliworkshop -maxdepth 2 -name .git -type d | while read g; do
     r=${g%/.git}; git -C "$r" log --since="14 days ago" --oneline --no-merges | sed "s|^|$(basename "$r"): |"
   done
   ```
   Commit messages that explain a *why* are often a post already.
2. **Work lessons, anonymized.** A lesson from day-job code is fine as a generic pattern
   ("a payments service retried and charged twice"). Never name the employer, its systems, its
   private repos, or a colleague.
3. **Claude Code memory and notes.** Feedback and project memories under `~/.claude/projects/*/memory/`
   record decisions and corrections with their reasons. Read for lessons, not secrets; never
   quote private paths, names, or credentials.
4. **The AI engineering course.** Each session's README states a failure and its fix: ready-made
   teaching posts.
5. **The content board itself**: ideas parked in the backlog list.
6. **Analytics**: what's worked, from `linkedin-post-analytics`.

## Three modes: mine, single card, and repurpose

**Mine mode** is the workhorse: pick one painful idea from the raw material above and stage it.
Its procedure is in `references/mine-posts.md`.

### Single-card mode: developing one existing card

Ali points at one card ("how many hooks for this?", "draft this one"):

- Read the card and work from its brief. Stay scoped to that one idea.
- **The card title is the hook direction; the description is the payoff.** If the card has no
  hooks yet, say so plainly before offering some.
- **When Ali brings a hook, sharpen it, don't replace it.** Offer 2-3 tight variations and name
  the one risk it carries. The full menu is for when Ali asks "give me hooks".
- **For a hook menu, run `linkedin-voice`'s Hook process** (10 candidates, two labeled halves).
- **On approval, draft and write it in.** Hand off to `linkedin-voice`, then append the chosen hook
  and draft to the card description under the brief, as a `## Draft` section. Don't overwrite the brief.

### Repurpose mode: re-running a proven post on another channel

The input is analytics: Ali picks best-performing posts and wants them run again elsewhere (a
Telegram channel, YouTube Community, or LinkedIn in the other language).

- No ideation, just re-placing proven copy. Still dedupe against the board, still propose the
  lineup and wait for approval.
- **Set the channel label to the target.**
- **Carry over the verbatim copy** from the `linkedin-post-analytics` feed API
  (`commentary.text.text`), in a fenced code block in the card description.
- **Crossing languages is not copying.** A post moving from English to a Persian channel gets
  rewritten natively in Persian via `bilingual-copy`, keeping the hook's mechanism, not its words.
- **Flag the media.** If the source had an image or video, pin `> 📷 Includes an image — pull it
  from the original before publishing` at the top of the card.
- **Dates follow the cadence Ali names.**

## Strategy is the backbone

Every idea serves the strategy in `references/strategy.md`. When laying out or rescheduling a
week, also read `references/scheduling-principles.md`. Board conventions (lists, labels, the
backlog, dedupe windows, the brief format) are in `references/content-board.md`. Run its dedupe
check in every mode before creating or rescheduling a card.

## Principles

- **Anonymize.** Never name a client, colleague, or employer in a post idea. Use a role and a
  domain ("a backend engineer on a small fintech team").
- **Verify numbers before they go in a brief.** A number must be a real, measured before/after.
  If the baseline wasn't measured, say so ("~2s, my estimate") or flag it to confirm. Never
  inflate or invent.
- **Briefs, not drafts**, except in single-card and mine mode when Ali asks for the draft, and in
  repurpose mode, where the card holds proven copy.
- **Build on Ali's angle, don't override it.** Refine and stress-test it; Ali keeps authorship.
- **Lead with ore, not packaging.** Surface the real bug, the real number, the real line from a
  commit message or a student's question. Ali tells the story.
- **One post, one reader.** Each idea targets one audience in `strategy.md`, not everyone.
- **Propose first, create on approval.** Never create or move a card before Ali says go.
