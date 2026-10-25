# Non-Coding Skills

Claude skills for the parts of my work that aren't code: planning the day, tracking tasks,
writing emails and docs, shipping copy in English and Persian, preparing for meetings,
negotiating, and teaching.

They started as a fork of [ShawhinT/non-coding-skills](https://github.com/ShawhinT/non-coding-skills),
cut down to what fits how I work and rewritten around my tools: Claude Code on macOS, Trello,
Claude Docs, git repos under `~/go/src`, and two languages.

## Skills

| Skill | What it does | Depends on |
|-------|--------------|------------|
| **daily-briefing** | What's due on Trello, open PRs, and uncommitted or unpushed work across local repos. Read-only. | Trello MCP, git, `gh` (optional) |
| **trello-helper** | Turn a sentence into a well-formed card, checklist, or reminder; move and read boards | Trello MCP |
| **skimmable-summary** | House format for any digest, briefing, or status report, in English or Persian | None |
| **writing-style** | House style for READMEs, docs, PR descriptions, commit messages, and announcements | None |
| **email-helper** | Emails and work messages in my voice, English or Persian | None |
| **bilingual-copy** | Write and localise user-facing text between English and Persian (ZWNJ, register, RTL) | None |
| **conversion-copy** | Landing pages, app store and bot listings, product emails, and outreach that has to convert | None |
| **meeting-prep** | A one-screen brief before a client call, interview, pitch, or technical review | Web search, Trello MCP |
| **tactical-negotiation** | Chris Voss–style moves and wording for rates, scope, salary, and tech disagreements | None |
| **business-strategy** | A sparring partner for product and side-project decisions | Web search |
| **workshop-planner** | Plan a workshop or course session: the failure to teach, the steps, the README | Web search |
| **skill-helper** | Find and build the next skill worth having | skill-creator |
| **extract-chatgpt-transcript** | Save a shared ChatGPT conversation as clean Markdown | Browser tool |
| **cost-optimizer** | Estimate what a conversation cost and its break-even hourly wage | Python |

## What I left out, and why

The upstream repo has skills built around one business's stack. I dropped the ones that
depend on tools I don't use or work I don't do: the brand system, Notion CRM and its
satellites (crm, engagements, referrals, testimonials, sop-helper, notion-helper,
night-transcript-linker), Stripe, Google Drive and Calendar, LinkedIn analytics and voice,
newsletter and sales-letter writing, YouTube strategy, video, animation, graphic and Keynote
builders, proposal decks, and the skill-sync tooling. `notion-helper` and
`executive-briefing` came back as `trello-helper` and `daily-briefing`; `pre-call-research`
became `meeting-prep`; `workshop-use-case-researcher` became `workshop-planner`.

## Install

```sh
git clone git@github.com:aliworkshop/non-coding-skills.git
ln -s "$PWD/non-coding-skills/daily-briefing" ~/.claude/skills/daily-briefing
```

Link the ones you want into `~/.claude/skills/`, or point Claude at a skill's folder URL and
ask it to adapt the skill to you.
