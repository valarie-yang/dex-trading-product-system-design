# DEX Trading Product System Design

A portfolio case study for a unified self-custodial trading experience combining AMM-style liquidity with order-book / CLOB execution concepts.

**Role lens:** Product Management  
**Product area:** DEX · AMM · CLOB · Spot / Perpetual Trading · Risk · Product Metrics  
**Artifacts:** Product strategy · Trade flows · Quote lifecycle · Order states · Risk controls · PM-level API logic  
**Status:** Product/system design case with synthetic examples; not a live production exchange  
**Portfolio:** [Valarie Yang — Product Portfolio](https://www.figma.com/design/pIUP2RYiUR3fpGoKHjRGnU/Valarie-Yang-%E2%80%94-Product-Portfolio?node-id=0-1)  
**Profile:** [LinkedIn](https://www.linkedin.com/in/valarie-yang-08573b122/) · [GitHub](https://github.com/valarie-yang)

> Public-safe portfolio reconstruction using synthetic examples. No confidential company data, real-time market data, private keys, automated signing, transaction broadcasting, or investment advice.

## Case signal

This case shows exchange-product judgment: how to design a trading surface where swaps, limit orders, quote expiry, slippage, liquidity depth, execution states, and risk warnings are understandable without oversimplifying the underlying mechanics.

A reviewer should be able to see:

- how AMM swap behavior differs from resting order / matching behavior;
- where users need price, fee, gas, slippage, and impact visibility before committing;
- how quote, signature, broadcast, confirmation, settlement, partial fill, cancellation, rejection, and failure are separated;
- how PM requirements connect trading UX, execution quality, risk controls, and metrics.

## Portfolio review status

**Flagship case for DEX, exchange trading, wallet-trading, and Web3 product roles.**

The core product case is complete as a design artifact. The AI-assisted Trading Decision Support material is intentionally a supporting study: a read-only, explainable layer over deterministic market/account snapshots and risk calculations. It is not an autonomous trading agent and does not connect to keys, signers, broadcasters, or automatic order execution.

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
- AI decision-support boundary and evaluation design

Implementation boundary:

- No ownership claim over matching-engine implementation, market making, routing algorithms, smart-contract engineering, exchange risk-engine code, production liquidity operations, or live transaction execution

## Core trade lifecycle

    Wallet connected
       ↓
    Market / pair selected
       ↓
    Balance + allowance validation
       ↓
    Quote / order parameters entered
       ↓
    Preview: price, fees, gas, slippage, impact
       ↓
    Awaiting user signature
       ↓
    Broadcasted / pending confirmation
       ↓
    Execution / matching
       ↓
    Confirmed / partially filled / filled / cancelled / rejected / failed
       ↓
    Settlement + portfolio update

AMM swaps, CLOB orders, and perpetual positions should not be treated as identical flows. For perpetuals, leverage, maintenance margin, liquidation, funding, and reduce-only behavior need separate rules.

## AI-assisted Trading Decision Support

This is appropriately included in the existing DEX repository under [supporting/trading-automation-and-decision-support.md](supporting/trading-automation-and-decision-support.md) and [supporting/ai-assisted-trading-decision-support.md](supporting/ai-assisted-trading-decision-support.md).

The AI layer may:

- explain why a deterministic strategy condition was triggered;
- summarize current exposure and configured risk limits;
- compare synthetic scenarios and parameter assumptions;
- explain execution failure, quote expiry, or price deviation;
- surface uncertainty and evidence for user review.

The AI layer may not:

- access private keys or signing functions;
- sign, broadcast, submit, or automatically execute transactions;
- modify risk limits or strategies without user confirmation;
- calculate authoritative balances, fees, slippage, or price impact from free-form text;
- provide personalized buy/sell/allocation advice or imply guaranteed returns.

All material actions require explicit user review and the existing wallet confirmation boundary.

## Product decisions highlighted

1. **Simple vs. professional UX** — progressive disclosure reduces cognitive load without removing controls advanced users need.
2. **Quote certainty vs. freshness** — quote expiry must be visible and actionable; stale certainty is worse than honest uncertainty.
3. **Execution quality vs. transaction cost** — lowest displayed price is not always best after gas, price impact, liquidity, and failure probability.
4. **One surface, truthful models** — AMM swaps and resting orders can share navigation, but their execution expectations remain distinct.
5. **Risk before irreversibility** — liquidation, stale quotes, insufficient collateral, approval risk, and signature risk surface before irreversible actions.
6. **Deterministic facts before generated explanation** — calculations and risk flags come from explicit snapshots and rules; AI explains them with evidence and uncertainty.

## Repository map

- [docs/product-strategy.md](docs/product-strategy.md) — users, scope and product principles
- [docs/quote-lifecycle.md](docs/quote-lifecycle.md) — quote generation and expiry logic
- [docs/order-state-model.md](docs/order-state-model.md) — market / limit order states
- [docs/risk-controls.md](docs/risk-controls.md) — pre-trade and execution risk surfaces
- [docs/product-metrics.md](docs/product-metrics.md) — proposed product metrics
- [docs/ai-decision-support-boundary.md](docs/ai-decision-support-boundary.md) — AI scope, safety, and non-execution boundary
- [docs/ai-decision-support-evaluation.md](docs/ai-decision-support-evaluation.md) — synthetic evaluation and demo gates
- [specs/quote-api-example.md](specs/quote-api-example.md) — example quote contract
- [specs/order-transition-rules.md](specs/order-transition-rules.md) — transition rules and invalid transitions
- [supporting/trading-automation-and-decision-support.md](supporting/trading-automation-and-decision-support.md) — strategy automation concept
- [supporting/ai-assisted-trading-decision-support.md](supporting/ai-assisted-trading-decision-support.md) — AI explanation and scenario-comparison case

## Portfolio connection

This is a flagship case for DEX, on-chain trading, wallet trading, exchange trading systems, and AI × FinTech product roles. It connects interface-level clarity with execution-state rigor and a controlled AI explanation layer.
