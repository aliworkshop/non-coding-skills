---
name: stripe-helper
description: Handle Ali's Stripe operations, when a Stripe account is connected — creating and sending invoices, generating payment links, and pulling reporting data (balance, recent payments, customer history). Use this skill whenever Ali mentions Stripe, invoicing a client, billing someone, sending a payment link, checking what someone has paid, or any reference to charges, refunds, or revenue activity. Triggers include "send X an invoice", "bill X for Y", "create a Stripe invoice", "make a payment link", "how much did X pay", "what's my Stripe balance", "did X's invoice go through", "void this invoice", "refund X", "check my Stripe", or any casual phrasing like "throw an invoice on the books for X". Even when Ali doesn't say "Stripe" explicitly — anything about billing a client, generating a paid link, or looking up payment history — this skill should fire.
---

# Stripe Helper

Workflow skill for a Stripe account, used only when the Stripe MCP is connected and the business
billing the work actually uses Stripe. If it isn't connected, say so and stop; don't improvise
another way to move money.

`TODO(ali):` name the payment provider each business really uses (Stripe, a local gateway, bank
transfer). For anything other than Stripe, this skill only drafts the invoice text and amounts;
Ali sends it.

Covers three things:
1. Creating and sending invoices for freelance/contract work and one-off engagements
2. Generating payment links
3. Pulling reporting data (balance, invoice status, customer history)

## Heads up: this is the LIVE Stripe account

The Stripe MCP may be connected to a live account, not test mode. Real money moves. Always confirm with Ali before finalizing anything that touches a real customer.

## Offers — read them live, don't trust a list

**Start every invoice by pulling the live catalog** (`GetProducts` with `active: true`, one call,
returns everything). Do not work from product/price IDs written down in this skill.

A cached product table goes stale within weeks: products get added and archived, and a written-down
list only supplies a wrong prior. The live catalog is one call away.

What's stable and worth knowing:

- Assume **one-off invoicing** (hourly blocks, fixed-scope projects). `TODO(ali):` confirm, and note
  any subscriptions or coupons here if they exist.
- Products are **services** (`type: service`, tax code `txcd_20030000`) with a single one-time
  price attached.
- Product names should encode the format and size, e.g. `Backend consulting (10 h block)`,
  `API integration (fixed scope)`. Match on that when picking a price.
- Older products linger as `active` after they stop being sold. Presence in the catalog is not
  evidence an offer is current — if the name doesn't match what the deal actually was, ask.

### When the amount has no matching price

If the total doesn't equal a catalog price × a whole-number quantity, **stop and ask Ali** before
improvising. This guardrail is the reason the price table wasn't needed: checked against live
Stripe, it catches both a mistyped amount and a genuinely new offer, and it distinguishes them by
asking rather than guessing.

The two resolutions look different:

- **A new offer** (Ali sold a format that doesn't exist yet) — create the product and price
  deliberately, named for its format and duration. Confirm with Ali first; a new SKU is
  permanent and lands in the live catalog. Then tell the `engagements` skill so the engagement card's `Offer` label matches.
- **A one-off deviation** (courtesy rate, bundled favor) — don't mint a price for it. Never
  create a price purely to make a total come out right, e.g. a $6,000 price when the deal is
  4 × a $1,500 block. Ali builds that line item in the dashboard.

## Sending an invoice (the standard workflow)

Stripe doesn't have a single "send invoice" action — follow this order:

0. **Ground the amount in the agreement, not a summary.** Before touching Stripe, confirm what was actually agreed from the source — the email thread with the client, not CRM card notes (notes lag and compress; a restructured deal can change the total). Watch for a price the client never restated in writing: if they replied "let's do it" to a two-option email, the number is implied, not confirmed, and the invoice line is what pins it down. Then reconcile against the live catalog per the section above.
1. **Find or create the customer.** Search by email first to avoid duplicates (`search_stripe_resources` with `customers:email~"domain.com"`). Only call `create_customer` if no match.
2. **Create a draft invoice** with `create_invoice` (sets `customer` and `days_until_due`).
3. **Attach ONE line item** with `create_invoice_item` using a price ID from the live catalog you pulled above. The MCP can't set quantity, so for multi-unit invoices create a single line item and tell Ali what quantity to set in the dashboard — do NOT create N duplicate line items, and never create a new price to fake a total (e.g. don't mint a $6,000 price when the deal is 4 × a $1,500 block price).
4. **Remind Ali about bank payment and the due date.** The MCP can't set payment methods, and `days_until_due` is fixed at creation on a draft that can't be edited afterward. `TODO(ali):` payment terms (e.g. due before work starts, or net-14). Compute from the agreed date rather than defaulting, and say so if the date is too near. If the client has paid by bank transfer before, remind Ali to check **ACH Direct Debit** under Payment options before finalizing.
5. **Pause and confirm with Ali.** Show the summary — customer, line item, quantity to set, amount, due date — and wait for explicit OK before finalizing. This is the rule, even when the request feels obvious.
6. **Finalize** with `finalize_invoice` after Ali has made the dashboard tweaks (quantity, ACH). This locks the invoice and triggers Stripe to email the hosted invoice link to the customer.

