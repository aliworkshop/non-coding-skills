---
name: sales-letter-writer
description: Draft long-form sales letters and one-pagers for Ali's offers (freelance and consulting packages such as a backend audit or build sprint, paid workshops and courses, premium tiers of Ali's products) using Hormozi's $100M Offers principles. Use this skill whenever Ali asks to write, draft, or iterate on a sales letter, one-pager, offer page, landing page copy, sales page, "offer brief," or any long-form copy designed to sell a specific paid offer. Triggers include "write a one-pager for X", "draft a sales page for my new offer", "help me write the sales letter for my [sprint / audit / workshop / course / premium plan]", "turn this offer into a sales page", or any time Ali is putting together written copy whose job is to sell a specific package. Even casual mentions like "I need to write up my new offer" or "let's put the offer in writing" should trigger this skill. Do NOT use for short-form content like LinkedIn posts, tweets, or newsletters (use linkedin-voice or newsletter-writer instead) — this skill is specifically for long-form sales copy that walks a buyer from headline to CTA.
---

# Sales Letter Writer

Draft long-form sales letters and one-pagers for Ali's offers, section by section, using Hormozi's $100M Offers principles. The output is a one-pager that someone could paste into a Claude Doc, a README, or a landing page and use to actually sell.

**Sentence-level craft:** When drafting individual sections, apply conversion-copy's 3-question filter sentence by sentence. Every headline, subhead, bullet, and CTA must pass visualize / falsify / unsignable before it ships. This skill owns structure, value equation, bonus design, and naming — conversion-copy owns the sentence-level craft.

## The non-negotiable workflow

Sales letters are too high-stakes to one-shot. Drafting one without context produces generic, unconvincing copy. Follow this loop every time:

1. **Interview first.** Never start drafting until you've locked the core inputs (see "Interview checklist" below). If Ali hasn't given them, ask. If a Claude Doc, Trello card, or other doc was linked, fetch it before asking — most of the answers are usually already written down somewhere.
2. **Section by section.** Draft one section at a time. Present it. Iterate with Ali. Lock it. Move on. Never draft the whole letter in one shot, even if it seems slower — the quality difference is enormous.
3. **Offer 3+ options when iterating.** When Ali pushes back on a draft, give at least 3 alternative phrasings/angles, then state your top pick with reasoning. Don't just rewrite once and hope.
4. **Push back honestly.** If a section is weak, padding, or doesn't earn its keep, say so. Evaluate it against the value equation (see below) before defending it. Ali would rather you cut a weak Step 3 than keep it for symmetry.
5. **Save the locked draft when done.** Either save to the user's outputs folder or, if Ali points to a Claude Doc, write it there. Ask before writing anywhere shared.

## Interview checklist

Before drafting anything, you need clear answers to:

- **Avatar.** Who *exactly* is this for? Narrow > broad. ("seed-stage startups whose Go API falls over under their first real traffic" beats "startups that need backend help.")
- **Dream outcome.** The clear, measurable result they get. Numbers help, but only real ones ("p99 under [real target] at [real load]").
- **Timeframe.** How long until they get the result. Shorter feels better.
- **Mechanism.** The specific framework, process, or thing you do that makes the outcome possible. This is the wedge against commodity competitors.
- **Pains in their language.** The exact phrases the avatar uses for their problem ("it works on my laptop", "we're scared to deploy on Fridays", "nobody understands the old service"). Use *their* words, not yours.
- **What they want to avoid.** The effort/sacrifice they're trying to dodge (a full rewrite, hiring a full-time senior engineer, months of migration, downtime). This becomes your anti-effort anchor.
- **Container.** The format/wrapper (audit, sprint, workshop, course, retainer, premium plan).
- **Price + scarcity + payment terms.**
- **Guarantee.** What risk reversal can you offer.
- **Bonuses.** Things you already have or can deliver cheaply that solve "the next problem after they buy."
- **CTA.** What's the exact next action you want them to take (book a call, fill an application, etc.)?

If Ali has linked a doc, read it first and pre-fill as much of this as you can. Then ask focused questions to fill the gaps. Don't make Ali retype things you can find yourself.

## The value equation (the universal lens)

Every section, every bonus, every word should move at least one of these levers:

- **↑ Dream outcome** — make the result bigger or more vivid
- **↑ Perceived likelihood of success** — make them believe it'll work for *them*
- **↓ Time delay** — make the result feel closer
- **↓ Effort & sacrifice** — make the path feel easier

When evaluating any section, bonus, or process step, ask: *which lever does this move?* If the answer is "none," cut it or rework it.

## The 7-section one-pager structure

Always use this structure unless Ali says otherwise. Each section has a formula. Walk through them in order.

### 1. Header Block (Headline + Subhead)

**Headline formula (M.A.G.I.C.):** `[Avatar] + [Dream Outcome] + [Timeframe] + [Format/Container]`

The headline encodes the value equation in one line: big dream outcome, short time, low effort. Lead with a visceral verb when possible ("ship," "cut," "stop paging") instead of soft verbs ("get," "have").

**Subhead formula:** `For [specific avatar] who [current painful situation] and want [dream outcome] without [biggest thing they want to avoid].`

The subhead is where you mirror the avatar's exact pain language and stack the things they want to avoid. The "without" clause is critical — it's your anti-effort anchor.

### 2. "This Is For You If…" (Qualifier)

3–7 bullets. Each bullet formula: `You are [identity/role] who [specific problem, frustration, or desire].`

