# Roadmap

This roadmap tracks how `hermes-skills` is being expanded from a first public batch into a broader reusable library.

## Current State

Published in the current public batch:

- `ai-meta-cognitive-engine`
- `feishu-file-transfer`
- `output-persistence`
- `trading-system-v8-memory`
- `trading-system-v8-llm-filter`
- `web3-daily-dashboard`
- `jerry-trading-engine-v8`

## Next Candidates

These are strong candidates for the next public round after additional cleanup:

- `hermes-system-evolution`
- more generalized reporting and delivery helpers
- more strategy and memory-layer skills that do not expose environment-specific bindings

## Hold-Back Rules

Skills stay out of the public repository when they still include one or more of the following:

- private app IDs, chat IDs, or bot bindings
- machine-specific paths
- account-specific routing logic
- execution flows that are risky to copy blindly
- vendor coupling without clear environment-variable setup

## Upstream Alignment

This repository is also used to inform upstream Hermes improvements. In practice that means:

- publishing patterns that are reusable outside one machine
- documenting cleanup steps needed before skills become shareable
- feeding migration and profile-isolation lessons back into upstream Hermes docs

## Short-Term Priorities

1. keep improving public documentation and examples
2. publish the next safe sanitized batch
3. continue preparing upstream Hermes documentation PRs
4. keep a clean line between public skills and private operations
