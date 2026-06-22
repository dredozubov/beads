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

## Last Verification

Run from `/Users/dr/workspace/beads` on 2026-06-22:

```bash
scripts/verify-planescape-api-subset
```

Result:

```json
{"ok":true,"repo":"/Users/dr/workspace/beads","commit":"002a05a4","bd_version":"bd version 1.0.3 (Homebrew) ","workspace":"/Users/dr/workspace/beads/.beads","checked":["where","show","show_json","create_dry_run_explicit_id","export_jsonl","custom_types_config"]}
```
