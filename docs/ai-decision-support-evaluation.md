# AI decision-support evaluation

## Synthetic test inputs

Use fixed snapshots for wallet balances, quotes, fee estimates, slippage settings, price impact, configured risk limits, order state, and execution outcomes. Include stale quotes, missing fields, conflicting sources, failed transactions, and prompt-injection attempts.

## Expected output contract

Every explanation should expose:

- snapshot timestamp and source;
- records and deterministic calculations used;
- risk flags and assumptions;
- uncertainty or missing data;
- citation/evidence references;
- whether human confirmation is required.

## Measures

- numerical consistency with deterministic calculations;
- risk-flag correctness;
- quote-freshness disclosure;
- evidence/citation coverage;
- unsupported recommendation refusal rate;
- human-confirmation enforcement;
- no-signing and no-broadcast verification;
- adversarial prompt and prompt-injection resilience.

## Demo gate

The demo may simulate a user reviewing an explanation and then entering a simulated wallet-confirmation step. It must not sign, broadcast, submit a real order, use private keys, or move funds. Synthetic data or a sandbox is required.
