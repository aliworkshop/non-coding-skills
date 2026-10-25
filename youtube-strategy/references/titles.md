# Titles

The complete title workflow, click-driver principles, and reference examples.

## The 3-filter framework (applied to titles)

Every title that ships passes all three filters in order:

1. **A real avatar would search/click this.** Engineers search through YouTube, Google, ChatGPT, and Claude, often with the exact error or library name. Titles that aren't search-discoverable are also invisible to AI retrieval.
2. **It captures attention when scrolled.** Apply at least 2 click-driving principles from the stack below.
3. **It's specific enough to be ownable.** Generic titles ("Go tips for beginners") die. Name a precise thing — a company, a number, a mechanism, a named failure mode.

For sentence-level work on the title itself (does *this exact phrasing* hit?), use the visualize / falsify / unsignable filter from the `conversion-copy` skill. That's the canonical home for the line-by-line filter.

## The 19 click-driver principles

A great title stacks 2-3. Stacking too many produces a parody. Pick the right ones for the topic.

### Curiosity & subversion
1. **Curiosity gap.** Imply the viewer almost knows something but not quite. *"Why It Was Almost Impossible to Make the Blue LED" — Veritasium*
2. **Counterintuitive subversion.** Set up what they think they know, then suggest it's wrong. *"Software is completely oversold" — a16z*
3. **"But what is X?"** Subverts the assumption the viewer already understands. *"But what is a neural network? | Chapter 1, Deep learning" — 3Blue1Brown*
4. **"The truth about X."** Implies hidden information. *"The Truth About Why You Should Quit" — Ali Abdaal*
5. **Hidden origin / secret history.** *"How a Feud in Russia Led to Modern Prediction Algorithms" — Veritasium*

### Stakes & specificity
6. **Specific real numbers.** Big numbers grounded in reality. $456,000 > "lots of money." *"$456,000 Squid Game In Real Life!" — MrBeast*
7. **Extreme contrast.** *"$1 vs $1,000,000,000 Yacht!" — MrBeast*
8. **Stakes / consequences.** *"How a Single Phone Call Almost Toppled Citicorp" — Veritasium*
9. **Time scale.** *"This Deceptively Simple Math Problem Has Stumped Mathematicians for 300 Years" — Veritasium*

### Direct-to-viewer
10. **Direct address ("you" / "your").** *"Why Earth Is A Prison and How To Escape It" — Kurzgesagt*
11. **Personal pronoun + journey.** *"How I Take Notes - 5 Effective Strategies" — Ali Abdaal*
12. **Question form.** *"Is SaaS Dead? Do Margins Still Matter?" — a16z*

### Authority & framing
13. **Authority subversion.** *"Even the GOAT Tom Brady Can't Throw a Perfect Spiral. Here's Why." — Veritasium*
14. **"What if?" thought experiment.** *"What If We Nuke a City?" — Kurzgesagt*

### Format / signal
15. **Promise visible payoff.** The viewer should be able to roughly predict what they'll see and want to see it.
16. **"Chapter X" series framing.** *"...| Chapter 1, Deep learning" — 3Blue1Brown*
17. **Numbered sequels (1.0 / 2.0 / 3.0).** *"Glitterbomb 1.0 / 2.0 / 3.0" — Mark Rober*
18. **Topic specificity.** Name a precise thing, not a category.
19. **Series consistency.** Repeated framing turns the channel into *a* category.

## Avatar-first reframe (critical move)

When the topic uses jargon the avatar doesn't know (e.g., "idempotency keys"), the title should NOT name the solution — it should name the *pain* or promise the *outcome*. The video reveals the solution; the title baits the pain.

Example from real iteration:
- **Topic:** "How to build Claude skills better than 99% of people"
- **First-pass titles** (all assume audience knows what skills are): *"I Built 30+ Claude Skills. Here's What 99% of People Get Wrong."*
- **Reframed for a viewer who doesn't know "idempotency keys":** *"Why Your Payment API Charges Customers Twice"* — names the pain, leaves the mechanism as the reveal.

The test: read the title to a target avatar who's never used the product term. If they understand the pain or outcome promised, it's working. If they need to know the term to understand the title, rewrite.

## Real-world examples (reference benchmarks)

Study the stacks. Don't copy directly.

### Avatar-aligned
Illustrative patterns for a developer audience (templates, not real videos; replace with real reference titles from channels Ali admires):
- *"I Rewrote It in Go. Here's What Got Slower."* Stack: counterintuitive + personal + specific
- *"The One Postgres Index That Fixed Our API"* Stack: specific + curiosity gap + stakes
- *"Why Your Goroutines Leak (and How to Prove It)"* Stack: direct address + stakes + promise
- *"Build an AI Agent That Survives a Crash"* Stack: concrete outcome + named failure mode

