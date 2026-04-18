---
name: output-persistence
category: devops
description: Ensure important outputs are persistently saved to the filesystem and referenced in durable notes or memory.
trigger: Use when generating any report, document, PDF, plan, dataset, script, or deliverable that must survive session loss.
---

# Output Persistence

## Why This Exists

Agent session context is not a durable storage layer. Important outputs can be lost if they only exist in:

- the current chat context
- temporary cache directories
- unstored tool output

This skill establishes a mandatory persistence workflow for important artifacts.

## Core Rule

All important outputs must be written to a durable `outputs/` directory inside the active project or workspace.

Recommended convention:

```text
workspace/
  outputs/
    report_v1.0.pdf
    design-note_v2.md
    dataset_snapshot_2026-04-18.csv
```

## Required Workflow

### 1. Persist the File

Immediately save or copy the generated artifact into `outputs/`.

### 2. Use Clear Versioned Names

Examples:

- `system_manual_v1.0.pdf`
- `market_dashboard_2026-04-18.md`
- `architecture_review_v2.1.md`

### 3. Record Metadata

Log the artifact in a durable note or memory file with:

- file name
- relative path
- description
- date
- version

Example:

```markdown
## Output Archive
- system_manual_v1.0.pdf -> outputs/system_manual_v1.0.pdf
  Description: system operating manual
  Date: 2026-04-18
```

### 4. Deliver If Needed

If the user expects a pushed or sent artifact, route it through the active delivery mechanism after persistence. Delivery must never replace archival storage.

## Checklist

- [ ] artifact saved to `outputs/`
- [ ] clear versioned file name
- [ ] metadata recorded
- [ ] delivery completed if requested

## Must Persist

- PDF reports
- Markdown reports
- design docs
- configuration files
- datasets
- generated scripts
- exported analysis results

## Optional

- temporary experiments
- intermediate debug logs
- scratch files with no future value

## Common Failure Mode

Generating a file successfully but leaving it only in cache or ephemeral tool state creates silent data loss in later sessions.

This skill exists to prevent that exact failure.
