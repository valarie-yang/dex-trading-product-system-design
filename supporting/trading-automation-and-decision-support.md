# Supporting Study — Trading Automation & Decision Support

This supporting case reframes an earlier trading-bot concept as a broader **trading automation and decision-support product**. The goal is to demonstrate product segmentation, automation design and future AI-product extensibility without presenting the bot as a separate flagship crypto project.

## Product question

How can one trading product support both users who want a fast, simplified workflow and more experienced traders who want control over execution and risk?

## User modes

### Quick Mode
Designed for lower-friction execution:
- simplified strategy selection;
- opinionated defaults;
- limited advanced configuration;
- clear expected outcome and risk summary;
- fast execution path.

### Secure / Advanced Mode
Designed for users who want more control:
- wallet selection;
- network / token validation;
- Gas and slippage controls;
- price-impact visibility;
- strategy parameters;
- execution preview;
- explicit risk checks.

## Product capabilities

- multi-wallet management;
- multi-network support concepts (e.g. EVM / Solana-style flows);
- contract-address validation;
- automated trading strategies;
- Gas / Slippage / Price Impact controls;
- portfolio and performance views;
- strategy state and execution history;
- stop / pause / failure handling.

## Automation state model

```text
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
EXECUTED
  ↓
MONITORING

Alternative states:
PAUSED / FAILED / STOPPED / EXPIRED
```

## Future AI extension

A useful AI layer should not simply generate trading instructions. It should support **decision explanation and controlled automation**.

Potential capabilities:
- explain why a strategy condition was triggered;
- summarize current exposure and configured risk limits;
- compare strategy settings using historical/synthetic examples;
- explain execution failure or price deviation;
- recommend parameter ranges with explicit assumptions;
- require user confirmation before material strategy changes.

## AI guardrails

- separate factual market/account state from generated interpretation;
- cite data used in an explanation;
- expose uncertainty and assumptions;
- never imply guaranteed returns;
- maintain deterministic controls for execution and risk limits;
- require human confirmation for high-impact actions.

## Why this is a supporting case

The flagship DEX case demonstrates trading-system product depth. This supporting study demonstrates how that foundation can extend into automation and AI-assisted decision support, making it more relevant to future AI × FinTech / AI × trading product roles.
