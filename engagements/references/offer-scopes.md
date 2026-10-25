# Offer Scopes

Deliverable **shapes** for recurring kinds of work. Fill the Scope section of a new engagement
card from these unless the agreement says otherwise. Prices are deliberately not here; see
`pricing-principles.md`.

Scope records what was **promised at sale**. If delivery materially changes, that's a change
request or a new card, not an edit to the old scope.

`TODO(ali):` replace or extend these with the shapes Ali actually sells.

## Consulting block

- N hours of backend consulting (architecture review, code review, pairing), used within a
  stated window.
- Written summary after each session.
- **Out of scope:** implementation beyond what fits in the hours.

## Fixed-scope API or service

- The endpoints or service boundary, listed.
- Tests for the listed behaviour, and the docs a caller needs (OpenAPI or README).
- One round of fixes after handover, within a stated window.
- **Out of scope:** new endpoints, infrastructure beyond what's listed, ongoing operation.

## Integration

- Connect the client's system to a named third party (payments, SMS, messaging), with the
  failure handling spelled out.
- **Out of scope:** changes on the third party's side, support for providers not named.

## Maintenance retainer

- Up to N hours per month of fixes and small changes, with a response time.
- Monthly summary of what was done.
- **Out of scope:** new features beyond the hours; unused hours don't roll over unless agreed.

## Closing deliverable

Every scope names its last deliverable (handover, final review, acceptance). Without it, there's
no clear moment to move the card to `Delivered`.
