# Maintenance Workflow

## Intake

1. Identify a profile-local skill worth publishing.
2. Copy it into a staging branch or local staging directory.
3. Sanitize private data and environment bindings.
4. Add examples and operational notes.
5. Review for public safety and reuse quality.

## Release Checklist

- No absolute user-specific paths
- No hard-coded app IDs or chat IDs
- No personal names or private operating assumptions
- Environment variables documented
- External dependencies listed
- Risks and limitations documented

## Upstream Strategy

Some improvements belong in the public skill repository.
Some improvements belong upstream in `NousResearch/hermes-agent`.

Use this split:

- Repository: reusable skills and documentation
- Upstream PRs: framework bugs, skill lifecycle tooling, profile isolation, messaging reliability
