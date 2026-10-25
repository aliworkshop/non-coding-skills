# Startup Principles

Fourteen principles that recur across ~20 years of Y Combinator writing and talks,
weighted by Lindy. Not an official list — YC publishes no numbered canon.

**Calibration.** YC's advice is tuned to maximize expected value across thousands of
bets in which roughly half go to zero and about ten companies produce most of the
returns. Ali plays one round, once, with limited hours. Advice that is rational for
a portfolio holder is often irrational for a single non-repeating player — so read
every principle below asking "does this survive when I only get one try?"

**Scope.** PG draws the boundary himself in *Startup = Growth* (2012): a startup is
"a company designed to grow fast," and a business not designed for rapid growth
isn't the subject. Ali is an engineer-founder building products (a consumer app, dev
tools, bots) with limited time and a small team, so several of these change
shape. Translation lines follow where they do.

**1. Make something people want.**
YC's motto since 2005 (PG, *Be Good*, 2008). The common failure isn't building
badly — it's building well for nobody.

**2. Notice problems; don't think up ideas.**
PG, *How to Get Startup Ideas*, 2012: "The verb you want is not 'think up' but
'notice.'" The best ideas are ones the founder personally needs.

**3. Be persistent about the goal, not the plan.**
PG, *The Right Kind of Stubborn*: "The persistent are attached to the goal. The
obstinate are attached to their ideas about how to reach it." Changing approach is
fine when each version reuses the last; restarting from scratch is the warning sign.

**4. Talk to users — carefully.**
Ralston & Seibel, *YC's Essential Startup Advice*. But naive execution produces
confident garbage: compliments, hypothetical fluff, and wishlists (Fitzpatrick,
*The Mom Test*). Ask about past behavior, never pitch, and treat false positives as
more dangerous than bad news.
→ Ali: watch what people already do — which events they join, which bot commands they
run, which issues they open on a library. Behaviour beats a survey of wishes.

**5. Launch fast — but never spend reputation.**
PG, *Startups in 13 Sentences*, 2009: "you haven't really started working on it till
you've launched." The "embarrassed by v1" line is Reid Hoffman's, not PG's.
Counterweight: Rand Fishkin's Moz shipped MVPs and earned a lasting reputation for
crappy software.
→ Ali: ship to a small closed group first (invite-only suits this). Anything public —
an app store listing, a library release — ships good, because a bad launch spends trust
you can't rebuy.

**6. Do things that don't scale.**
PG, July 2013. Manual recruiting, onboarding, and delivery are how you learn what's
worth automating. YC re-hardened this in 2026: customers 1–3 come from your network,
4–10 from unscalable effort, and tooling only matters from 10–50.
→ Ali: the engineer's trap is automating before anyone uses it. Onboard the first
members and venues by hand; build the admin screen after you've done the job manually
enough times to know its shape.

**7. Make it stick before you pour fuel on it.**
Scaling a leaky bucket makes you fail faster. Retention is the precondition for
growth being real rather than churn-masked.
→ Ali: for the app, it's members who come back for a second event; for a library,
users who upgrade rather than fork; for a bot, people who use it the next week.

**8. A few customers who love you beat many who kind of like you.**
Ralston & Seibel; Altman, *Startup Playbook*, 2015. Intensity of desire is the
signal, breadth is the vanity metric. Firing a bad-fit customer is cheap; doing it
late is expensive.

**9. Know your one number and check it weekly.**
PG, *Startup = Growth*: the growth rate makes your decisions for you. Skip the
5–7%/week benchmark — it's a batch artifact and doesn't survive extrapolation.
→ Ali: pick one per product — weekly active members, repeat attendance, paying venues —
and ignore the rest until it moves.

**10. Know whether you're default alive.**
PG, October 2015. Most startups die of running out of time and learn their real
position too late.
→ Ali: the salary covers the burn, so money rarely kills the product. Time does. The
useful version is: at the hours you actually have, when does this ship, and is that
still worth it?

