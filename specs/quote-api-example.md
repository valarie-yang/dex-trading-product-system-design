# Quote API — Product Contract Example

This is a **product specification example**, not a production API.

## Goal

Return an executable trade quote with enough metadata for the client to present execution quality, risk and expiry clearly.

## Example request

```json
{
  "chainId": 1,
  "tokenIn": "USDC",
  "tokenOut": "WETH",
  "amountIn": "1000",
  "wallet": "0xUSER",
  "maxSlippageBps": 50
}
```

## Example response

```json
{
  "quoteId": "q_20260820_001",
  "amountIn": "1000.00",
  "estimatedAmountOut": "0.3124",
  "minAmountOut": "0.3108",
  "estimatedGasUsd": "3.42",
  "priceImpactPct": "0.18",
  "route": ["USDC", "WETH"],
  "expiresAt": "2026-08-20T15:02:30Z",
  "approvalRequired": true,
  "warnings": []
}
```

## Product requirements

- A quote must have an explicit expiration time.
- The UI should not present an expired quote as executable.
- Slippage tolerance and minimum received should be visible before signing.
- `approvalRequired` should trigger an explicit Approval step before Swap when needed.
- Warnings should be typed and actionable rather than a free-text error blob.

## Suggested error taxonomy

| Code | Meaning | Product action |
|---|---|---|
| `INSUFFICIENT_BALANCE` | Token balance is too low | Disable submit and show required balance |
| `INSUFFICIENT_GAS` | Native gas balance is too low | Explain required native asset |
| `NO_ROUTE` | No executable liquidity path | Offer retry / smaller amount / alternate asset |
| `QUOTE_EXPIRED` | Quote passed validity window | Refresh automatically or ask user to refresh |
| `PRICE_MOVED` | Execution conditions changed materially | Re-quote and require reconfirmation |
| `RPC_ERROR` | Provider unavailable | Retry with bounded fallback |

## Non-functional considerations

- latency targets;
- rate limits;
- idempotent quote identifiers where appropriate;
- observability by failure category;
- versioned response schema;
- clear distinction between quote generation and transaction execution.
