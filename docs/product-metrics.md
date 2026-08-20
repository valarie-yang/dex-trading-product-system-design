# Product Metrics

These are **proposed product metrics** for a DEX trading product. They are not presented as production results.

## Funnel

1. Wallet connected
2. Quote requested
3. Quote returned
4. Trade preview opened
5. Transaction signed
6. Transaction submitted
7. Transaction confirmed / order filled

Useful conversion metrics:
- quote-to-preview rate;
- preview-to-sign rate;
- sign-to-submit rate;
- submit-to-success rate;
- end-to-end trade conversion.

## Reliability

- quote success rate;
- transaction success rate;
- failed transaction rate by reason;
- stale-quote rate;
- RPC / provider error rate;
- settlement / indexing delay rate.

## Trading quality

- realized vs. quoted output;
- price impact distribution;
- slippage distribution;
- route quality vs. alternative path;
- order fill rate;
- partial-fill rate;
- cancellation rate.

## Speed

- quote latency p50 / p95;
- time from preview to signature;
- time from submit to confirmation;
- time to order acknowledgement / execution report.

## Risk / support

- insufficient-balance failures;
- allowance / approval failures;
- user-rejected signatures;
- contract-revert rate;
- support tickets per 1,000 trades.

## PM interpretation

A higher trade conversion rate is not automatically better if it is achieved by hiding risk or degrading execution quality. Product health should balance conversion, execution quality, reliability and user protection.
