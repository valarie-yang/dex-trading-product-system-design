# DEX Product Risk Controls

This note summarizes product-level controls for a unified DEX trading experience.

## Pre-trade controls
- Wallet connected and network validated
- Sufficient balance and gas token
- Token approval state checked
- Quote freshness checked before signing
- Slippage tolerance validated against product limits
- Price impact warning thresholds
- Liquidity / route availability check
- Position / margin validation for leveraged products

## Execution controls
- Idempotent submission handling where the product backend participates
- Prevent duplicate submit actions while a transaction/order is pending
- Clear distinction between user rejection, submission failure and on-chain failure
- Explicit cancelability rules for open orders

## Market / protocol risk examples
- Liquidity deterioration
- Oracle/index price divergence
- Extreme price impact
- Abnormal funding / mark price movement
- Liquidation proximity
- Network congestion or chain instability

## UX escalation

Risk communication should be severity-based:

**Informational** — estimated gas, expected price impact.  
**Warning** — high price impact, unusual slippage, low liquidity.  
**Blocking** — invalid quote, insufficient margin, unsupported network, transaction would violate product limits.

## Product principle

A risk control should answer three questions for the user:
1. What changed?
2. Why does it matter?
3. What can I safely do next?

This document is a portfolio reconstruction, not a representation of a live exchange risk engine.
