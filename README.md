# Hermes Skills

Curated reusable skills for Hermes Agent, extracted from real multi-agent production workflows and cleaned for public reuse.

## What This Repository Is

This repository is a public skill library for Hermes Agent.

It focuses on skills that are:

- reusable across projects
- operationally tested in real agent workflows
- cleaned for public publication
- documented with constraints and safety notes

## Repository Goals

- publish high-signal Hermes skills instead of raw private prompts
- turn production knowledge into reusable public workflows
- maintain a clean boundary between private agent state and open-source skills
- evolve toward a stronger public Hermes skill ecosystem

## Scope

- reusable Hermes skills only
- no private credentials
- no personal chat IDs
- no machine-specific absolute paths
- no user-bound delivery instructions

## Current Skill Index

### Agent Architecture

- [`skills/ai-meta-cognitive-engine`](./skills/ai-meta-cognitive-engine/SKILL.md)

### Productivity / Delivery

- [`skills/feishu-file-transfer`](./skills/feishu-file-transfer/SKILL.md)
- [`skills/output-persistence`](./skills/output-persistence/SKILL.md)

### Trading / Research

- [`skills/trading-system-v8-memory`](./skills/trading-system-v8-memory/SKILL.md)
- [`skills/trading-system-v8-llm-filter`](./skills/trading-system-v8-llm-filter/SKILL.md)
- [`skills/web3-daily-dashboard`](./skills/web3-daily-dashboard/SKILL.md)
- [`skills/jerry-trading-engine-v8`](./skills/jerry-trading-engine-v8/SKILL.md)

## Repository Layout

```text
skills/
  skill-name/
    SKILL.md

docs/
  BATCH_01.md
  EXAMPLES.md
  PUBLISHING_PLAN.md
  REPOSITORY_MAP.md
  ROADMAP.md
  SECURITY_BOUNDARY.md
  SKILL_INDEX.md

README.md
CONTRIBUTING.md
MAINTENANCE.md
CHANGELOG.md
```

## Publishing Standard

Each published skill should meet all of the following:

1. No absolute local paths
2. No personal references or private routing details
3. No hard-coded credentials, chat IDs, or vendor secrets
4. Clear environment-variable requirements where applicable
5. Clear safety notes for risky domains such as finance or messaging
6. Enough context to be usable outside the original machine

## Start Here

- Browse the skill index: [docs/SKILL_INDEX.md](./docs/SKILL_INDEX.md)
- See the first public batch: [docs/BATCH_01.md](./docs/BATCH_01.md)
- See example use cases: [docs/EXAMPLES.md](./docs/EXAMPLES.md)
- See the roadmap: [docs/ROADMAP.md](./docs/ROADMAP.md)
- Review the security boundary: [docs/SECURITY_BOUNDARY.md](./docs/SECURITY_BOUNDARY.md)
- Read the repository map: [docs/REPOSITORY_MAP.md](./docs/REPOSITORY_MAP.md)
- Read contribution rules: [CONTRIBUTING.md](./CONTRIBUTING.md)
- Read maintenance expectations: [MAINTENANCE.md](./MAINTENANCE.md)
- See batch planning: [docs/PUBLISHING_PLAN.md](./docs/PUBLISHING_PLAN.md)

## Quick Start

1. Pick a skill from [docs/SKILL_INDEX.md](./docs/SKILL_INDEX.md)
2. Review its `SKILL.md` for inputs, assumptions, and safety notes
3. Replace any remaining placeholders with your own environment variables
4. Test it in a fresh Hermes session before using it in a shared workflow

## Status

This repository is actively being expanded from a private production skill base into a maintained public collection.
