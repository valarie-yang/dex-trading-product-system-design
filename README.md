# DEX Trading Product System Design

A product case study for a unified self-custodial trading experience combining AMM-style liquidity with order-book / CLOB execution concepts.

**Role lens:** Product Management  
**Focus:** DEX · AMM · CLOB · Spot / Perpetual Trading · Risk · Product Metrics  
**Artifacts:** Product strategy · Trade flows · State models · Risk controls · API/product logic

> This is a portfolio reconstruction based on product design work and synthetic examples. It contains no confidential company data and is not presented as a live production deployment.

## My role and scope

**PM scope represented in this case:** requirements, user journeys, quote/order product rules, interface-field definitions, state/exception design, risk UX, metrics, testing and UAT collaboration.

**Implementation boundary:** this case does not claim ownership of matching-engine implementation, market making, smart-contract engineering, routing algorithms or exchange risk-engine code.

## Product problem

DEX users often trade across fragmented venues and interfaces, balancing simplicity, liquidity depth, execution quality, self-custody and transparency. This case explores how one product experience can support both quote-based swaps and order-based trading without pretending they are the same execution model.

## Product scope

- Swap with AMM-style liquidity
- Spot / perpetual trading concepts
- Market and limit orders
- Quote preview and quote-expiry rules
- Slippage, price impact and gas visibility
- Partial fills, cancellation and execution reports
- Liquidity / route comparison dimensions
- Risk controls and transaction failure handling
- Unified account / position concepts

## Core trade lifecycle

```text
Wallet connected
   ↓
Market / pair selected
   ↓
Balance + allowance validation
   ↓
Quote / order parameters
   ↓
Preview: price, fees, gas, slippage, impact
   ↓
Sign / submit
   ↓
Execution / matching
   ↓
Partial fill / filled / cancelled / failed
   ↓
Settlement + portfolio update
```

## Key product trade-offs

1. **Simple vs. professional UX** — progressive disclosure reduces cognitive load without removing controls advanced users need.
2. **Quote certainty vs. freshness** — longer quote validity improves completion but increases stale-price / execution risk; expiry must be visible and actionable.
3. **Execution quality vs. transaction cost** — lowest displayed price is not automatically the best route once gas, price impact, liquidity and failure probability are considered.
4. **One trading surface vs. truthful mental models** — AMM swaps and resting limit orders can share navigation, but their state models and execution expectations should remain distinct.

## Product decisions highlighted

- Distinguish quote-based swaps from resting orders and matching behavior.
- Treat execution quality as a product surface, not only a backend concern.
- Expose liquidation, stale quotes, insufficient collateral and other material risk states before irreversible actions.
- Design for pending, partial, cancelled, rejected and failed outcomes instead of treating submission as completion.

## Repository map

- [`docs/product-strategy.md`](docs/product-strategy.md) — users, scope and product principles
- [`docs/quote-lifecycle.md`](docs/quote-lifecycle.md) — quote generation and expiry logic
- [`docs/order-state-model.md`](docs/order-state-model.md) — Market / Limit order states
- [`docs/risk-controls.md`](docs/risk-controls.md) — pre-trade and execution risk surfaces
- [`docs/product-metrics.md`](docs/product-metrics.md) — proposed product metrics
- [`specs/quote-api-example.md`](specs/quote-api-example.md) — example quote contract
- [`specs/order-transition-rules.md`](specs/order-transition-rules.md) — transition rules and invalid transitions
- [`supporting/trading-automation-and-decision-support.md`](supporting/trading-automation-and-decision-support.md) — Trading Bot → AI decision-support study

## Portfolio connection

This is a flagship case for DEX, on-chain trading, wallet trading, exchange trading-systems and institutional trading product roles. The supporting automation study extends the same product foundation toward AI-assisted trading and decision support.
