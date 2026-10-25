# Ali's LinkedIn Hook Bank

A labeled library of hook **mechanisms** to retrieve and remix instead of writing from scratch.

> TODO(ali): Part 1 holds templates, not real posts. Replace each group's examples with your
> own hooks and their metrics (`imp` = impressions, `eng` = reactions+comments+shares ÷
> impressions) once you've pasted your posts into `ali-posts.md`. Delete any group you never use.

A hook is the **first two lines**: line 1 stops the scroll, line 2 re-hooks and earns the
"…see more". Brackets mark a real fact to fill in. Never ship a bracket with an invented value.

---

> The hook **principles** live in `SKILL.md`. This file is the example library.

# PART 1 — Mechanisms, with templates for Ali's topics

## 1. Number + stakes
Count welded to a reason to care in the same line.
- **[N] Go libraries I stopped writing myself.**
  Every one of them started as "it's only 50 lines".
- **[N] things I check before a backend service goes to production.**
  None of them are about the code.

## 2. Oddly specific receipt
Unrounded figures read as lived proof.
- **One index took a query from [real ms] to [real ms].**
  The query didn't change. The order of the columns did.
- **My open-source library just passed [real number] stars.**
  Here's what I'd build differently if I started again.

## 3. Bold colloquial declaration (+ ellipsis)
Casual confidence; line 2 opens the loop.
- **Your ORM is hiding the query that will page you at 3AM…**
  Here's how to see it before it does.

## 4. Concede-then-pivot
Grant the premise, redirect to the real tension. Highest ceiling for takes.
- **AI can write most of a Go service now.**
  The question is who still understands it six months later.
- **Microservices let teams ship independently.**
  Until they share a database. Then they're a distributed monolith.

## 5. Second-person stakes / threat reversal
- **Your retry logic is probably charging customers twice.**
  Here's the one table that stops it.

## 6. "Most people [do X wrong]…"
Overused. Rotate.
- **Most Go developers use `OFFSET` for paging.**
  It gets slower on every page, and the fix is one `WHERE` clause.

## 7. Dated milestone / origin
- **[N] months ago I started porting an AI agent workshop to Go.**
  Today it survives being killed mid-task. Here's what that took.

## 8. Self-imposed challenge / countdown
- **I have [N] days to ship [product] in two languages.**
  Here's the stack, and what I'm deliberately not building.

## 9. Anonymized story lead
A real conversation, role not name.
- **A teammate asked why our list endpoint ignores `?user_id=`.**
  The answer is the most important line in the handler.

## 10. Plain value offer + arrow
For giveaways and launches, the value is the hook.
- **I open-sourced the [library] we run in production 👇**
  [one line on the problem it removes].

## 11. Counter-intuitive / myth-bust
- **Deleting code was the best performance work I did this year.**
  Not caching. Not goroutines. Deleting.

## 12. How-to + friction removed
- **How to add row locking in Go without writing raw SQL…**
  Most people reach around their query builder. You don't have to.

## 13. Question / provocation
- **If your service can't be killed mid-request without side effects, is it done?**
  Mine wasn't. Here's the event log that fixed it.

---

# PART 2 — Borrowed hooks (15) from top creators

Patterns to adapt to Ali's voice and audience, not copy verbatim. Sourced from public teardowns and the creators' own posts; some are templates. The first three groups are **new mechanisms you don't currently use** — prime candidates for the rotation.

## 14. NEW — Norm-violation / expectation-break
Open by admitting you broke an unwritten rule, so the reader must know why. (Lara Acosta's signature.)
- "Hired a Gen-Z candidate without interviewing him." — Lara Acosta
- "I use psychology in my writing, but no one can tell." — Lara Acosta
- *Ali's version: "I told my team to delete the cache we spent a week building."*

## 15. NEW — Credential-stacked authority + number
Front-load the rep count as authority, then the payoff number. (Hormozi's core move.)
- "I've hired 4,000 people — here are the 3 questions I ask every time." — Alex Hormozi
- "I asked 100 of my customers why they paid me $2k+." — Lara Acosta
- "I've used 100s of tools to grow my LinkedIn. Here are my 3 (free) must-use tools." — Lara Acosta
- "I've written over [X] essays. These are the [N] formats that drove [%] of my growth." — Nicolas Cole [template]
- *Ali's version: "I've shipped [N] Go services to production. Here are the 3 things every one needed by month two."*

## 16. NEW — Two-paths / aphoristic contrast triad
Two mindsets or a 3-beat contrast that creates clean tension. (Sahil Bloom, Cole, Welsh.)
- "Everyone's fighting for attention. Nobody's fighting for trust. That's your unfair advantage." — Nicolas Cole
- "The 9-to-5 is getting pummeled. / The great resignation is growing faster than ever. / And I love it. Why?" — Justin Welsh (enemy → hero → teaser)
- *Ali's version: "Two teams adopted AI coding tools. One shipped faster. The other shipped more code nobody understands."*

## NEW — Bold outcome claim + system promise
State a big outcome or a flat verdict with no hedging, then promise the repeatable system behind it. The confidence *is* the appeal; hedging kills it. (Matt Gray's signature.)
- "I built a [$X] business working [N] hours a day. Here's the system." — Matt Gray [template]
- "Most people quit [X] in week one. Here are the [N] frames that get them to week ten 👇" [template]
- *Ali's version: "Durable agents aren't hard. Here are the 4 pieces that let one crash mid-task without doing anything twice 👇"*

## Reinforcers (mechanisms in Part 1, proven by others)
- "The Icarus Paradox: What makes you successful can lead to your downfall." — Sahil Bloom (paradox → your myth-bust #11)
- "The Smart Friends Razor: if your smartest friends are all into something, pay attention." — Sahil Bloom (named mental-model → #11)
- "I cracked LinkedIn's code in 8 moves." — Justin Welsh (number + mastery → #1)
- "X lessons I wish I knew before I [did Y]." — Justin Welsh [template] (regret/hindsight → #7)
- "I learned this tactic from Eminem — and it makes sales way more effective." — Alex Hormozi (unexpected-source curiosity → #13)
- "100 Viral Hooks from 100 Viral Posts." — Katelyn Bourgoin (mega-list tease → #1)
- "Bad marketing talks at customers. Great marketing joins the conversation already in their head." — Katelyn Bourgoin (friction-first contrast → #4)

---

# How to use this bank

**Weak openers (avoid):** an abstract trend with no person, number, or turn ("Cloud-native
adoption is accelerating…"). Lead with a concrete subject in the first four words: **I, you, a
number, or a named role**.

**Reach vs. replies:** broad, curiosity, and milestone hooks pull reach; opinion and identity
hooks (concede-then-pivot, "most people", story leads, norm-violation) pull replies. Pick the
lever before the mechanism.

**Structural constants:** two-line shape (claim → turn, whitespace between), ellipsis open loop,
first four words carry it, colloquial over corporate.

**The borrowed half of a hook menu.** Every menu is 10 candidates: 5 in Ali's voice, 5 in named
creators' registers from Part 2. Always name whose register each borrowed hook is in, so Ali can
say "more Sahil Bloom, less Hormozi" in three words. Say the trade-off too: these registers run
guru-ward against a peer voice, so a borrowed hook buys punch and spends credibility. That
should be a choice, not a drift.

**Rotation rule:** no mechanism repeats within ~3-4 weeks.
