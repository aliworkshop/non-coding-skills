---
name: sop-helper
description: >
  Create, update, and pull up Ali's standard operating procedures (SOPs) and runbooks. SOPs
  live as Claude Docs (or as markdown files in a repo Ali names). Use whenever Ali wants to
  turn a process into an SOP, update one, or walk through one. Triggers: "write/update the SOP
  for X", "document this process", "turn this into a runbook", "where's the SOP for X", "walk
  me through the release checklist", "let's save this", "I keep redoing this, write it down",
  "یه چک‌لیست برای X بنویس". Also load before reasoning about what an SOP should say. Do NOT
  use for one-off tasks (those are Trello cards via trello-helper) or for project
  instructions that belong in a repo's CLAUDE.md.
---

# SOP Helper

Ali's SOP manager. It captures repeatable processes (releasing a library version, onboarding
a client, running a workshop session, rotating a secret, publishing an app update) as tight,
checklist-style references that Ali, teammates, and future Claude runs can follow. Not a
process manual.

If it happens once, it's a Trello card. If Ali will do it again and wants a reference, it's
an SOP.

## Where SOPs live

**Default: Claude Docs.** One doc per SOP, plus one index doc that lists them by category.
Before any docs call, load the docs skill or the Claude Docs `guide` (`topic.index`) as the
connector's instructions require.

| Thing | Where |
|---|---|
| SOP index doc | `TODO(ali):` link once created |
| Categories | `TODO(ali):` e.g. Releases · Clients · Teaching · Ops |

**Alternative: a repo.** When Ali names a repo for SOPs, each SOP is `sops/<slug>.md` and the
index is `sops/README.md`. Edit files as text. Committing and pushing wait for Ali's word.

When the index doesn't exist yet, offer to create it on the first SOP. Add every new SOP under
a category heading. No obvious fit? Suggest extending a category or adding one; don't drop it
at the bottom.

## Format (keep it minimal)

An SOP opens with one **Context** line, then a chronological spine of steps, then templates.
Read top to bottom, it's the workflow in order.

- **`**Context**:` first.** One sentence: what this is and when it happens.
- **Top-level bullets are the steps**, in order, step name in bold. Common shape:
  **Trigger → Prep → Do → Verify → Follow-up**. Use whatever order the process really has.
- **Detail nests under the step that uses it.** Commands, checks, question banks.
- **Edge cases inline**, under the step where they come up. No "Edge cases" section at the end.
- **Commands in code blocks**, exactly as run, so they can be copied.
- **`**Links**`** near the bottom: the repos, boards, dashboards, and docs this SOP touches.
- **Templates last**, below a `---` divider: emails or messages, each with a `Subject:` line
  and an italic note on when it's sent, body in a fenced block. Variants A/B when one step
  needs more than one, each with its own **Context** line.

No Purpose, Scope, Owner, Version, or Last Updated sections unless Ali asks.

### Skeleton

````
**Context**: one sentence — what this is and when it happens

- **Trigger** — what starts it
- **Prep**
	- Sub-step
- **Do**
	- Sub-step
	```sh
	exact command
	```
	- Edge case: handled here, where it comes up
- **Verify** — how to know it worked
- **Follow-up**
**Links**
- [Board / repo / doc](url)

---
Subject: <subject> *(what it is — when it's sent)*
```plain text
<body>
```
````

### Style

- Short imperative bullets: "Tag the release", not "The release should be tagged."
- Two levels of nesting; three is a smell.
- Keep Ali's shorthand (FU, PR, CI). Don't expand it.
- Write per `writing-style`. Persian SOPs are written natively in Persian, commands and
  identifiers stay in Latin script.

## What belongs in an SOP

**SOP vs. skill.** The SOP owns intent, policy, and content: steps, decisions, templates,
written so a person without Claude could follow it. A skill owns execution: tool calls, IDs,
payloads. A fact lives in one of them, and the other points to it.

**Codify only what's real.** Steps, edge cases, and templates come from what Ali actually did
or sent. Don't invent edge cases to look thorough. An empty section is honest; an invented one
misleads.

**Templates feed `email-helper`.** Keep them plain text. When Ali sends an edited version of a
templated email, propose updating the SOP so the next draft starts from the current one.

## Creating an SOP

1. **Search first.** Look in the index (or `sops/`) for the likely title and keywords. If
   something close exists, ask: update it, or create a new one beside it? One SOP per process.
2. **Draft in the conversation first.** Extract the repeatable core: ordered steps with the
   one-off specifics (dates, names, this week's numbers) stripped out, sub-steps where real,
   templates lifted to the bottom. If Ali's description is thin, ask one or two questions.
   Don't invent a process.
3. **Pick the category.** Ask if it's unclear.
4. **Create** the doc (or file) and **add it to the index** under its category.
5. **Confirm briefly:** title, category, link. Don't re-summarise the steps.

## Updating an SOP

1. Find it and read it fully.
2. Make a **targeted edit** to the relevant section. For a full rewrite, confirm scope first:
   a rewrite can drop detail Ali has forgotten is there.
3. No revision metadata.

## Pulling one up

- **Reference:** link plus the top-level checklist if useful. Don't dump the whole thing.
- **Walk-through:** step through it one item at a time, waiting for Ali to confirm each before
  the next. The SOP becomes a runbook.
- **None exists:** say so and offer to draft one.

## Keeping the library tidy

When asked, or when it's obviously drifting: promote placeholder entries to real SOPs, propose
merging near-duplicates, flag steps that reference tools or repos that no longer exist.
Propose; don't silently restructure.

## Rules

- Repeatable processes only. One-offs go to `trello-helper`.
- Match the format above.
- Mechanics in skills, content in SOPs.
- Codify only what's real.
- Search before creating.
- Link every SOP from the index.
- Big edits need confirmation.
