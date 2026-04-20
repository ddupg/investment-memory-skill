# Sub-skill: write-memory

## Goal
Write new records into the investment memory repository while preserving history and readability.

## Rules
- Facts are append-only
- Do not silently rewrite historical events
- Long reasoning goes into markdown
- Current config can be updated, but archive prior versions first

## Write targets
- New decision -> `decisions/YYYY/YYYY-MM-DD-symbol-action.md`
- New factual event -> append to `events/YYYY/YYYY-MM.jsonl`
- Thesis update -> update `theses/<SYMBOL>/thesis.md` and append to `updates.jsonl`
- Preference update -> archive old `preferences/active.yaml`, then write new one

## Metadata
Include as relevant:
- ts
- type
- symbol
- source
- confidence
- decision_id
- linked_theses
- linked_events
- tags
