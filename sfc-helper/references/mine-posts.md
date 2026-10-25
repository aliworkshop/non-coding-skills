# Mine mode: one painful post from Ali's own material

Turn raw material Ali already has into a single post. The sources are in SKILL.md ("Where raw
material comes from"): recent commits on the public repos, anonymized work lessons, Claude Code
memories, course sessions, and the backlog.

**Trigger:** "new post", "find me something to post from this week", "mine my commits for a post",
"یه ایده برای پست پیدا کن".

## The steps

- **Read efficiently.** Start with the 14-day git log across `~/go/src/aliworkshop` and the
  board's Backlog list. Open individual commits, READMEs, or memory files only for the 2-3
  candidates worth pursuing. Don't dump whole repos into context.
- **Audit against the board first.** An idea that fails the audit gets no hook and no draft.
  Run the dedupe check in `content-board.md` (Backlog/Scheduled, posted in the last ~4 weeks,
  hook freshness), per language.
- **Pick for pain, not coverage.** The idea that's widely felt by engineers, contrarian or
  surprising, and ties to a territory in `strategy.md`. One sharp pain beats a survey of the week.
- **Anchor on the real artifact.** Build the post around the actual commit message, the actual
  benchmark, the actual error, the actual line from a README. Don't paraphrase it away; it's the
  proof. Hand the draft to `linkedin-voice` and match the machinery to the format (a take gets no
  list; a teaching post gets the list).
- **Check privacy before handing over.** Nothing from work repos by name, no internal hostnames,
  ids, or colleague names, no paths from `~/.claude` in the post.
- **Close the loop after Ali edits.** Diff Ali's version against the draft, infer the principle
  behind each change, list them, and let Ali pick which ones stick. Feed those into
  `linkedin-voice` (via `skill-updater` if the skill is installed elsewhere).
