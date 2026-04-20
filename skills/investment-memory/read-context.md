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
3. `strategy/active.yaml`
4. `allocation/target.yaml`
5. latest `market-accounts/snapshots/*.json`
6. latest `snapshots/portfolio/*.json`
7. if a security is involved, first resolve it to canonical `instrument_id`
8. then read:
   - `theses/<INSTRUMENT_ID>/thesis.md`
   - recent `theses/<INSTRUMENT_ID>/updates.jsonl`
9. recent `events/YYYY/YYYY-MM.jsonl`
10. related `decisions/YYYY/*.md` only if deeper rationale is needed

## Rules
- Start from active preferences
- Prefer recent context over old context
- Distinguish facts from opinions
- Use `market_preference_order` when the user gives only a company name or an ambiguous ticker
- Use market-level funds and strategy state when deciding whether a buy is actionable now
- If sources conflict, prefer:
  1. active preferences
  2. active strategy
  3. latest market-account snapshot
  4. latest execution events
  5. latest thesis updates
  6. thesis.md
  7. older decisions

## Extract at least
- active constraints
- market preference order
- market-level strategy rules
- current market-level available cash
- current portfolio state
- relevant security stance
- recent actions
- currency exposure if relevant
- any recent contradiction or thesis drift
