# Planescape API Subset

This document records the Beads project-local subset required before
Planescape treats Beads projection as available.

## Required Surface

- Project-local discovery with `bd where`.
- Stable issue lookup with `bd show <id>` and `bd show --json <id>`.
- JSONL projection with `bd export -o <tmp>/issues.jsonl`.
- Explicit-id issue creation semantics, checked with `bd create --dry-run --id`.
- Custom issue type configuration in `.beads/config.yaml` for existing Beads
  infrastructure records.
- Dependency metadata in exported JSONL for parent-child relationships.

## Verification

Run from `/Users/dr/workspace/beads`:

```bash
scripts/verify-planescape-api-subset
```

The script is read-only with respect to tracked issue state. It exports to a
temporary directory, validates the `bd-planescape-api` and
`bd-planescape-api-verify` records, checks custom issue type configuration, and
prints a JSON result with the Beads commit and `bd version`.

Planescape and ops must not treat Beads projection as available unless this
script passes from a pinned Beads commit.
