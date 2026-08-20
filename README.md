# DEX Trading Product System Design

A product case study for a unified self-custodial trading experience combining AMM-style liquidity with order-book / CLOB execution concepts.

**Role lens:** Product Management  
**Focus:** DEX · AMM · CLOB · Spot / Perpetual Trading · Risk · Product Metrics  
**Artifacts:** Product strategy · Trade flows · State models · Risk controls · API/product logic

> This is a portfolio reconstruction based on product design work and synthetic examples. It contains no confidential company data and is not presented as a live production deployment.

## Product problem

DEX users often trade across fragmented venues and interfaces, balancing simplicity, liquidity depth, execution quality, self-custody and transparency. This case explores how a single product can serve retail users and more advanced traders without collapsing those requirements into one overly complex interface.

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

## Product decisions highlighted

1. **Simple vs. professional trading modes** — progressive disclosure rather than one dense interface.
2. **AMM + CLOB mental model** — distinguish quote-based swaps from resting orders and matching behavior.
3. **Execution quality as a product surface** — users need clear trade-offs among price, gas, slippage, liquidity and success probability.
4. **Risk transparency** — liquidation, price deviation, stale quotes and insufficient collateral should be understandable before irreversible actions.
5. **Stateful trading UX** — order creation is only the start; pending, partial, cancelled, rejected and failed states all require explicit product treatment.

## Evidence sources used for this reconstruction

The underlying product documentation includes market analysis, user segmentation, competitor analysis, AMM/CLOB design, liquidity-pool concepts, risk-control concepts and KPI planning.

## Planned repository map

- `docs/product-strategy.md`
- `docs/quote-and-execution-lifecycle.md`
- `docs/order-state-model.md`
- `docs/risk-controls.md`
- `docs/product-metrics.md`
- `specs/quote-api-example.md`

## Portfolio connection

This repository supports applications for DEX, on-chain trading, wallet trading, exchange trading-systems and institutional trading product roles. The visual case study is maintained separately in Figma.
