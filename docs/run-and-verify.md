# Run and verify

## Public surface

This is a documentation-first product/system design case. The shortest valid path is:

1. Open [evidence-overview.svg](../assets/evidence-overview.svg).
2. Read [portfolio-evidence-index.md](portfolio-evidence-index.md).
3. Inspect the quote/order state model, transition rules, risk controls and AI boundary.

## Runtime status

No public trading runtime is included. The quote API and lifecycle documents are PM-level specifications, not a connected exchange client.

## Test status

No application test command is claimed. Verification is a manual scenario review covering fresh/stale quote, allowance, gas, slippage, signature, pending, fill, cancellation, rejection and failure states.

## Evidence labels

- `public-safe reconstruction`: portfolio material curated for public review.
- `synthetic examples`: illustrative market/account scenarios.
- `PRD/system design`: proposed product and state logic.
- `production`: not claimed.