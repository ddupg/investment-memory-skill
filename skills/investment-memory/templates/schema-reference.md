# Schema Reference

This file is the canonical write contract for the investment-memory skill.

Agents must read this file before creating or substantially rewriting any record.

## Storage principles

- Use `instrument_id` as the canonical identity key.
- Use append-only writes for factual history where possible.
- Keep thesis summaries readable in Markdown.
- Treat repository samples as examples, not as the schema source of truth.

## Canonical identity fields

Every security-specific record should include:

- `instrument_id`
- `symbol`
- `market`
- `exchange`
- `currency`
- `security_type`

Examples:

- `600519.SH`
- `00700.HK`
- `NVDA.US`

## Path rules

- Thesis summary: `investment-memory/theses/<INSTRUMENT_ID>/thesis.md`
- Thesis updates: `investment-memory/theses/<INSTRUMENT_ID>/updates.jsonl`
- Decisions: `investment-memory/decisions/YYYY/YYYY-MM-DD-<instrument-slug>-<action>.md`
- Events: `investment-memory/events/YYYY/YYYY-MM.jsonl`
- Active preferences: `investment-memory/preferences/active.yaml`
- Archived preferences: `investment-memory/preferences/history/YYYY-MM-DD.yaml`
- Latest snapshot: `investment-memory/snapshots/portfolio/latest.json`

`<instrument-slug>` should be lowercase and replace separators with hyphens.

Examples:

- `600519.SH` -> `600519-sh`
- `00700.HK` -> `00700-hk`
- `NVDA.US` -> `nvda-us`

## Write rules

Before writing:

1. Load this schema reference.
2. Load the matching template from this directory.
3. Resolve the security to one canonical `instrument_id`.
4. Reuse existing field names exactly.

Do not:

- invent alternate field names for the same concept
- store a bare `symbol` without market metadata
- overwrite historical events to "clean up" the past
- create a new thesis directory using only `symbol`

## Minimum required fields by record type

### Event records

- `ts`
- `type`
- `source`
- security fields when security-specific
- `decision_id` when linked to a decision

### Decision files

- front matter with `decision_id`, `ts`, `action`, `status`, `source`
- full security identity fields
- `linked_theses`
- `linked_events`
- `tags`

### Thesis summary files

- front matter with full security identity fields
- `status`
- `stance`
- `updated_at`
- `horizon`
- `confidence`
- `invalidates_if`
- `action_bias`

### Portfolio snapshots

- `ts`
- `base_currency`
- `cash_pct`
- `positions`
- `market_exposure_pct`

## Market conventions

- `CN_A`: mainland A-shares traded in CNY on `SH` or `SZ`
- `HK`: Hong Kong equities traded in HKD on `HK`
- `US`: US equities traded in USD on `NASDAQ` or `NYSE`

## Template files

- `decision-template.md`
- `thesis-template.md`
- `event-template.json`
- `preference-template.yaml`
- `portfolio-snapshot-template.json`
