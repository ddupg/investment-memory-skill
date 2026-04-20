# Sub-skill: make-recommendation

## Goal
Generate a recommendation grounded in historical preferences, portfolio context, thesis, and recent actions.

## Before recommending
Check:
1. Does this violate active preferences?
2. Does this fit the target market strategy?
3. Does the relevant market account have enough free cash?
4. Does this exceed size / sector / cash rules?
5. Does this violate the market priority order or currency rules?
6. Does this contradict the active thesis?
7. Was there a recent opposite action?
8. Is the suggestion based on facts, opinions, or both?

## Output structure
- Recommendation
- Why
- Historical basis
- Strategy fit
- Funding fit
- Consistency with prior thesis
- Risks
- What would change the view

## Recommendation style
- Prefer small, explicit actions over vague advice
- State uncertainty clearly
- If recommendation differs from prior behavior, explain why
- If the name is outside the preferred market order, explain why it still deserves capital
- If the strategy fits but cash is tight, prefer sizing guidance over a binary yes/no
- If historical context is weak, say so
