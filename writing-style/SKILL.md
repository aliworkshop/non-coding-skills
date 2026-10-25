---
name: writing-style
description: >
  Ali's house style for anything written in prose: READMEs, docs, project instructions
  (CLAUDE.md), PR descriptions, commit messages, release notes, team announcements, Slack
  or Telegram updates, technical posts, and course material. Use whenever Claude writes or
  edits prose for Ali, or when asked to "make this clearer", "tighten this", "rewrite this
  README", "write the PR description", "write a commit message", "explain this to the team".
  Other writing skills (email-helper, conversion-copy) take their voice from here. Do NOT use
  for code itself or for skimmable digests (that's skimmable-summary).
---

# Writing Style

Ali writes the way the code should be written: simple beats clever, less beats more, and
every sentence earns its place. The reader is busy and smart. Give them the thing, then the
reason, then stop.

## The rules

**Explain why, plainly.** A sentence earns its place by saying something the reader can't see
for themselves: why a bound is exclusive, why a filter is fixed, what breaks if the order
changes, what a choice cost. Don't narrate what the next line, step, or screenshot already
shows.

**Short sentences.** One idea each. A long sentence with clauses hung off dashes and
parentheses becomes two or three short ones. If a sentence needs a second read, split it.

**Say it once.** A rule, a number, a definition lives in one place, and the rest points to it.
Repeating it "for convenience" means two copies drift apart.

**Concrete over abstract.** Name the file, the function, the endpoint, the number. "The `List`
query reads every row when paging is off" beats "there may be performance implications."

**Lead with the answer.** The first line says what this is or what was decided. Background
comes after, if at all.

**No filler.** Cut "it's worth noting", "in order to", "basically", "simply", "robust",
"seamless", "leverage", "comprehensive", and any sentence that restates the previous one.
Cut hedges that protect the writer rather than inform the reader.

**State limits honestly.** If something is accepted rather than fixed, say so and say why.
"Inside that window the two disagree. That's accepted, because closing it means writing on
every read." Readers trust a document that names its own gaps.

**Plain formatting.** Headings and lists when the content has that shape, not to decorate it.
A table when comparing things across the same columns ("before / now"). Code in fences, names
in backticks. Bold for the one thing per section a skimmer must not miss, never for whole
sentences.

## By format

### README

Open with what the thing is in one line, then how to run it in a code block, then what's
interesting about it. Example openings Ali likes:

> Built up from nothing, one step at a time. Two dependencies and nothing clever.

A README for a library shows the smallest working example before any option. Options nobody
passes don't get documented as if they matter.

### Project instructions (CLAUDE.md and the like)

Rules as short paragraphs with a bolded lead sentence, each followed by the reason. Point to
a real file as the pattern (`see event/handler.go`) instead of restating it. Include the
traps: "things that are easy to get wrong."

### Commit messages

```
type(scope) Capitalized summary

Why the change was needed, and what it cost or gave up.
```

- Types: `feat`, `fix`, `refactor`, `docs`, `test`, `chore`.
- No colon after the scope. Summary in the imperative, no trailing period.
- The body says why, not what. The diff already says what.
- Never add `Co-Authored-By`, "Generated with", or any mention of Claude or AI.
- Small commits, one logical change each, ordered so each one builds.

### PR description

One line on what changes for a user or caller. Then why. Then anything a reviewer must check
by hand (a migration, a config key, a docs change). No attribution footer, no checklist of
things CI already checks.

### Team update or announcement

What changed, who it affects, what they need to do (if anything), by when. Four lines is
usually enough. Link the PR or doc for depth.

### Technical post or course material

Start from the failure or the question, not the solution. Build the solution one step at a
time, each step answering the problem the previous one left. Compare against the previous
version in a table when the improvement is the point. Name what's still broken at the end;
it's the hook for the next part.

## Persian

When writing in Persian, write natively. Don't translate English sentence structure. Use
نیم‌فاصله (ZWNJ) correctly (`می‌شود`, `درخواست‌ها`), Persian punctuation (`،` `؛` `؟`), and
keep code identifiers, repo names, and commands in Latin script inside backticks. For
anything user-facing in both languages, see the `bilingual-copy` skill.

## Self-check before handing it over

1. Does the first line say what this is?
2. Is every "why" stated, and no "what" narrated?
3. Can any sentence be cut without losing information? Cut it.
4. Any sentence over ~25 words? Split it.
5. Any filler word from the list above? Remove it.
