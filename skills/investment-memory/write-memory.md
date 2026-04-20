# Sub-skill: write-memory

## Goal
Write new records into the investment memory repository while preserving history and readability.

## Rules
- Facts are append-only
- Do not silently rewrite historical events
- Long reasoning goes into markdown
- Current config can be updated, but archive prior versions first
- Before writing, load `templates/schema-reference.md` and the matching template
- Reuse canonical field names exactly
- Use `instrument_id` as the storage key for security-specific files

## Write targets
- New decision -> `decisions/YYYY/YYYY-MM-DD-<instrument-slug>-<action>.md`
- New factual event -> append to `events/YYYY/YYYY-MM.jsonl`
- Thesis update -> update `theses/<INSTRUMENT_ID>/thesis.md` and append to `updates.jsonl`
- Preference update -> archive old `preferences/active.yaml`, then write new one

## Metadata
Include as relevant:
- ts
- instrument_id
- type
- symbol
- market
- exchange
- currency
- security_type
- source
- confidence
- decision_id
- linked_theses
- linked_events
- tags
