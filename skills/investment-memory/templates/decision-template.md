---
decision_id: dec-<YYYY-MM-DD>-<instrument-slug>-<action>
ts: <ISO8601 timestamp>
instrument_id: <INSTRUMENT_ID>
symbol: <SYMBOL>
market: <CN_A|HK|US>
exchange: <EXCHANGE>
currency: <CURRENCY>
security_type: equity
action: <buy|add|trim|sell|hold|avoid>
status: <proposed|executed|canceled>
confidence: <0.00-1.00>
source: <manual|agent>
linked_theses:
  - thesis-<instrument-slug>-core
linked_events: []
tags:
  - <tag>
---

# Context

Why this name is under review now.

# Historical background

What the existing preferences, position, and thesis already say.

# Why act now

- Concrete supporting reason

# Why not wait

- What would be lost by waiting

# Risks

- Main downside

# Preference check

Confirm the action against position, market, and currency constraints.

# Consistency with prior thesis

Explain whether this matches or updates the active thesis.

# Follow-up conditions

What would change the view or trigger the next action.
