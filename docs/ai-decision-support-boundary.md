# AI decision-support boundary

## Architecture boundary

    Market / wallet / portfolio snapshots
                 ↓
    Deterministic calculations and risk flags
                 ↓
    AI explanation and scenario comparison
                 ↓
    Human review
                 ↓
    Existing wallet-confirmation flow

The AI layer is read-only and does not connect to private keys, signers, transaction broadcasters, automatic order submission, or fund-transfer functions.

## AI may

- explain a deterministic strategy trigger;
- summarize exposure against configured limits;
- compare synthetic scenarios and assumptions;
- explain quote expiry, execution failure, or price deviation;
- surface uncertainty and evidence for user review.

## AI may not

- provide personalized buy, sell, or allocation advice;
- calculate authoritative financial values from free-form text;
- change a strategy or risk limit without explicit user review;
- sign, broadcast, submit, or execute a transaction;
- imply guaranteed returns or risk-free execution.

## Deterministic facts

Balances, quotes, fees, gas, slippage, price impact, margin, liquidation flags, order state, and confirmation state must be generated from explicit snapshots and rules. AI explains those facts; it does not replace the source of truth.

This is a portfolio product and architecture case. It is not investment advice or a live trading service.
