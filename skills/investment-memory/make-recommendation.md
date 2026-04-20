# Sub-skill: make-recommendation

## Goal
Generate a recommendation grounded in historical preferences, portfolio context, thesis, and recent actions.

## Before recommending
Check:
1. Does this violate active preferences?
2. Does this exceed size / sector / cash rules?
3. Does this violate the market priority order or currency rules?
4. Does this contradict the active thesis?
5. Was there a recent opposite action?
6. Is the suggestion based on facts, opinions, or both?

## Output structure
- Recommendation
- Why
- Historical basis
- Consistency with prior thesis
- Risks
- What would change the view

## Recommendation style
- Prefer small, explicit actions over vague advice
- State uncertainty clearly
- If recommendation differs from prior behavior, explain why
- If the name is outside the preferred market order, explain why it still deserves capital
- If historical context is weak, say so
