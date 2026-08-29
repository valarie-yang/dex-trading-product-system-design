# AI-Assisted Trading Decision Support

## Positioning

A supporting AI layer for DEX trading workflows, focused on explainability, risk visibility, and scenario comparison.

It is not an AI trading bot, autonomous trading agent, investment adviser, portfolio manager, or profit-prediction system.

## Proposed interaction

In a proposed implementation, the system would retrieve a quote and portfolio snapshot, apply deterministic rules, show risk flags and evidence, and ask the user to review the result. The model would be used to explain the result in plain language; it would not create a binding trade instruction.

## Example response shape

    Summary
    Snapshot timestamp
    Data sources and records used
    Deterministic calculations
    Risk flags
    Assumptions and uncertainty
    Human confirmation required: yes/no

## Guardrails

- read-only AI layer;
- no private-key, signer, broadcaster, or auto-submit access;
- no personalized buy/sell/allocation advice;
- no guaranteed-return or “optimal strategy” language;
- explicit stale-data and missing-data disclosure;
- user confirmation before any high-impact action.

## Wallet boundary

The design assumes a separate wallet-confirmation flow; this repository does not implement signing, broadcasting, or fund transfer.

## Portfolio status

This is a product and architecture case using synthetic scenarios. It is included in the DEX repository as supporting work because the flagship evidence remains the quote, order, execution, risk, and settlement lifecycle.
