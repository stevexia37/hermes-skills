---
name: trading-system-v8-memory
description: Strategy memory system for trading workflows using BM25 retrieval, post-trade reflection, and position sizing based on historical outcomes.
category: trading
tags: [memory, bm25, trading, reflection, position-sizing]
---

# Trading System v8 Memory

## Purpose

Add experience accumulation to a trading engine. Record trade context, generate post-trade reflections, retrieve similar scenarios, and adjust position sizing based on historical outcomes.

## Architecture

```text
Trade Entry -> Record Context -> Execute -> Trade Exit -> Generate Reflection -> Update Index
                                                                   |
                                                                   v
Next Signal -> Query Similar Cases -> Estimate Win Rate -> Adjust Position Multiplier
```

## Implementation

Suggested module:

`strategy_memory.py`

### BM25 Layer

- custom BM25 implementation using only standard Python
- no external dependencies required
- tokenization can be rule-based and domain-specific

### Core Methods

```python
class StrategyMemory:
    def __init__(self, state_file)
    def record_trade(self, trade_data)
    def complete_trade(self, trade_id, exit_data)
    def generate_reflection(self, trade_id)
    def query_similar(self, context, top_k=3)
    def get_action_advice(self, context)
    def get_memory_stats(self)
```

## Example Action Advice Table

| Win Rate (Top-K similar) | Action | Position Multiplier |
| --- | --- | --- |
| >= 75% | proceed | 1.2x |
| 60-74% | proceed | 1.0x |
| 40-59% | cautious | 0.6x |
| < 40% | avoid | 0.0x |
| insufficient samples | proceed | 1.0x |

## Reflection Design

Reflections should convert outcomes into reusable lessons, for example:

- trend-aligned oversold entry succeeded
- reversal attempt in a downtrend failed
- high-volatility trade was profitable but risk was elevated

The point is not literary analysis. The point is compact reusable priors for the next trade.

## Integration Pattern

### On Entry

```python
trade_id = memory.record_trade({
    "symbol": sym,
    "action": "BUY",
    "price": px,
    "context": ctx,
})
```

### On Exit

```python
memory.complete_trade(trade_id, {
    "price": exit_px,
    "pnl_pct": pnl_pct,
    "reason": reason,
})
memory.generate_reflection(trade_id)
```

### Before the Next Trade

```python
advice = memory.get_action_advice(ctx)
```

## Pitfalls

1. Advice quality is weak when sample count is too small.
2. Tokenization logic must evolve with the domain vocabulary.
3. Only one process should write to the state file at a time.
4. Old reflections may drift out of relevance over time.
5. This system supports execution quality; it does not replace risk controls.

## Safety Note

This skill is an engineering pattern, not investment advice. Use explicit guardrails, position limits, and venue-specific risk controls in any real deployment.
