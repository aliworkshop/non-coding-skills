---
name: skill-sync
description: Sync the skills in Ali's skills repo (github.com/aliworkshop/non-coding-skills) into ~/.claude/skills as symlinks, check what's linked, add or remove one, and show what changed in the repo. Use whenever Ali asks to sync skills, install a skill from the repo, link a new skill, "what skills do I have", "is X installed", "remove X from Claude Code", "skills status", "اسکیل‌ها رو سینک کن". Do NOT use for writing or editing a skill (that's skill-creator / skill-updater). Never commits or pushes unless Ali asks in that turn.
---

# Skill Sync

Ali's skills have one source of truth: the git repo **aliworkshop/non-coding-skills**. Claude
Code reads skills from `~/.claude/skills`. This skill keeps the two joined with **symlinks**, so
an edit in the repo is live immediately and there is never a second copy to drift.

## Paths

- **Repo:** `$SKILLS_REPO` if set, else `TODO(ali):` the local clone path. If neither is known,
  ask once. Clone with `git clone git@github.com:aliworkshop/non-coding-skills.git` when missing.
- **Target:** `~/.claude/skills`.

`~/.claude/skills` also holds skills from elsewhere (other folders, plugin syncs, a `.trash`).
**Only touch entries that are symlinks into the repo.** Anything else is left alone, even if
its name matches a repo skill. Report the clash instead.

A repo skill is any top-level directory containing a `SKILL.md`.

## Operations

### status (read-only, no confirmation)

```sh
R="$SKILLS_REPO"; T=~/.claude/skills
for d in "$R"/*/; do s=$(basename "$d"); [ -f "$d/SKILL.md" ] || continue
  if [ -L "$T/$s" ] && [ "$(readlink "$T/$s")" = "${d%/}" ]; then echo "linked     $s"
  elif [ -e "$T/$s" ]; then echo "CLASH      $s (exists, not our link)"
  else echo "not linked $s"; fi
done
for l in "$T"/*; do [ -L "$l" ] && [ ! -e "$l" ] && echo "BROKEN     $(basename "$l") -> $(readlink "$l")"; done
git -C "$R" status --short; git -C "$R" fetch -q && git -C "$R" log --oneline HEAD..@{u}
```

Show linked / not linked / clashes / broken links, uncommitted changes in the repo, and commits
on GitHub not yet pulled.

### sync (dry-run, confirm, apply)

1. **Dry-run:** list what would happen: `LINK <skill>` for repo skills not linked,
   `UNLINK <skill>` for broken symlinks that pointed into the repo (the skill was removed or
   renamed), `CLASH <skill>` for names taken by something else.
2. **Show the plan.** If it's empty, say "Nothing to sync" and stop.
3. **Confirm, then apply:**

```sh
ln -s "$R/<skill>" ~/.claude/skills/<skill>     # LINK
rm ~/.claude/skills/<skill>                     # UNLINK — only a broken symlink, never a directory
```

`rm` on a symlink removes the link, not the repo folder. Never `rm -r` anything under
`~/.claude/skills`.

If the repo is behind GitHub, offer `git -C "$R" pull --ff-only` first. Pulling changes Ali's
working tree, so ask; don't pull on your own.

### add / remove one skill

- "Install X" → `LINK X` (confirm if it clashes).
- "Remove X from Claude Code" → delete only the symlink. The skill stays in the repo. To retire it
  for good, it has to be deleted from the repo too, which is a commit, so it waits for Ali.

## Publishing a new or edited skill

When a skill was written or changed in the repo:

1. Show `git -C "$R" status --short` and `git -C "$R" diff --stat`.
2. Stop there. **Committing and pushing are Ali's call, asked for in that turn.** "Commit" means
   one commit and doesn't imply a push. When asked:
   - Commit message per `writing-style`: `feat(<skill>) Add …` / `fix(<skill>) …`, body says why.
   - No `Co-Authored-By`, no "Generated with", no mention of Claude.
   - One commit per skill when several changed.
3. If the skill was written somewhere else first (a project's `.claude/skills/`), move it into the
   repo and link it, so there's one copy.

## Troubleshooting

- **Broken links after a rename:** run sync; it offers `UNLINK` for the old name and `LINK` for
  the new one.
- **A skill doesn't show up in Claude Code:** check the link resolves (`ls -L`) and that
  `SKILL.md` has valid frontmatter with `name` equal to the folder name and a `description`
  under 1024 characters.
- **Clash with a non-link folder:** report it. Ali decides which one wins.

## Doesn't

- Create or edit skills (`skill-creator`, `skill-updater`).
- Touch skills outside the repo, plugin-managed folders, or `.trash`.
- Commit, push, or pull without being asked.
