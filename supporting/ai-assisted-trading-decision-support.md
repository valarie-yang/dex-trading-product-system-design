# AI-Assisted Trading Decision Support

## Positioning

A supporting AI layer for DEX trading workflows, focused on explainability, risk visibility, and scenario comparison.

It is not an AI trading bot, autonomous trading agent, investment adviser, portfolio manager, or profit-prediction system.

## Example interaction

A user asks why a strategy condition was triggered. The system retrieves a quote and portfolio snapshot, applies deterministic rules, shows the relevant risk flags and evidence, and asks the user to review the result. The model may explain the result in plain language; it does not create a binding trade instruction.

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

## Portfolio status

This is a product and architecture case using synthetic scenarios. It is included in the DEX repository as supporting work because the flagship evidence remains the quote, order, execution, risk, and settlement lifecycle.
