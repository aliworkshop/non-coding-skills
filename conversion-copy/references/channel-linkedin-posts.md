# Channel: LinkedIn Posts (meant to sell)

Use this framework when Ali is writing a LinkedIn post whose job is to drive conversion — launching an app or a Telegram bot, pushing an open-source library toward users and contributors, recruiting venues or beta testers, or opening freelance or consulting slots. Ali posts as a developer and founder, not as a brand.

This is **not** the framework for general thought-leadership posts, essays, or frame-setting content. Those follow the `writing-style` skill. Use this one only when the post has a conversion goal.

## Before you draft

Lock these:

- **What's being sold?** Specific offer, price (if relevant), link or CTA.
- **Where is this person in Ali's world?** Cold (scrolling feed, first exposure) or warm (follows Ali, has seen the projects)? This shapes how much setup you need.
- **The sharp angle.** Selling LinkedIn posts live or die on a sharp angle — contrarian claim, specific pain point, named competitor. The feed is noisy; neutral posts get skipped.
- **Customer-language source.** Even for a post, real customer phrases make it hit harder.

## Core principles (LinkedIn-specific)

### 1. The first line is the post

LinkedIn shows ~2 lines before the "...see more" cutoff. If the first line doesn't make someone expand, nothing else you wrote matters.

- Open with tension, specificity, or a confession. Not a setup paragraph.
- Questions work if they're sharp. Hooks work if they're concrete.
- Kill "In today's fast-paced world..." openers. Real people don't start sentences that way.

**Weak openers:**
- "Excited to announce my new app!"
- "I've been thinking a lot about Go lately..."
- "In today's business landscape..."

**Strong openers:**
- "Last week a venue owner told me our app filled a Tuesday they'd written off."
- "Most Go services write the same list endpoint four times. Here's how to write it once."
- "I've done this wrong 4 times. Here's the version that finally worked."

### 2. One idea per post

A selling LinkedIn post is not a sales letter. It makes ONE point, lands it, and offers ONE next step. Trying to cover multiple angles dilutes both.

- Pick the sharpest angle and commit. You'll write the next post next week.

### 3. Be easy to sum up

Harry: *"If you want to grow on social, make yourself easy to sum up."* A post should be summarizable in one sentence your reader can repeat.

- If someone read your post and a friend asked "what was it about?", what's the one-sentence answer?
- If that one-sentence answer is vague ("something about AI"), the post isn't sharp enough.

### 4. Be useful on the platform, don't redirect

The Kyiv Independent beat the Kyiv Post 5-to-1 in followers because they gave the value *inside the tweet*, not behind a link. LinkedIn rewards the same pattern.

- Don't bury the valuable content behind "click the link to learn more."
- Give the insight in the post. The CTA is an offer for *more*, not the insight itself.
- This is counterintuitive — giving away the gold in the post *increases* conversions on the attached offer because it proves the offer's quality.

### 5. Stories beat facts

Stories are memorable. Facts get skimmed.

- If you have a client anecdote (with permission and anonymized as needed), lead with it.
- "Last week a venue owner told me..." beats "40% of venues struggle with..."
- The story should demonstrate the problem/solution, not just illustrate a point.

### 6. Show your work, don't claim credentials

Developers and founders are a sophisticated audience. They can smell a credential-drop from a mile away. Instead:

- Show the before/after screenshot.
- Paste the actual customer DM (anonymized).
- Share the diagram, the benchmark, or the diff, not the abstract description.
- Point at the artifact — don't claim the outcome.

### 7. Low-friction close over "book a call"

The post's job is to create the next step, not close the sale. Match the CTA to where the reader is in the funnel:

- **Too aggressive:** *"Book a discovery call here."*
- **Right-sized:** *"Comment 'beta' and I'll DM you the TestFlight link."* / *"Comment 'lists' and I'll send the repo."* / *"Run a venue? DM me 'venue' and I'll send the 1-minute walkthrough."*
- **Soft:** *"Repo in the comments."*

The best CTA on LinkedIn is usually a comment prompt — it also boosts reach.

## Structure (default)

Most selling LinkedIn posts follow one of these shapes:

**Shape A — The Story**
1. Hook (specific scene / confession / claim).
2. 2–4 short paragraphs developing the story.
3. The lesson or insight.
4. The offer tied to the insight.
5. CTA (low-friction next step).

**Shape B — The Contrarian Take**
1. Hook (contrarian claim).
2. Why most people get this wrong.
3. What actually works (concrete, demonstrated).
4. The offer tied to the approach.
5. CTA.

**Shape C — The Proof Drop**
1. Hook (specific client result).
2. Quick context (who, what they tried before).
3. What changed.
4. How they got there.
5. Offer + CTA.

## Which universal principles matter most here

- **#9 Create momentum** — the first line especially. On LinkedIn, this principle is life-or-death.
- **#2 Use the customer's voice** — quote actual DMs, actual calls. Anonymized but verbatim.
- **#7 Don't persuade, let them be persuaded** — advice-shaped posts outperform pitch-shaped posts 10x on social.
- **#10 Memorable beats likeable** — the post is competing with dog photos. Be sticky, not polite.

## Voice cues

- Short paragraphs (1–3 lines each). LinkedIn formatting rewards white space.
- Don't use hashtags unless there's a specific reason. They make the post look like a brand wrote it.
- Don't tag people unless they're genuinely central to the post. Tag-bait is transparent.
- Read it aloud. If it sounds like a brand statement, rewrite.

## Worked example — a selling LinkedIn post

**Offer:** an open-source Go library Ali maintains under aliworkshop. The post's job is real users and a few contributors.

**Weak draft:**
> *Excited to announce the release of my new Go library! 🚀*
>
> *In today's fast-paced development landscape, building robust, scalable APIs is more important than ever. That's why I created a powerful, flexible toolkit that empowers developers to supercharge their backend workflows.*
>
> *Check it out and let me know what you think! #golang #opensource #backend*

**Filter check:** Every line fails visualize, falsify, and unsignable. No sharp angle. "Landing page words" everywhere.

**Rewrite — Shape B (contrarian take, problem-led):**

> Most Go services I've reviewed write the same list endpoint four times.
>
> Paging in one, sorting in another, a `?status=` parser in the third, and a fourth that forgot all three.
>
> So I pulled that into one place. You declare which columns a list may filter on. Paging, sorting, and `?status=a,b` work everywhere, the same way.
>
> It's been running in production for [real duration, from Ali]. The list handlers went from [real before] lines to [real after].
>
> Repo in the comments. If you want help wiring it into an existing service, comment "lists" and I'll DM you.

**Why this works:**
- Hook passes the filter (specific and falsifiable: "the same list endpoint four times").
- Names the real enemy (copy-pasted, drifting handlers) instead of a vague "complexity."
- Shows the alternative concretely (declare a whitelist, the rest works).
- Proof slots stay as placeholders until Ali gives real numbers. Never fill them with guesses.
- Low-friction CTA (comment "lists").
- Zero landing-page words.

## Common failure modes

1. **Announcement-style openers.** "Excited to announce" is the death rattle of LinkedIn posts. Replace with a scene or a claim.
2. **Hashtag blocks at the bottom.** They scream "brand wrote this."
3. **Emoji-heavy formatting.** One sparing emoji can work. Five makes you look like a content team.
4. **Generic "limited time" scarcity.** Either make the scarcity real and specific or cut it.
5. **Asking for a "quick call" in the post.** That's too big a jump from a first exposure. Offer a comment-prompt or DM-prompt instead.
