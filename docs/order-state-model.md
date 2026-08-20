# Order State Model

A unified trading product needs a clear state model across market and limit orders, partial fills and cancellation.

## Core order states

```text
CREATED
  ↓
VALIDATING
  ├─→ REJECTED
  ↓
OPEN
  ├─→ PARTIALLY_FILLED
  │      ├─→ FILLED
  │      └─→ CANCELED
  ├─→ FILLED
  └─→ CANCELED
```

## Important distinctions

- **Rejected**: order never became active because validation failed.
- **Canceled**: an active order was intentionally removed before full execution.
- **Partially filled**: some quantity executed while residual quantity remains open.
- **Filled**: the requested executable quantity completed.

## Product data fields

- order id
- account / wallet
- market / pair
- side
- order type
- quantity
- limit price (if applicable)
- filled quantity
- remaining quantity
- average execution price
- fees
- created / updated timestamps
- status
- cancel reason / reject reason

## UX implications

Users should never have to infer whether an order is still executable. The interface should expose the remaining quantity and whether cancellation is still possible.

For partial fills, execution history and order state should remain separately inspectable.
