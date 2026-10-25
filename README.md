# Non-Coding Skills

Claude skills for the parts of my work that aren't code: planning the day, tracking tasks,
writing emails and docs, shipping copy in English and Persian, preparing for meetings,
negotiating, teaching, and making content.

They started as a fork of [ShawhinT/non-coding-skills](https://github.com/ShawhinT/non-coding-skills),
rewritten around my tools: Claude Code on macOS, Trello,
Claude Docs, git repos under `~/go/src`, and two languages.

## Skills

Every skill from upstream is here. Four were rebuilt under new names because the tool they
wrapped changed: `executive-briefing` → **daily-briefing**, `notion-helper` → **trello-helper**,
`pre-call-research` → **meeting-prep**, `workshop-use-case-researcher` → **workshop-planner**.
Notion is replaced by Trello and Claude Docs throughout. Gmail, Google Calendar, Drive and
Stripe are optional connectors: the skills that use them say so and work without them where
they can.

Lines marked `TODO(ali):` inside a skill are data only I can supply (brand colours, voice
samples, board names). Fill them in before relying on that skill.

### Daily work

| Skill | What it does | Depends on |
|-------|--------------|------------|
| **daily-briefing** | What's due on Trello, open PRs, and uncommitted or unpushed work across local repos. Read-only. | Trello MCP, git, `gh` (optional) |
| **trello-helper** | Turn a sentence into a card, checklist, or reminder; move and read boards | Trello MCP |
| **calendar-helper** | Create, move, and delete calendar events; keep paired Trello cards in step | Google Calendar (optional), Trello MCP |
| **google-drive-helper** | Search and read Docs, Sheets, Slides, and PDFs in Drive | Google Drive MCP |
| **sop-helper** | Write, update, and look up repeatable procedures | Claude Docs |
| **night-transcript-linker** | Scheduled job that links each day's meeting transcripts to their cards or docs | Python, Trello MCP |
| **meeting-prep** | A one-screen brief before a client call, interview, pitch, or technical review | Web search, Trello MCP |
| **skimmable-summary** | House format for any digest, briefing, or status report, in English or Persian | None |

### Writing

| Skill | What it does | Depends on |
|-------|--------------|------------|
| **writing-style** | House style for READMEs, docs, PR descriptions, commit messages, and announcements | None |
| **email-helper** | Emails and work messages in my voice, English or Persian | None |
| **bilingual-copy** | Write and localise user-facing text between English and Persian (ZWNJ, register, RTL) | None |
| **conversion-copy** | Landing pages, app store and bot listings, product emails, and outreach that has to convert | None |
| **sales-letter-writer** | Long-form sales letters and one-pagers on Hormozi's offer principles | None |
| **linkedin-voice** | LinkedIn posts about Go, backend, open source, and launches | None |
| **newsletter-writer** | Newsletter or Telegram-channel editions in a consistent voice | None |
| **youtube-strategy** | Title, thumbnail, hook, and outro for a developer-audience video | None |
| **sfc-helper** | Content ideas mined from boards, git activity, and past sessions | Trello MCP |
| **linkedin-post-analytics** | Pull and analyse LinkedIn post performance | Browser tool |

### Clients, partners, and money

| Skill | What it does | Depends on |
|-------|--------------|------------|
| **crm** | Leads and contacts on a Trello CRM board; follow-ups by due date | Trello MCP, Gmail (optional) |
| **outreach** | 1:1 outreach campaigns to venues, partners, or freelance leads | Trello MCP, browser tool |
| **engagements** | Paid client engagements, start to finish | Trello MCP |
| **referrals** | Ask for, log, and trace referrals | Trello MCP |
| **testimonials** | Collect and polish testimonials and user quotes | Trello MCP |
| **stripe-helper** | Invoices, payment links, and reporting, if the business uses Stripe | Stripe MCP |
| **tactical-negotiation** | Chris Voss–style moves and wording for rates, scope, salary, and tech disagreements | None |
| **business-strategy** | A sparring partner for product and project decisions | Web search |

### Making things

| Skill | What it does | Depends on |
|-------|--------------|------------|
| **brand-system** | Brand template: colours, type (with Persian/RTL), voice, components | None |
| **graphic-builder** | Social graphics and figures in HTML, rendered to retina PNG | Python, headless Chrome |
| **animation-builder** | Short motion-graphic clips in HTML/CSS/SVG, rendered to MP4 | Python, Playwright, ffmpeg |
| **proposal-deck-creator** | A client or partner proposal deck (pptx) from notes | Node (pptxgenjs) |
| **keynote** | Read, create, and edit Apple Keynote files | macOS, Keynote |
| **training-proposal** | Proposals and outlines for technical training, converted to PDF | Python |
| **workshop-planner** | Plan a workshop or course session: the failure to teach, the steps, the README | Web search |
| **video-editor** | Propose cuts on raw recordings and generate FCPXML for Final Cut Pro | Python, ffmpeg, AssemblyAI |

### Skills about skills, and tooling

| Skill | What it does | Depends on |
|-------|--------------|------------|
| **skill-helper** | Find and build the next skill worth having | skill-creator |
| **skill-sync** | Link this repo's skills into `~/.claude/skills` | git |
| **skill-updater** | Update and repackage a skill in this repo | None |
| **extract-chatgpt-transcript** | Save a shared ChatGPT conversation as clean Markdown | Browser tool |
| **cost-optimizer** | Estimate what a conversation cost and its break-even hourly wage | Python |

## Install

```sh
git clone git@github.com:aliworkshop/non-coding-skills.git
ln -s "$PWD/non-coding-skills/daily-briefing" ~/.claude/skills/daily-briefing
```

Link the ones you want into `~/.claude/skills/`, or point Claude at a skill's folder URL and
ask it to adapt the skill to you.