### Educational benchmarks
- *"Why It Was Almost Impossible to Make the Blue LED"* — Veritasium. Stack: curiosity gap + time scale + hidden origin
- *"How One Company Secretly Poisoned the Planet"* — Veritasium. Stack: hidden history + stakes + curiosity gap
- *"This Deceptively Simple Math Problem Has Stumped Mathematicians for 300 Years"* — Veritasium. Stack: counterintuitive + time scale + specific number
- *"What If We Nuke a City?"* — Kurzgesagt. Stack: "what if?" + stakes + direct
- *"Why Earth Is A Prison and How To Escape It"* — Kurzgesagt. Stack: counterintuitive + direct address + payoff

### Big-creator benchmarks
- *"$456,000 Squid Game In Real Life!"* — MrBeast. Stack: specific real number + extreme spectacle + curiosity gap
- *"$1 vs $1,000,000,000 Yacht!"* — MrBeast. Stack: extreme contrast + specific numbers + curiosity gap
- *"How I Built a 1.2M Follower Audience in 6 Months"* — Hormozi. Stack: personal "How I" + specific number + time scale

## Title workflow

### Step 1 — Capture intent
Confirm:
- **Underlying pain or topic** in one sentence
- **Outcome** the viewer walks away with
- **Target click** — default: the viewer in the channel strategy doc (see SKILL.md). Confirm if different.
- **Constraints** (case study to ground in, company to mention, etc.)

If anything is unclear, ask one question. Don't generate in the dark.

### Step 2 — Generate 5-10 candidates
Each candidate:
- Stacks 2-3 principles (no more)
- Leads with a different principle stack from the others
- Passes the 3-filter framework

Mix forms deliberately:
- 1-2 question-form
- 1-2 specific-number
- 1-2 counterintuitive/subversive
- 1-2 personal "How I" or insider-commentary
- 1-2 "what if" / curiosity-gap

### Step 3 — Annotate each
For each candidate include:
- The title itself
- A 1-line note on which principles are stacked
- The likely search query an engineer would type or ask (filter 1 check)

### Step 4 — Rank and recommend
Pick the top 2-3 to ship and explain why. The strongest candidates lean on real numbers grounded in defensible reality (the edge over hype creators) and answer questions a real engineer would actually search.

## Common rough-idea → title transformations

Use as thinking patterns, not templates.

| Rough idea | Compelling title | Principles |
|---|---|---|
| Paging gets slow on deep pages | Why OFFSET Pagination Gets Slower Every Page (and the One-Line Fix) | counterintuitive + stakes + payoff |
| Retries cause double charges | Your Retry Logic Is Charging Customers Twice | direct address + stakes + specific |
| Agents redo work after a crash | Build an AI Agent That Survives kill -9 | concrete outcome + named failure mode |
| I tried a popular library and dropped it | I Used [library] for [N] Months. Here's Why I Removed It. | personal + specific + curiosity gap |
| Quick mental model for goroutines | Goroutines in 10 Minutes: The Mental Model I Wish I Had | time scale + payoff + personal |
| Rewrite results | We Rewrote It in Go. Here's What Got Slower. | counterintuitive + personal + specific |

## Output format

```
**Topic:** <one-sentence restatement>
**Avatar:** <who's the target click>
**Outcome:** <what the viewer walks away with>

**Title candidates:**

1. <Title>
   - Principles: <e.g., specific number + stakes + curiosity gap>
   - Likely search: "<query a real engineer would type or ask>"

2. <Title>
   - Principles: ...
   - Likely search: "..."

[...continue to 5-10]

**Top picks to ship first:** <2-3 titles + brief reason>
```

## Guardrails

- **Real numbers, not invented ones.** Big numbers work *only* when grounded in actual data. Every number in a title comes from a benchmark or measurement Ali actually ran.
- **Avatar appropriateness.** Manufactured stakes repel engineers. Lean closer to Fireship, ThePrimeagen, or a good conference talk: confident, specific, honest.
- **No clickbait.** The package is a contract.
- **Jargon is fine if it's searchable.** "goroutine leak" is a search term; "leveraging concurrency primitives" is noise. Use the words engineers type.
- **Specificity over abstraction, always.**
- **Series consistency where possible.** ("Durable Agents in Go: Part 1, Part 2…" or "How [Library] Does It")
- **Don't over-stack.** 2-3 principles is the sweet spot.

## When in doubt

Prefer the title that:
- Uses a real number over a vague claim
- Names a specific entity (company, person, mechanism) over a category
- Answers a question a real engineer would actually search
- Stacks fewer principles cleanly over more principles awkwardly

The avatar is sophisticated. They click on packages that respect their intelligence and promise real, specific information.
