# Domain Docs

How the skills should consume context before working on any task.

## Before starting any task, read these

1. **`CONTEXT.md`** at the repo/workspace root — Mariano's GTM identity, ICP definition, offer structure, active pipeline, positioning rules, signal stack, and any agent-specific constraints. Always read this first.
2. **`CLAUDE.md`** at the project root — codebase conventions, architecture, dev setup. Read for any software or tooling task.

If either file doesn't exist, proceed silently. Don't flag absence or suggest creating them upfront.

## What CONTEXT.md covers (for this workspace)

- **ICP**: who the ideal customer is (role, company stage, signals)
- **Offer**: GTM Sprint, Audit, retainer structure, pricing
- **Pipeline**: active prospects, deal status, next actions
- **Positioning**: messaging rules, what to say, what to avoid
- **Signal stack**: hiring signals, funding signals, ranked priority
- **Agent rules**: any constraints on how agents should behave

## Use the vocabulary

When naming things (issue titles, output files, copy, variable names), use terms as defined in `CONTEXT.md`. Don't drift to synonyms.

If a concept isn't in `CONTEXT.md`, that's a signal — either you're inventing language the workspace doesn't use (reconsider) or there's a real gap worth noting.

## For software tasks

Also read:
- `README.md` — project purpose and setup
- `CLAUDE.md` — conventions and patterns to follow
- Relevant source files before writing code

## Multi-client note

This workspace is single-context (Mariano's own business). When working in a client's Linear workspace, that workspace's own `CONTEXT.md` takes precedence — it will contain client-specific ICP, offer, and rules.

## No ADRs required

This workspace doesn't use Architecture Decision Records. Architectural decisions live in `CONTEXT.md` or `CLAUDE.md` directly.
