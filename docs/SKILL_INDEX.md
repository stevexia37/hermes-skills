# Skill Index

This index gives a quick browsing layer over the first public batch in `hermes-skills`.

## Strategy, Research, and Meta

### `ai-meta-cognitive-engine`

- Purpose: meta-reasoning scaffold for reflective agent operation
- Best for: self-checks, adaptive planning, internal review loops
- Notes: intentionally generic and safe to reuse across different Hermes profiles

### `web3-daily-dashboard`

- Purpose: recurring research and briefing workflow for daily Web3 signal tracking
- Best for: morning reports, ecosystem scans, trend summaries
- Notes: designed as a reporting skill rather than an execution bot

### `jerry-trading-engine-v8`

- Purpose: high-level architecture and orchestration skill for Jerry's trading workflow
- Best for: strategy framing, system decomposition, role separation
- Notes: published as a planning and system-design layer, not as an opinionated execution package

## Messaging and Output

### `feishu-file-transfer`

- Purpose: generalized workflow for sending generated files back through Feishu/Lark
- Best for: report delivery, document handoff, file-based agent outputs
- Notes: public version removes account-specific bindings and assumes environment-based configuration

### `output-persistence`

- Purpose: durable save-and-handoff pattern for preserving important outputs
- Best for: reports, summaries, artifacts, task handoff
- Notes: public version removes local path coupling and private delivery rules

## Trading System Components

### `trading-system-v8-memory`

- Purpose: memory layer for strategy state, observations, and historical signal context
- Best for: persistent trading context and long-horizon review
- Notes: useful even outside trading when an agent needs structured long-lived state

### `trading-system-v8-llm-filter`

- Purpose: LLM-based filtering layer for noisy candidate signals
- Best for: triage, ranking, filtering, and reducing action noise
- Notes: provider bindings should be configured through environment variables in downstream usage

## Publishing Standards

These public skills were selected because they can be shared after sanitization. The current repository standard is:

- no private app IDs, chat IDs, tokens, or internal endpoints
- no hard-coded user-specific absolute paths
- no org-specific routing rules or personal names unless clearly marked as placeholders
- favor reusable patterns over one-machine operational scripts
