# Product Strategy

## Product concept

A unified self-custodial trading product that combines AMM-style swaps with order-book/CLOB concepts, giving users one product surface for simple execution and more advanced trading workflows.

## User problem

On-chain traders often face fragmentation across wallets, DEXs, aggregators and derivatives venues. The product challenge is to balance:
- simple onboarding and execution;
- transparent self-custody;
- liquidity and execution quality;
- professional order controls;
- understandable risk states.

## Primary user groups

### Simple swap user
Wants a reliable quote, clear fees, limited configuration and high transaction success.

### Active on-chain trader
Needs price impact, slippage, routing quality, faster market discovery and stronger transaction-state visibility.

### Order-book / derivatives user
Needs market/limit orders, partial fills, cancellation, execution reports, position and risk controls.

## Product principles

1. **Progressive disclosure** — expose advanced controls without making the default experience dense.
2. **Execution quality is visible** — price, gas, liquidity, slippage and quote validity are product surfaces.
3. **Trading is stateful** — pending, partial, cancelled, rejected and failed states all need explicit UX.
4. **Wallet state matters** — balance, allowance, network and signing are part of the trade journey.
5. **Risk before action** — liquidation, price deviation and insufficient collateral should be understandable before submission.

## MVP focus

- wallet connection;
- market discovery;
- AMM quote / swap lifecycle;
- Approval where required;
- Market / Limit order concepts;
- partial fill / cancellation states;
- execution and settlement status;
- product reliability and conversion metrics.

## Expansion paths

- multi-route aggregation;
- advanced order types;
- institutional API / SDK;
- cross-chain execution;
- portfolio margin;
- automation / strategy layer.
