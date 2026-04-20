# Sub-skill: read-context

## Goal
Retrieve only the minimum relevant historical context before answering.

## Read order
1. `memory_index.yaml`
2. `preferences/active.yaml`
3. latest `snapshots/portfolio/*.json`
4. if a symbol is involved:
   - `theses/<SYMBOL>/thesis.md`
   - recent `theses/<SYMBOL>/updates.jsonl`
5. recent `events/YYYY/YYYY-MM.jsonl`
6. related `decisions/YYYY/*.md` only if deeper rationale is needed

## Rules
- Start from active preferences
- Prefer recent context over old context
- Distinguish facts from opinions
- If sources conflict, prefer:
  1. active preferences
  2. latest execution events
  3. latest thesis updates
  4. thesis.md
  5. older decisions

## Extract at least
- active constraints
- current portfolio state
- relevant symbol stance
- recent actions
- any recent contradiction or thesis drift
