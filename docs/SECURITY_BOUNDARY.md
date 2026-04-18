# Security Boundary

`hermes-skills` is meant to publish reusable skills, not private operating state.

This document defines the line between what belongs in the public repository and what must remain local or private.

## Never Publish

The following must never be committed to this repository:

- private API keys or access tokens
- chat IDs, app IDs, or account-specific bot bindings that identify a live deployment
- absolute local filesystem paths tied to one machine
- hostnames, private endpoints, or internal service URLs that are not intentionally public
- personally identifying routing logic or delivery instructions tied to one operator
- unattended execution flows that can trigger real-world actions without explicit safety framing

## Publish Only After Sanitization

These patterns can be valuable, but only after cleanup:

- messaging delivery skills
- execution or trading scaffolds
- workflow skills that call local scripts
- environment-coupled reporting pipelines

Public-ready versions should:

- switch secrets to environment variables
- replace real IDs with placeholders
- remove machine-specific path assumptions
- explain expected runtime dependencies
- include domain-specific safety notes where needed

## Good Public Candidates

The best public skills usually look like:

- reasoning scaffolds
- research and reporting patterns
- memory architecture patterns
- generalized delivery or handoff workflows
- reusable orchestration layers

## Review Questions

Before publishing a skill, ask:

1. Would this leak anything about one real deployment?
2. Would someone else understand how to configure it safely?
3. Does it depend on one machine, one user, or one private environment?
4. Could a copy-paste use of this skill cause unintended real-world effects?

If the answer to any of these is unclear, the skill should stay private until revised.