The job of this section is to make the right reader feel called out by name (the "cocktail party effect") and filter out the wrong ones. Use the avatar's own language. Each bullet should hit a different pain or desire — don't repeat yourself. Cover: identity, the "it mostly works but we don't trust it" feeling, the "we tried a contractor and got a black box" frustration, the specific problem eating their week, the "we can't stop shipping features to fix this" objection, and the alternative they're considering instead.

### 3. Core Promise Block

A short paragraph (2–4 sentences). Formula: `In [short time interval], we will help you get [clear, measurable dream outcome] using [your mechanism] so you can [emotional payoff], without [major effort or sacrifice they fear].`

This is your Grand Slam Offer in words. Name the mechanism explicitly (it's your category-of-one differentiator). The "without" clause should list 2–3 specific things they fear (e.g., "no rewrite, no feature freeze, no new stack to learn"). Avoid generic anti-effort anchors like "without the hassle" — be specific.

### 4. What You Get (Deliverables + Bonuses)

Split into two clearly labeled mini-lists.

**Core Deliverables** — 3–7 bullets. Each bullet formula: `[Tangible thing they receive] so that you can [immediate practical benefit].`

**Bonuses** — 2–5 bullets. Each bullet formula: `Bonus: [extra asset/support] to help you [reduce effort, reduce risk, or get results faster].`

Bonuses are not random extras. They are levers on the value equation aimed at "the next problem after they buy." See `references/bonus-design-playbook.md` for the full design principles and pre-flight checklist. Audit every bonus against that checklist before presenting it.

### 5. How It Works (Process)

3 simple steps. Each step is 1–2 sentences answering: what happens, when, and who does what.

- **Step 1: [Name]** — what happens before the engagement starts (intake, prep, kickoff)
- **Step 2: [Name]** — what happens during delivery (the core mechanism in action)
- **Step 3: [Name]** — what happens at the end (handoff, roadmap, lock-in)

If a step doesn't earn its keep, cut it. A weak Step 3 is worse than no Step 3. Test each step against the value equation: which lever does it move? If it doesn't move any, kill it or reframe it. (For example: a "handoff call" that only walks through the diff is weak. A written runbook plus a 60-day plan for the issues not fixed in the sprint directly attacks the "what happens after you leave?" objection — that earns its keep.)

### 6. Guarantee

Use one or two clear guarantees that kill risk. Single-tier formula: `If [specific result or milestone] does not happen by [timeframe] and you have [simple conditions they must meet], then I will [refund, redo, or add extra service].`

For premium offers, a two-tier guarantee is stronger:
- **Wage-payment guarantee on Session 1** — "If our first session isn't worth at least your hourly rate, I'll pay you for your time." This kills the "what if I waste my morning" objection.
- **Outcome guarantee at the end** — "If by Day [X] you don't have [specific minimum result], and you've shown up to every session and done the work, I'll keep working with you for free until you do." This kills the "what if it doesn't work" objection.

The minimum result in the outcome guarantee should be the *floor* of your headline range, not the average — this keeps the promise believable. ("If the headline says p99 under 300-500ms, guarantee 500.")

### 7. Investment, Scarcity, CTA

Three short blocks:

- **Investment:** `[Price] for everything above. [Payment terms.]`
- **Availability:** `Only [number] [slots/spots/seats] available. [Why scarcity is real.]`
- **Next Step:** `[What to do] by [how to do it] [when/urgency], and you'll [what happens next].`

Scarcity must be real, not invented. Tie it to your actual capacity. The CTA should be one specific next action — book a call, fill an application, reply to an email — and tell them what happens immediately after.

## Persian offers

An offer for a Persian-speaking audience is written in Persian from the start, not translated (see `bilingual-copy`). Prices use the currency the buyer pays in. Check the guarantee wording with Ali, since what counts as a credible guarantee differs by market.

## Voice and style

For Ali's voice (`writing-style`), the "landing page words" ban list, and all sentence-level craft rules (visceral verbs, em-dash restraint, concrete over abstract), see conversion-copy's **Voice and style** section — that's the canonical source. Apply those rules to every section drafted here.

## Naming offers

If Ali needs to name (or rename) the offer itself, use the naming playbook. See `references/naming-playbook.md` for the M.A.G.I.C. naming formula, container word library, and the full set of naming principles. Always offer a shortlist of options grouped by direction (outcome-first, mechanism-first, identity-first, etc.) and give a top pick with reasoning. Then remind Ali that the market decides — pick something clear enough to ship and let the data sort it out.

## When iterating with Ali

- If Ali says "iterate on X" or "give me options," provide at least 3 alternative phrasings and state your top pick.
- If Ali says "make it shorter," cut ruthlessly. Don't preserve cute phrases.
- If Ali provides new context mid-draft (a doc, a customer quote, a specific pain), weave it in immediately and explicitly note where you used it.
- If Ali locks a section, repeat it back verbatim before moving on so there's no ambiguity about what's locked.
- If Ali changes a structural element (e.g., dropping a process step, merging two bonuses), check whether other sections need to update for consistency and surface the conflict before making the change.

## Worked example

For a complete worked example of this workflow producing a finished one-pager, see `examples/backend-audit-sprint-one-pager.md`. It's an illustrative offer (a freelance Go backend audit sprint) with bracketed placeholders where real prices and numbers go — useful as a reference for tone, structure, and depth, not as facts.
