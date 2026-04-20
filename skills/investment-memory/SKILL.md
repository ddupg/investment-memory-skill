# Skill: investment-memory

Use the personal investment memory repository to retrieve history, apply user preferences,
generate grounded investment suggestions, and write back new records.

## Use this skill when
- answering investment questions that depend on user history
- reviewing a position
- checking whether an action fits preferences
- recording a new decision, thesis update, or execution
- generating a review or summary

## Routing
Choose the smallest relevant sub-skill set:

- Market question / consultation / "what do you think?"
  -> use `read-context.md` + `make-recommendation.md`

- Symbol-specific recommendation
  -> use `read-context.md` + `make-recommendation.md`

- Record a buy / sell / add / trim / thesis change / preference change
  -> use `write-memory.md`

- Review past actions / summarize lessons / generate periodic report
  -> use `read-context.md` + `review-history.md`

## Repository
The repository is a lightweight file-based investment memory store.
Prefer human-readable files and append-only factual logs.
