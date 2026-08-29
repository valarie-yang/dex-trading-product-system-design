# DEX Trading Product System Design

A portfolio case study for a unified self-custodial trading experience combining AMM-style liquidity with order-book / CLOB execution concepts.

**Role lens:** Product Management  
**Product area:** DEX · AMM · CLOB · Spot / Perpetual Trading · Risk · Product Metrics  
**Artifacts:** Product strategy · Trade flows · Quote lifecycle · Order states · Risk controls · PM-level API logic  
**Portfolio:** [Valarie Yang — Product Portfolio](https://www.figma.com/design/pIUP2RYiUR3fpGoKHjRGnU/Valarie-Yang-%E2%80%94-Product-Portfolio?node-id=0-1)  
**Profile:** [LinkedIn](https://www.linkedin.com/in/valarie-yang-08573b122/) · [GitHub](https://github.com/valarie-yang)

> Public-safe portfolio reconstruction using synthetic examples. No confidential company data. Not presented as a live production exchange.

## Case signal

This case is built to show exchange-product judgment: how to design a trading surface where swaps, limit orders, quote expiry, slippage, liquidity depth, execution states, and risk warnings are understandable without oversimplifying the underlying mechanics.

A reviewer should be able to see:

- How AMM swap behavior differs from resting order / matching behavior
- Where users need price, fee, gas, slippage, and impact visibility before committing
- How partial fill, cancellation, rejection, failure, and portfolio settlement states are modeled
- How PM requirements can connect trading UX, execution quality, risk controls, and metrics

## Founder Orange review pass

**Verdict:** flagship case. It should lead when applying for exchange, trading, wallet-trading, or Web3 product roles.

**Sharpened positioning:** this repo proves that I can design around execution truth, not just trading screens. The strongest signal is the separation of user intent, quote validity, matching/execution behavior, and post-trade state.

## Product problem

DEX users often trade across fragmented venues and interfaces, balancing simplicity, liquidity depth, execution quality, self-custody, and transparency. A product surface can feel simple only if the underlying state model is rigorous: quote freshness, allowance, gas, slippage, fill status, and settlement all need explicit product rules.

## My role and scope

Represented PM work:

- Product strategy and user segmentation for self-custodial trading
- Quote and order lifecycle definition
- Market / limit order state model
- Risk warning and exception-surface design
- Interface-field definitions for trading forms and previews
- Metrics, UAT thinking, and PM-level API examples

Implementation boundary:

- No ownership claim over matching-engine implementation, market making, routing algorithms, smart-contract engineering, exchange risk-engine code, or production liquidity operations

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
Partial fill / filled / cancelled / rejected / failed
   ↓
Settlement + portfolio update
```

## Product decisions highlighted

1. **Simple vs. professional UX** — progressive disclosure reduces cognitive load without removing controls advanced users need.
2. **Quote certainty vs. freshness** — quote expiry must be visible and actionable; stale certainty is worse than honest uncertainty.
3. **Execution quality vs. transaction cost** — lowest displayed price is not always best after gas, price impact, liquidity, and failure probability.
4. **One surface, truthful models** — AMM swaps and resting orders can share navigation, but their execution expectations should remain distinct.
5. **Risk before irreversibility** — liquidation, stale quotes, insufficient collateral, and signature risk must surface before irreversible actions.

## Repository map

- [`docs/product-strategy.md`](docs/product-strategy.md) — users, scope and product principles
- [`docs/quote-lifecycle.md`](docs/quote-lifecycle.md) — quote generation and expiry logic
- [`docs/order-state-model.md`](docs/order-state-model.md) — market / limit order states
- [`docs/risk-controls.md`](docs/risk-controls.md) — pre-trade and execution risk surfaces
- [`docs/product-metrics.md`](docs/product-metrics.md) — proposed product metrics
- [`specs/quote-api-example.md`](specs/quote-api-example.md) — example quote contract
- [`specs/order-transition-rules.md`](specs/order-transition-rules.md) — transition rules and invalid transitions
- [`supporting/trading-automation-and-decision-support.md`](supporting/trading-automation-and-decision-support.md) — Trading Bot → AI decision-support study

## Portfolio connection

This is a flagship case for DEX, on-chain trading, wallet trading, exchange trading systems, and institutional trading product roles. It connects interface-level clarity with execution-state rigor.