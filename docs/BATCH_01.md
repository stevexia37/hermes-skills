# Batch 01

This document records the first public release batch for `hermes-skills`.

## Included Skills

- `ai-meta-cognitive-engine`
- `feishu-file-transfer`
- `output-persistence`
- `trading-system-v8-memory`
- `trading-system-v8-llm-filter`
- `web3-daily-dashboard`
- `jerry-trading-engine-v8`

## Batch Theme

Batch 01 focuses on skills that are useful across real Hermes deployments after sanitization:

- reasoning and meta-cognition
- output delivery and persistence
- research, memory, and trading-system scaffolds

## What Was Intentionally Excluded

The following stayed out of Batch 01 because they still carry higher risk or stronger environment coupling:

- `feishu-file-delivery`
- `okx-automated-trading`
- any skill with live credentials, hard-coded routing targets, or machine-bound paths

## Release Standard Applied

Every skill in Batch 01 was checked against the public repository standard:

- no private credentials
- no personal delivery bindings
- no environment-specific absolute paths
- no one-machine-only assumptions without documentation

## Suggested Reading Order

1. [README.md](../README.md)
2. [SKILL_INDEX.md](./SKILL_INDEX.md)
3. [EXAMPLES.md](./EXAMPLES.md)
4. [SECURITY_BOUNDARY.md](./SECURITY_BOUNDARY.md)

## Follow-Up

Future batches should continue to prefer:

- reusable patterns
- explicit configuration
- low-risk public sharing

They should continue to avoid publishing raw operational automations without cleanup.
