# Hermes Skills

Curated reusable skills for Hermes Agent, extracted from real multi-agent production workflows and cleaned for public reuse.

## Scope

- Reusable Hermes skills only
- No private credentials
- No personal chat IDs
- No machine-specific absolute paths
- No user-bound delivery instructions

## Initial Collections

- `skills/ai-meta-cognitive-engine`
- `skills/feishu-file-transfer`
- `skills/output-persistence`
- `skills/hermes-system-evolution`
- `skills/trading-system-v8-memory`
- `skills/trading-system-v8-llm-filter`
- `skills/web3-daily-dashboard`
- `skills/jerry-trading-engine-v8`

## Publishing Rules

1. Replace all local absolute paths with placeholders or relative conventions.
2. Replace all personal references with role-neutral wording.
3. Move all secrets and vendor credentials to environment variables.
4. Add operational caveats for any finance or messaging workflow.
5. Keep each skill independently usable.

## Maintenance

This repository is maintained as a living public mirror of selected Hermes production skills after sanitization and hardening.
