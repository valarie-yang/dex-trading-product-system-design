# Order Transition Rules

This document makes the product-state model explicit enough for PM–engineering discussion. It is not a matching-engine implementation spec.

## Core order states

```text
CREATED
  ↓
SUBMITTED
  ↓
ACKNOWLEDGED
  ├─→ PARTIALLY_FILLED ─→ FILLED
  │          └─→ CANCEL_REQUESTED ─→ CANCELLED
  ├─→ FILLED
  ├─→ CANCEL_REQUESTED ─→ CANCELLED
  └─→ REJECTED
```

## Allowed transitions

| From | To | Product meaning |
|---|---|---|
| `CREATED` | `SUBMITTED` | Client sends a valid order request |
| `SUBMITTED` | `ACKNOWLEDGED` | Trading service accepts the order for processing |
| `SUBMITTED` | `REJECTED` | Validation / risk / venue rejects the order |
| `ACKNOWLEDGED` | `PARTIALLY_FILLED` | Some quantity executes |
| `ACKNOWLEDGED` | `FILLED` | Full quantity executes |
| `ACKNOWLEDGED` | `CANCEL_REQUESTED` | User requests cancellation |
| `PARTIALLY_FILLED` | `FILLED` | Remaining quantity executes |
| `PARTIALLY_FILLED` | `CANCEL_REQUESTED` | User cancels remaining quantity |
| `CANCEL_REQUESTED` | `CANCELLED` | Venue confirms remaining quantity is cancelled |

## Invalid / misleading transitions

- `CREATED → FILLED`: skips submission and acknowledgement states.
- `REJECTED → FILLED`: a rejected order must not later appear as executed without a new order identity.
- `FILLED → CANCELLED`: a fully executed order cannot be cancelled.
- `CANCEL_REQUESTED → CANCELLED` should not be shown to users until the venue confirms cancellation.

## Product fields required for state reconstruction

- `orderId`
- `clientOrderId`
- `market`
- `side`
- `orderType`
- `requestedQty`
- `filledQty`
- `remainingQty`
- `limitPrice` where applicable
- `avgFillPrice`
- `status`
- `rejectReason`
- `createdAt`
- `updatedAt`
- `executionReports[]`

## Example reject reasons

- `INSUFFICIENT_BALANCE`
- `INSUFFICIENT_MARGIN`
- `PRICE_OUTSIDE_LIMIT`
- `INVALID_ORDER_SIZE`
- `MARKET_UNAVAILABLE`
- `RISK_LIMIT_EXCEEDED`
- `ORDER_EXPIRED`

The PM requirement is to keep user-visible order state consistent with backend acknowledgement and execution reports rather than inferring completion from the original submit action.
