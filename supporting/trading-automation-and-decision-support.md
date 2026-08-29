# Supporting Study — Trading Automation & Decision Support

This supporting case reframes an earlier trading-bot concept as a broader trading automation and decision-support product. It demonstrates product segmentation, automation design, and future AI-product extensibility without presenting the bot as a separate flagship crypto project.

**Status:** Illustrative product design / future-scope study. The repository does not implement live trading, signing, broadcasting, custody, or automated order execution.

## Product question

How can one self-custodial trading product support both users who want a fast, simplified workflow and experienced traders who want control over execution and risk?

## User modes

### Quick Mode

Designed for lower-friction product exploration:

- simplified strategy selection;
- opinionated defaults;
- limited advanced configuration;
- clear expected outcome and risk summary;
- simulated or user-confirmed execution path.

### Secure / Advanced Mode

Designed for users who want more control:

- wallet and network selection;
- token and contract-address validation;
- gas, slippage, and price-impact controls;
- strategy parameters;
- execution preview;
- explicit risk checks;
- visible signature and confirmation stages.

## Designed capabilities

The following are product capabilities under consideration, not a claim of implementation:

- multi-wallet and multi-network concepts;
- contract-address validation;
- configurable strategy conditions;
- portfolio and performance views;
- strategy state and execution history;
- stop, pause, expiry, and failure handling.

## Illustrative automation state model

    DRAFT
      ↓
    VALIDATED
      ↓
    ACTIVE
      ↓
    SIGNAL_TRIGGERED
      ↓
    EXECUTION_PENDING
      ↓
    USER_CONFIRMATION_REQUIRED
      ↓
    MONITORING

Alternative states: PAUSED / FAILED / STOPPED / EXPIRED

The states are a product design artifact. Any real execution would require a separate, explicit wallet-confirmation boundary and a production implementation that is not included here.

## AI-assisted decision-support layer

A useful AI layer should support decision explanation and controlled comparison—not generate authoritative trading instructions.

Potential future capabilities:

- explain why a deterministic strategy condition was triggered;
- summarize exposure against configured risk limits;
- compare synthetic scenarios and parameter assumptions;
- explain quote expiry, execution failure, or price deviation;
- surface candidate parameter ranges with assumptions for user review.

## Non-execution boundary

The AI layer is read-only. It must not access private keys, invoke wallet signing, broadcast transactions, submit orders, alter risk limits, or move funds.

Balances, quotes, fees, gas, slippage, price impact, margin, and liquidation indicators should come from explicit data snapshots and deterministic calculations. The language model may explain those results with citations, assumptions, and uncertainty.

This is not investment advice and does not provide personalized buy, sell, allocation, or guaranteed-return recommendations. Any high-impact action requires user review and explicit wallet confirmation.

## Why this is a supporting case

The flagship DEX case demonstrates trading-system product depth. This supporting study demonstrates how that foundation can extend into automation and AI-assisted decision support while preserving self-custody, risk visibility, and execution truth.
