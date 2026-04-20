# investment-memory package

This repository contains a portable investment-memory skill and a sample file-based
knowledge base for personal investing.

Default runtime storage location for actual user data:

- `~/.investment-memory`

It is designed for a single-writer repository that mainly covers:

- A-share (`CN_A`)
- Hong Kong equities (`HK`)
- US equities (`US`)

## Repository layout

- `skills/investment-memory/`
  Agent instructions, sub-skills, schema reference, and canonical write templates.
- `investment-memory/`
  Example knowledge-base data managed by the skill.
  This is sample data for the skill repository itself, not the default live storage path.

## Design goals

- Human-readable first
- Facts stay append-only where possible
- Long reasoning lives in Markdown
- Every security has a canonical identity, not just a bare ticker
- The same skill can be reused by Codex, OpenClaw, or another file-writing agent

## Canonical identity model

Every tracked security should have these fields:

- `instrument_id`: canonical identifier such as `600519.SH`, `00700.HK`, `NVDA.US`
- `symbol`: broker- or exchange-facing code such as `600519`, `00700`, `NVDA`
- `market`: `CN_A`, `HK`, `US`
- `exchange`: `SH`, `SZ`, `HK`, `NASDAQ`, `NYSE`
- `currency`: `CNY`, `HKD`, `USD`
- `security_type`: usually `equity`, but can be extended later

`instrument_id` is the storage key. File paths, links, and thesis directories should
use it instead of a bare symbol.

## Why templates live inside the skill

Yes: the canonical templates should live inside the skill.

If templates only live in the knowledge base, a new agent can read old files but still
invent new shapes when writing. Putting templates inside `skills/investment-memory/`
solves the portability problem:

- the skill carries its own schema and write contracts
- a fresh repository can be bootstrapped from the skill alone
- different agents can share one canonical write format

The sample files under `investment-memory/` are examples. The authoritative write shape
is defined by:

- [skills/investment-memory/templates/schema-reference.md](/Users/bytedance/opensource/investment-memory-skill/skills/investment-memory/templates/schema-reference.md)
- the matching template files in `skills/investment-memory/templates/`

By default, live investment-memory data should be stored under `~/.investment-memory`.
Do not treat this repository's `investment-memory/` example directory as the default
write target for day-to-day use.

## Agent compatibility

This package is intentionally plain:

- Markdown instructions
- YAML / JSON / JSONL / Markdown data files
- no Codex-only runtime APIs

That means any agent can use it if it can:

1. read the skill instructions
2. read and write local files
3. follow the schema and template rules

### Codex

Two reasonable installation modes:

1. Repo-local
   Keep `skills/investment-memory/` inside the target repository and route investment
   tasks to `skills/investment-memory/SKILL.md` from `AGENTS.md`.

2. User-level skill install
   Copy `skills/investment-memory/` to `$CODEX_HOME/skills/investment-memory/`, then
   point the skill at `~/.investment-memory` unless the user explicitly selects another root.

Recommended Codex routing rule:

```md
When the task involves investment memory lookup, recommendation, thesis updates,
decision logging, or portfolio review, read `skills/investment-memory/SKILL.md`
first and manage the repository rooted at `~/.investment-memory` unless the user explicitly overrides it.
```

### OpenClaw and similar agents

Treat `skills/investment-memory/` as a reusable prompt pack:

1. Load `SKILL.md` as the entry instruction.
2. Route to the referenced sub-files such as `read-context.md` and `write-memory.md`.
3. Grant file access to the knowledge-base root.
   Default root: `~/.investment-memory`
4. Require the agent to load `templates/schema-reference.md` plus the matching template
   before creating or rewriting records.

If an agent framework supports reusable toolkits, package `skills/investment-memory/`
as the toolkit and pass the target repository path as configuration.

## Recommended operating model

For each task, the agent should:

1. Read `skills/investment-memory/SKILL.md`.
2. Resolve the security to a canonical `instrument_id`.
3. Read active preferences and relevant history.
4. Before any write, load the schema reference and the matching template.
5. Write only the minimum required files.

## Current sample scope

The sample knowledge base reflects a preference order of:

1. `CN_A`
2. `HK`
3. `US`

US ideas are still allowed, but they should be justified against the lower market
priority and any currency exposure constraints.
