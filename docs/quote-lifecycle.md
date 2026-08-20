# Quote Lifecycle

This case models a DEX quote as a time-bounded product object rather than a static price.

## Quote request

Typical inputs:
- sell token / buy token
- sell amount or desired buy amount
- wallet / account
- chain / network
- slippage tolerance
- execution mode

## Quote response

A product-facing quote should expose:
- expected output amount
- minimum received / worst acceptable output
- estimated gas
- price impact
- route / liquidity source summary
- quote expiration
- approval requirement
- warnings and blocking conditions

## Lifecycle

```text
REQUESTED
   ↓
VALIDATING
   ↓
QUOTED
   ├─→ INVALID_INPUT
   ├─→ NO_LIQUIDITY
   └─→ QUOTE_EXPIRED
   ↓
PREVIEWED
   ↓
APPROVAL_REQUIRED? ──→ APPROVING
   ↓
READY_TO_SIGN
   ↓
SIGNED
   ↓
SUBMITTED
   ↓
PENDING
   ├─→ REVERTED / FAILED
   ↓
EXECUTED
   ↓
SETTLED / INDEXED
```

## Key product decisions

### Quote validity
A quote is valid only for a bounded period because market price, pool reserves and gas conditions change.

### Slippage vs. price impact
- **Price impact** describes how the order itself moves execution price relative to the reference market/pool state.
- **Slippage tolerance** is the user's allowed execution deviation before the transaction should fail.

They are related but not interchangeable.

### Route comparison
A product can compare routes using more than displayed price:
- expected output
- gas cost
- price impact
- liquidity depth
- route complexity
- historical execution reliability

The best displayed rate is not always the best final execution.

## Portfolio note

This is a product-system reconstruction based on the DEX case study and does not claim a live routing engine implementation.
