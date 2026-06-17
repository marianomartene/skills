# Orchestrator

How to pick up a Linear task and run it through the Builder → Reviewer → Deployer pipeline.

## Trigger

A task is ready when a Linear issue:
- Has the Blocks delegate assigned, OR
- Is labeled `ready-for-agent` and Mariano asks you to pick it up

## Step 1 — Read the issue

```
mcp__claude_ai_Linear__get_issue(issueId)
```

Fetch full content: title, description, labels, project, parent issue, comments.

## Step 2 — Load context

Always load in this order:
1. `CONTEXT.md` at workspace root — GTM identity, ICP, offer, positioning, rules
2. `CLAUDE.md` at project root — software conventions (skip if not a software task)
3. Issue description + comments — task-specific context

If `CONTEXT.md` doesn't exist, proceed but note the gap in your first Linear comment.

## Step 3 — Detect task type

Infer from Linear project + issue content:

| Signal | Task type |
|--------|-----------|
| Project `outbound`, `linkedin` | GTM ops |
| Project `inbound`, `newsletter` | Content |
| Project `website` + code/files in description | Software |
| Project `sales` | Human-only — do not run pipeline |
| Label `human-only` | Human-only — do not run pipeline |
| No project or mixed | Read issue description to determine |

**If `human-only`**: comment on issue — "This issue is marked human-only. Mariano needs to action this directly." Set status to `Todo`. Stop.

**If `needs-info`**: comment listing what's missing. Do not start pipeline until clarified.

## Step 4 — Run pipeline

Spawn subagents in sequence using the Agent tool. Pass each agent:
- The issue content
- The loaded context
- The task type
- Its role-specific system prompt (from `docs/agents/pipeline.md`)

```
Builder  → produces output
Reviewer → reads Builder output, produces verdict
Deployer → reads verdict + Builder output, ships or summarizes
```

## Step 5 — Handle Reviewer blocks

If Reviewer finds blocking issues:
1. Pass findings back to Builder with `fix: true`
2. Builder fixes
3. Reviewer re-checks once
4. If still blocked after one loop: add `needs-info` label, comment with details, ping Mariano

## Step 6 — Final Linear update

Deployer writes final comment and transitions issue to `Done`.
If anything went wrong: set label `needs-info`, leave status at `Review`, explain in comment.

## Agent system prompts

Use these when spawning subagents:

**Builder prompt:**
> You are the Builder. Your only job is to do the work described in the issue. For software tasks: write clean code following existing patterns. For GTM ops: run the pipeline and produce the output. For content: draft using positioning from CONTEXT.md. Do not review your own work. Do not deploy. Move fast.

**Reviewer prompt:**
> You are the Reviewer. Your only job is to find problems in the Builder's output. For software: check for bugs, edge cases, security issues — report with specifics. For GTM ops: spot-check data quality, verify ICP alignment. For content: check accuracy, tone, positioning. Never fix anything. Report only. If the work passes, say "Approved" explicitly.

**Deployer prompt:**
> You are the Deployer. Your only job is to ship work the Reviewer approved. Check for explicit Reviewer approval before doing anything. For software: run tests, deploy, write summary. For GTM ops: upload to destination system. For content: publish. If Reviewer did not approve, stop and report. If nothing to ship, write a completion summary and mark the issue Done in Linear.
