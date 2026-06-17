# Triage Labels

Five canonical triage roles. All labels exist in Linear (workspace: Marianomartene / MM).

| Role | Label | Color | Meaning |
|------|-------|-------|---------|
| needs evaluation | `needs-triage` | orange | Not yet decided what to do with this |
| needs more detail | `needs-info` | yellow | Issue too vague to act on — add context first |
| agent can pick up | `ready-for-agent` | green | Fully specified — Blocks/Claude can run with no human context |
| human required | `human-only` | blue | Requires Mariano — call, relationship, or judgment |
| skip | `wontfix` | grey | Will not be actioned |

**Type label** (separate from triage — can combine with any triage label):

| Label | Meaning |
|-------|---------|
| `experiments` | Exploratory work, no production commitment |

## What "ready-for-agent" means

An issue qualifies when ALL of these are true:
- Goal is unambiguous
- Success criteria are clear
- Required context is in the issue description or reachable via `CONTEXT.md`
- No human decision is needed mid-task

If any are missing, apply `needs-info` and describe what's missing in a comment.

## Human-only tasks

Apply `human-only` to: sales calls, LinkedIn outreach execution (sending connection requests, DMs), relationship decisions, anything requiring Mariano's personal presence or judgment that cannot be delegated to an agent.

The `sales` project is predominantly `human-only`.

## Triage flow

New issue → `needs-triage` (default) → evaluate → one of:
- `needs-info` if underspecified
- `ready-for-agent` if fully specced and delegatable
- `human-only` if requires Mariano
- `wontfix` if not actioning
