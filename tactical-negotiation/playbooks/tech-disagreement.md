# Playbook: Disagreeing With a Lead, PM, or Teammate

Goal: change the decision, or at least get your concern on record, without
turning it into a contest. Architecture and deadline fights are rarely about
the facts. They're about who looks wrong. Make it easy for them to change
their mind.

## Sequence
1. **Show you heard their reason first (summary → "that's right").**
   > "So the worry is that a second service is more to deploy and watch, and
   > we don't have the people for it. Is that right?"
   Don't make your case until they agree you've understood theirs.
2. **Soften before the disagreement (accusation audit).**
   > "I'm probably going to sound like I'm overcomplicating this."
3. **Label the risk instead of asserting it.**
   > "It seems like we'd be locking ourselves into this schema for the
   > invoices that are already out."
   A label invites them to check. An assertion invites them to defend.
4. **Let them find the problem (calibrated question).**
   > "How would we roll this back if it goes wrong in production?"
   > "What happens to the open orders during the migration?"
   If the plan has a hole, the question finds it. You don't have to.
5. **Offer a small, reversible test.**
   > "Would it be crazy to try it on one service first and decide after?"
6. **Commit once it's decided.** If it goes their way, say so plainly and do it
   well. Write your concern down once, where the team keeps decisions.
   > "Fine by me. I'll note the rollback concern on the ticket and get on with it."

## Highest-leverage lines
- "So the worry is X. Is that right?" *(earn the hearing first)*
- "It seems like this locks us into…" *(label the risk)*
- "How would we roll this back?" *(calibrated question)*
- "Would it be crazy to try it on one service first?" *(no-oriented)*
- "What would change your mind on this?"

## Traps
- Don't argue in a group thread. Take it to one person or a short call.
- Don't say "why did you…". Ask "what led to…" or "how does this handle…".
- Don't relitigate a decision that's already made. Note it once and move on.
- Don't win the argument and lose the teammate. You'll work with them next week.