**11. Ask where the hard bit is.**
Tom Blomfield, 2026: writing software used to be the hard part and no longer is. If
nothing about your business is hard, you don't have one.
→ Ali: with code cheap, the hard bits are distribution, trust, and (for the app) the
two-sided cold start between members and venues.

**12. Startups die of suicide, not murder.**
Altman, *Startup Playbook*, 2015: "Competitors are a startup ghost story." PG's
version: "Competitors are rarely what kills startups. Poor execution does."
→ Ali: part-time, so the failure mode is starting the next project before this one
finished — quiet abandonment, not a competitor.

**13. Speed is your only early moat.**
Proposed by YC in 2025 as an eighth Helmer power. Incumbents beat you on capital,
brand, and distribution; cycle time is the one axis you can win on.

**14. Focus is sequential.**
Do one thing until it works. A list of parallel priorities is a to-do list, not a
strategy. Balanced by principle 3 — focus on execution, not on being right.
(Matches the lead-domino principle in SKILL.md.)

---

## Sources

Primary, verified:

- PG, [Be Good](https://paulgraham.com/good.html) (2008) — origin of the motto
- PG, [How to Get Startup Ideas](https://paulgraham.com/startupideas.html) (2012)
- PG, [The Right Kind of Stubborn](https://paulgraham.com/persistence.html)
- PG, [Startups in 13 Sentences](https://paulgraham.com/13sentences.html) (2009)
- PG, [What Startups Are Really Like](https://paulgraham.com/really.html) (2009) — credits Hoffman
- PG, [Do Things that Don't Scale](https://paulgraham.com/ds.html) (July 2013)
- PG, [Startup = Growth](https://paulgraham.com/growth.html) (Sept 2012)
- PG, [Default Alive or Default Dead?](https://paulgraham.com/aord.html) (Oct 2015)
- Altman, [Startup Playbook](https://playbook.samaltman.com/) (2015)
- Ralston & Seibel, [YC's Essential Startup Advice](https://www.ycombinator.com/library/4D-yc-s-essential-startup-advice)
- Blomfield, [What Actually Makes A Startup Durable](https://www.youtube.com/watch?v=99sPd15j3Zc) (July 2026)

Counter-evidence (read before treating any of the above as universal):

- Heyman, [On the life and death of YC startups](https://jaredheyman.medium.com/on-the-life-and-death-of-y-combinator-startups-d58aa03421f0) — ~50% failed at 12 years; value concentrated in ~10 companies
- Baek & Hegde, [Beyond Demo Day](https://www.nber.org/papers/w35063) (NBER, 2026) — 60–80% of accelerators destroy value; YC is in the elite minority, partly via selection
- Renert, [Growth as a false signal in YC startups](https://techcrunch.com/2016/12/18/growth-as-a-false-signal-in-y-combinator-startups/) — why the weekly growth benchmark doesn't extrapolate
- Fishkin, [Can we finally stop launching MVPs?](https://www.linkedin.com/pulse/can-we-finally-stop-launching-minimum-viable-products-rand-fishkin) — reputation cost of shipping ugly to an existing audience
- Cohen, [Business Advice Plagued by Survivor Bias](https://longform.asmartbear.com/survivor-bias/)
- Garber, [Why "Do Things That Don't Scale" Doesn't Always Work](https://www.forbes.com/sites/stellafayman/2013/08/01/why-do-things-that-dont-scale-doesnt-always-work/) — the hidden premise is access to capital

Better-fitting canon for a part-time, self-funded builder: Rob Walling (stair-step
method), Arvid Kahl (audience first), Pieter Levels (*Make*), Jason Fried & DHH
(*Rework*).

## Known omissions

Cofounder selection and equity splits — the most-repeated non-product instruction in
the YC canon (PG's *13 Sentences* opens with it), deliberately dropped because Ali builds
solo. Restore if that ever changes.
