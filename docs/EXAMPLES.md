# Examples

This page shows lightweight example use cases for the first public batch in `hermes-skills`.

## `ai-meta-cognitive-engine`

Use when an agent should pause and review its own plan quality before continuing.

Example:

- inspect whether the current plan is drifting from the user's stated objective
- identify hidden assumptions before a long multi-step task
- decide whether to continue, revise, or ask for clarification

## `feishu-file-transfer`

Use when an agent has already produced a file and needs to hand it back through Feishu/Lark.

Example:

- generate a PDF report, then send it to the target chat
- export a spreadsheet and deliver it to the requester
- return a generated deck or briefing file after task completion

## `output-persistence`

Use when important outputs should not remain buried in a transient chat session.

Example:

- persist a finalized report to a shared workspace
- save a summary and handoff note for another agent
- archive a generated artifact before follow-up work begins

## `trading-system-v8-memory`

Use when signal review should include historical state rather than only the current snapshot.

Example:

- compare today's candidate signals against prior observations
- preserve strategy rationale across recurring runs
- carry forward structured memory for later review

## `trading-system-v8-llm-filter`

Use when a large raw signal set needs a fast first-pass reduction.

Example:

- rank candidate observations before deeper review
- reject noisy signals that do not meet minimum quality bars
- group high-priority candidates for downstream execution or reporting

## `web3-daily-dashboard`

Use when a recurring scan should be turned into a compact daily brief.

Example:

- produce a daily Web3 market pulse summary
- highlight ecosystem developments worth follow-up research
- turn raw monitoring inputs into a readable morning briefing

## `jerry-trading-engine-v8`

Use when you want the system architecture around a trading workflow rather than a single narrow task.

Example:

- separate memory, filtering, and execution responsibilities
- define a repeatable daily operating loop for trading research
- structure a role-based trading agent stack before adding implementation details