The `finalize_invoice` response includes a hosted invoice URL (`url` field). Always include this in the reply to Ali, plus the dashboard URL (see URL patterns below).

### Computing days_until_due

Ali may say "due May 10" or "due next Friday". Convert to a day count from today using `date` in bash if needed. Stripe's API takes an integer count, not a date.

## Critical: finalized invoices can't be edited

Once an invoice is finalized (status `open`), the API blocks updates to `due_date`, line items, and most other fields — this is a Stripe constraint, not an MCP limitation. The Stripe MCP also does NOT expose `void_invoice` or an invoice update operation, so neither can be done from this skill.

When Ali asks to change a finalized invoice:

1. Say the limitation up front.
2. Point Ali to void the existing one in the dashboard (steps below).
3. Offer to create a fresh invoice with the corrected details.

### How to void in the Stripe dashboard (give Ali these exact steps)

1. Open the invoice in the dashboard
2. Click the **three dots** (top right of the invoice page)
3. Select **Change invoice status**
4. Choose **Mark invoice as void**
5. Click **Update status**

### Draft invoices are nearly as locked (MCP walls)

Discovered limits of the Stripe MCP, even on drafts: no invoice update (due date, payment methods), no invoice or invoice-item deletion, and `create_invoice_item` accepts only a price ID — no quantity, no custom amount, no description. `stripe_api_execute` doesn't expose invoiceitems operations either. Practical upshot: get the draft right at creation; anything wrong on a draft is fixed or deleted by Ali in the dashboard (drafts delete cleanly from the ⋯ menu). If you create a price by mistake, deactivate it with `PostPricesPrice` (`active: false`).

## Payment links

For "create a Stripe link for X" — use `create_payment_link` with a price ID. Payment links are shareable and don't require a customer record. Good for: a fixed-scope offer, a paid tier of a product or bot, a one-off offer to drop into a DM.

Confirm with Ali before creating: which price, any quantity limits, where Ali plans to share it. Return the payment link URL when done.

## Reporting and lookups

When Ali asks "did X pay", "how much is in my account", "what's my Stripe doing", reach for:

- **`retrieve_balance`** — current available + pending balance
- **`GetInvoices`** via `stripe_api_execute` — recent invoices with status (`paid`, `open`, `void`, `draft`, `uncollectible`) and full line items. Filter with the `customer` param if Ali names a specific person. (There is no `list_invoices` tool.)
- **`list_payment_intents`** — actual successful payments (`status: succeeded`) vs. canceled attempts. Useful for verifying a charge actually went through.
- **`search_stripe_resources`** with `customers:email~"..."` — quick lookup for a specific person (there is no `list_customers` tool)

Don't check subscriptions or coupons unless Ali asks or the account uses them.

## URL patterns

These are stable Stripe dashboard patterns — useful for giving Ali a clickable link to manage things.

- Invoice (dashboard): `https://dashboard.stripe.com/invoices/{invoice_id}`
- Customer (dashboard): `https://dashboard.stripe.com/customers/{customer_id}`
- Payment intent (dashboard): `https://dashboard.stripe.com/payments/{payment_intent_id}`
- Hosted invoice (customer-facing): returned in the `url` field on `finalize_invoice`

When Ali asks for "the link to that invoice", that usually means the dashboard URL (to manage it), not the hosted one (which is for the customer to pay). If unclear, share both.

## Working pattern reminders

- **Confirm before finalizing.** Always pause after step 3 of the invoice flow.
- **Surface the live-mode caveat** when creating anything for a real customer — quick reminder, no need to belabor it.
- **Don't create duplicate customers.** Email lookup first, every time.
- **When something is blocked by API limits** (void, update finalized invoice, etc.), tell Ali what the wall is and offer the dashboard workaround. Don't loop trying alternative API operations.
- **Default to including dashboard links** in any summary so Ali can jump straight to it.
