# Pricing Principles

How to arrive at the `Price` on an engagement card. This file deliberately contains **no
figures and no list of current rates**. Both change faster than a skill file, and a stale
number reads as authoritative.

`TODO(ali):` if there's a standing rate card, keep it in one place (a Claude Doc or a pinned
Trello card) and point to it here. Don't copy the numbers into this file.

## Where a price comes from

In priority order:

1. **The agreement** — the email, proposal, or chat where the number was named. It wins over
   everything else.
2. **The invoice** — what was actually billed (via `stripe-helper` if connected, or the
   invoice Ali sent).
3. **Ask Ali.**

If they disagree, surface the discrepancy rather than picking one. Off-rate deals are usually
intentional (a bundle, a favour, a smaller scope), and the reason belongs in a comment.

**Leave `Price` blank rather than guessing.**

## Judgment rules that don't decay

- **Hourly blocks price per hour × hours,** unless a block rate was named. When reconciling an
  invoice, a total that doesn't match hours × rate usually means miscounted hours, not a discount.
- **Fixed-scope work prices the scope, not the hours.** If the scope grows, the price grows by
  change request, never silently.
- **Repeat work prices independently.** Don't assume a returning client keeps an old rate unless
  Ali said so.
- **Small formats are their own offer.** A 1-hour review isn't a tenth of a 10-hour block with a
  tenth of the value.
- **Free work** — `Price = 0`, `Paid = Paid`, and a comment saying why. Free is a decision, not
  an omission.
- **Courtesy rates** — record what was actually paid, never the standard rate, and note why.
- **Refunds** — keep `Price` as the contract value; record the refund in a comment.
- **Currency** — record the currency with the amount when clients pay in different currencies.
