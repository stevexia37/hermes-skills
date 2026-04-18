# Release Checklist

Use this checklist before publishing a new skill or release batch to `hermes-skills`.

## Skill-Level Checks

- [ ] no private credentials or tokens
- [ ] no live app IDs, chat IDs, or personal routing targets
- [ ] no machine-specific absolute filesystem paths
- [ ] no environment-specific assumptions without explanation
- [ ] placeholders are clearly marked
- [ ] dependencies are mentioned when required
- [ ] safety notes are included for risky domains
- [ ] the skill can be understood outside the original deployment

## Repository-Level Checks

- [ ] `README.md` navigation points to the new material
- [ ] `docs/SKILL_INDEX.md` includes the new skill if appropriate
- [ ] `docs/BATCH_01.md` or a later batch manifest is updated
- [ ] `docs/ROADMAP.md` still reflects the next likely public candidates
- [ ] `docs/SECURITY_BOUNDARY.md` is still consistent with the published scope

## Final Sanity Pass

- [ ] review the skill as if it were being copied by a stranger
- [ ] confirm that copy-paste usage would not leak or trigger private operations
- [ ] confirm the public version is the sanitized version, not the local working version
