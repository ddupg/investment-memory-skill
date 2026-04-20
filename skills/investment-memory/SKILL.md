# Skill: investment-memory

Use the personal investment memory repository to retrieve history, apply user preferences,
generate grounded investment suggestions, and write back new records.

## Routing
- Market question -> read-context + make-recommendation
- Symbol recommendation -> read-context + make-recommendation
- Record action -> write-memory
- Review -> read-context + review-history
