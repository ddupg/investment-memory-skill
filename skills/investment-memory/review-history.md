# Sub-skill: review-history

## Goal
Review historical actions, thesis evolution, and decision quality.

## Repository root
Default root: `~/.investment-memory`

## Review flow
1. Read active preferences
2. Read active strategy and target allocation
3. Read the latest market-account snapshot
4. Resolve the target to canonical `instrument_id`
5. Load relevant thesis or portfolio snapshot
6. Scan recent and historically important events
7. Read linked decision files
8. Summarize:
   - what happened
   - how the thesis changed
   - what worked
   - what failed
   - whether current positioning still fits preferences
   - whether the position still fits the market strategy and available funds
   - what to do next

## Output
- Timeline
- Key thesis changes
- Repeated patterns
- Errors or drift
- Market or currency mismatch
- Next-step recommendation
