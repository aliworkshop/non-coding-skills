# Impact slide patterns

The proof slide lives or dies on whether the proof is real and relevant. This file covers
turning raw research into honest, persuasive slide content.

## Segment by what the reader cares about

Group the proof into the two or three concerns the reader named or obviously has. A CTO reads
for reliability and risk; a founder for speed and cost; a venue owner for customers and revenue.
Each reader should see their own concern in one column. Match each case study to the column it
proves.

## Case study vs Example — tag everything

This distinction is the integrity of the slide. Tag each item:

- **Case study** — a real result from real work Ali did. Mark it visibly (a small colored tag).
  Name the client only if Ali confirms it's allowed; otherwise describe the shape ("a payments
  backend", "an exchange's order service"). Public work, such as Ali's open-source libraries,
  can always be named and linked.
- **Example** — a capability Ali can demonstrate but isn't yet tied to a client result (a
  prototype, a load-test on a sample, a design sketch). These are what's *possible*, not past
  results.

Never let an example pass as a proven result. If the slide title says "proven" and some items
are examples, soften the title or move the examples.

## Before → after is the strongest frame

The most persuasive line pairs the old cost with the new, with a number Ali can stand behind.
Shapes, not facts — fill in only with real numbers:

- "p99 latency [before] → [after] after moving [component] to [approach]."
- "Deploys went from [manual, N per week] to [automated, on every merge]."
- "Library used in [N] projects; replaced [N] lines of hand-written query code."

Phrase impacts compactly ("[before] → [after]"). Keep the metric vocabulary consistent across
the deck (latency, throughput, uptime, time) so it reads as one argument.

## Sourcing notes

- Every number needs a source Ali can point to: a dashboard, a load-test result, a PR, a
  GitHub page. Keep the link next to the number in your notes.
- Ask Ali for the before number when only the after exists. A lone "after" proves little.
- Public numbers (GitHub stars, adopters) are safe; check they're current on the day.

## Watch-outs

- Work under NDA: describe the shape, never the client, the code, or internal figures.
- Don't overclaim: if only one column has a verified case study, mark the others as examples.
- Flag gaps to Ali ("reliability column has no measured result yet, using examples") rather
  than papering over them.
