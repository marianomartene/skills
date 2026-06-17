# Setup Mariano's Skills

Scaffold the per-project configuration that the engineering and GTM skills assume.

Most decisions are already locked for this workspace (Linear, 5 triage labels, single-context GTM).
This skill only asks what it cannot infer.

## Process

### 1. Explore

Read whatever exists — don't assume:

- `CONTEXT.md` at the repo/workspace root — does it exist?
- `CLAUDE.md` at the root — exists? Has `## Agent skills` section already?
- `docs/agents/` — does prior skill output exist?
- Project structure — is this a software project, GTM ops workspace, or mixed?

### 2. Ask

Two questions only, one at a time:

**Question A — Project type.**

> What kind of work lives in this project?
>
> - **Software** — code, tools, apps (Builder writes code; Deployer ships to production or a URL)
> - **GTM / Content** — outbound, inbound, content ops (Builder executes pipelines or drafts; Deployer uploads or publishes)
> - **Mixed** — both happen here

**Question B — CONTEXT.md.**

If `CONTEXT.md` does NOT exist at root:
> "No `CONTEXT.md` found. This file gives agents ICP, offer, and positioning so they make good decisions. Create it before running agent tasks. Want me to scaffold a template?"

If it exists, confirm it covers: ICP definition, offer structure, active pipeline, positioning rules.

### 3. Confirm and edit

Show the user a draft of:
- The `## Agent skills` block for `CLAUDE.md`
- Each `docs/agents/` file contents

Let them edit before writing.

### 4. Write

**Pick the file to edit:**
- If `CLAUDE.md` exists, edit it.
- If it doesn't exist, create it.

Never create `AGENTS.md` — always use `CLAUDE.md`.

If `## Agent skills` block already exists, update in-place. Don't overwrite surrounding content.

The block:

```markdown
## Agent skills

### Issue tracker

Issues live in Linear (workspace: Marianomartene / MM). See `docs/agents/issue-tracker.md`.

### Triage labels

Five canonical triage labels + `experiments` type label. See `docs/agents/triage-labels.md`.

### Domain docs

Single-context: `CONTEXT.md` at repo root (GTM identity, ICP, offer). See `docs/agents/domain.md`.

### Agent pipeline

Builder → Reviewer → Deployer. Always full chain. See `docs/agents/pipeline.md`.

### Orchestrator

How to load context, detect task type, and route to pipeline. See `docs/agents/orchestrator.md`.
```

Then write five docs files using the seed templates in this skill folder:

- [issue-tracker-linear.md](./issue-tracker-linear.md) — Linear MCP conventions
- [triage-labels.md](./triage-labels.md) — label mapping
- [domain.md](./domain.md) — domain doc consumer rules
- [pipeline.md](./pipeline.md) — Builder/Reviewer/Deployer definitions
- [orchestrator.md](./orchestrator.md) — orchestration flow

### 5. Done

Tell the user setup is complete and which skills now read from these files.
Mention:
- Edit `docs/agents/*.md` directly at any time — re-run this skill only to switch issue trackers or restart from scratch.
- For new clients: set up a separate Linear workspace and re-run this skill there.
