---
name: trading-system-v8-llm-filter
description: Secondary LLM-based signal confirmation and lightweight sentiment guarding for trading workflows.
category: trading
tags: [llm, signal-filter, sentiment, trading]
---

# Trading System v8 LLM Filter

## Purpose

Add a secondary confirmation layer between rule-based trade signals and execution. This skill is designed to:

- reduce false breakouts
- delay weak entries
- incorporate lightweight sentiment gating

## Signal Filter

Suggested module:

`signal_filter.py`

### Architecture

- use a lightweight model for low-latency confirmation
- apply a short timeout and degrade gracefully on failure
- cache recent checks to avoid repeated calls for the same setup
- keep temperature low for stable structured responses

### Core Methods

```python
class SignalFilter:
    def __init__(self, api_key=None, model="small-fast-model")
    def confirm_signal(self, signal_data)
    def get_stats(self)
```

### Suggested Response Format

```json
{"action": "confirm|reject|delay", "confidence": 0.0, "reason": "short explanation"}
```

## Prompt Design

Include:

- symbol
- action
- entry price
- trend
- RSI
- volatility
- band position or equivalent setup features
- optional memory-derived advice

Constrain output to strict JSON.

## Integration Pattern

```python
signal_data = {
    "symbol": sym,
    "action": "BUY",
    "price": px,
    "context": ctx,
    "memory_advice": advice,
}

llm_result = signal_filter.confirm_signal(signal_data)

if llm_result["action"] == "reject":
    return
elif llm_result["action"] == "delay":
    return
```

## Sentiment Guardian

Suggested module:

`sentiment_guardian.py`

### Purpose

Block or reduce buying when broader market sentiment becomes extreme or structurally unstable.

### Example Output

```json
{
  "action": "ALLOW|PAUSE_BUY",
  "composite": 0.78,
  "reason": "sentiment healthy"
}
```

### Example Integration

```python
sent_result = sentiment.check_market_sentiment(sym)
sentiment_factor = 0.3 if sent_result["action"] == "PAUSE_BUY" else 1.0
trade_amt *= sentiment_factor
```

## Operational Guidance

1. Keep model calls short and bounded by timeout.
2. Fallback behavior should be explicit and predictable.
3. Do not let external API latency block the main execution loop.
4. Treat sentiment as a position-weighting input, not as a full trading strategy.

## Pitfalls

1. Hard-coding one provider makes the skill harder to reuse.
2. Proxy assumptions should never be embedded in the public version.
3. Placeholder sentiment sources are acceptable for scaffolding, but production use needs real feeds.
4. Cache windows should match the trading horizon.

## Safety Note

This skill is for automation engineering and signal hygiene. It does not provide investment advice and should always be paired with explicit risk controls.
