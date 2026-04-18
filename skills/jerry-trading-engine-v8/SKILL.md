---
name: jerry-trading-engine-v8
description: Modular trading engine pattern combining memory, LLM filtering, sentiment gating, and dynamic risk parameters.
category: trading
tags: [trading, automation, bm25, llm, sentiment, risk-management]
---

# Jerry Trading Engine v8

## Purpose

This skill documents a modular trading-engine architecture that combines:

- strategy memory
- LLM-based signal confirmation
- sentiment-aware position throttling
- dynamic take-profit and stop-loss adjustment

It is intended as an automation architecture reference, not as financial advice.

## High-Level Architecture

```text
Market Context
  -> Rule-Based Signal Layer
  -> Strategy Memory Advice
  -> LLM Signal Filter
  -> Sentiment Guard
  -> Dynamic Risk Parameter Adjustment
  -> Execution Layer
  -> Reflection + State Update
```

## Suggested File Layout

| File | Role |
| --- | --- |
| `jerry_trader.py` | main engine entry |
| `strategy_memory.py` | BM25 retrieval and reflection |
| `signal_filter.py` | LLM confirmation layer |
| `sentiment_guardian.py` | sentiment gating |
| `dynamic_params.py` | dynamic TP/SL and risk scaling |
| `state.json` | durable local state |

## Suggested Runtime Flow

1. Initialize all support modules.
2. Build market context.
3. Manage open positions.
4. Query strategy memory for similar historical cases.
5. Run LLM confirmation on new entries.
6. Apply sentiment weighting.
7. Adjust TP, SL, and position size dynamically.
8. Execute only if all gates pass.
9. Persist state and generate reflection on exit.

## Risk Parameter Examples

| Parameter | Example Default | Notes |
| --- | --- | --- |
| Take Profit | 1.5% | should adapt to volatility and confidence |
| Stop Loss | -0.5% | must remain bounded |
| Base Position Size | 30% | should be capped |
| Max Hold Time | 30 min | enforce time-based cleanup |
| Daily Loss Limit | fixed ceiling | stop trading after breach |

## Integration Notes

### Memory

Use memory as a position-sizing modifier, not as the sole entry decision.

### LLM Filter

Use short timeouts and deterministic output constraints. Fail closed or degrade predictably.

### Sentiment

Treat sentiment as a throttle rather than a full strategy.

### Dynamic Parameters

Keep hard bounds around all auto-adjusted values. Dynamic logic should never bypass global risk caps.

## Public Release Rules

- Never publish live credentials
- Never ship exchange-specific secrets in code examples
- Keep vendor endpoints configurable
- Keep proxy assumptions out of the public version
- Include explicit warnings for live deployment

## Safety Note

This skill describes an engineering pattern for automated trading workflows. It does not provide investment advice, expected returns, or guarantees of profitability. Any real deployment requires separate venue testing, operational monitoring, and strict risk controls.
