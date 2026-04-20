# Sub-skill: read-context

## Goal
Retrieve only the minimum relevant historical context before answering.

## Repository root
Default root: `~/.investment-memory`

If the user does not specify another location, resolve every path in this file relative
to `~/.investment-memory`.

## Read order
1. `memory_index.yaml`
2. `preferences/active.yaml`
3. latest `snapshots/portfolio/*.json`
4. if a security is involved, first resolve it to canonical `instrument_id`
5. then read:
   - `theses/<INSTRUMENT_ID>/thesis.md`
   - recent `theses/<INSTRUMENT_ID>/updates.jsonl`
6. recent `events/YYYY/YYYY-MM.jsonl`
7. related `decisions/YYYY/*.md` only if deeper rationale is needed

## Rules
- Start from active preferences
- Prefer recent context over old context
- Distinguish facts from opinions
- Use `market_preference_order` when the user gives only a company name or an ambiguous ticker
- If sources conflict, prefer:
  1. active preferences
  2. latest execution events
  3. latest thesis updates
  4. thesis.md
  5. older decisions

## Extract at least
- active constraints
- market preference order
- current portfolio state
- relevant security stance
- recent actions
- currency exposure if relevant
- any recent contradiction or thesis drift
