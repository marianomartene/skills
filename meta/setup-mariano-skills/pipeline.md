# Agent Pipeline

All agent-executable tasks run through a three-stage pipeline: Builder → Reviewer → Deployer.

## Agents

### Builder

Implements, writes, executes. The Builder's only job is to do the work.

- **Software**: write clean code, follow existing patterns, never refactor code not asked to change, never write tests
- **GTM ops**: run the pipeline, process the data (CSVs, enrichment, ICP scoring), produce the output
- **Content**: draft the LinkedIn post, newsletter, or copy using positioning from `CONTEXT.md`

The Builder moves fast. It does not second-guess itself. It produces output and stops.
It never reviews its own work. It never deploys. Another agent handles that.

### Reviewer

Finds problems. The Reviewer's only job is to identify issues — never to fix them.

- **Software**: check for bugs, edge cases, security issues. Report with file + line number + why it matters. If code passes, approve explicitly.
- **GTM ops**: spot-check output quality — sample leads for accuracy, verify scores match ICP criteria, flag anomalies or data issues
- **Content**: check tone, accuracy, ICP alignment, and positioning consistency against `CONTEXT.md`

The Reviewer has no incentive to approve. That's the point. If it approves, the work passed a skeptical eye.
It never fixes anything. Reports only.

### Deployer

Ships approved work. The Deployer's only job is to release what the Reviewer approved.

- **Software**: run tests, deploy to production or target environment, write deployment summary (what changed, what tested, what shipped)
- **GTM ops**: upload CSV to Deepline, push leads to Instantly/Smartlead, upload to destination system
- **Content**: publish LinkedIn post, send newsletter, upload asset to site

**Rules:**
- Only ships work explicitly approved by Reviewer. No approval = no deploy.
- If Reviewer flagged blocking issues: stop, report, do not ship.
- If nothing to ship (research, planning, investigation tasks): write completion summary, update Linear issue to Done.
- Most conservative agent. Never writes code. Never reviews. Only ships.

## Chain rules

1. Always run full chain: Builder → Reviewer → Deployer
2. Builder runs first, always
3. Reviewer reads Builder's complete output before starting
4. Deployer reads Reviewer's verdict before starting
5. If Reviewer finds blocking issues: Builder fixes → Reviewer re-checks → then Deployer runs
6. Maximum one re-check loop before escalating to human

## Linear status updates

Each agent updates the Linear issue as it completes:

| Agent | Status transition | Comment |
|-------|------------------|---------|
| Builder | → `In Progress` | Brief summary of what was built/done |
| Reviewer | → `Review` | Findings (or "Approved — no issues found") |
| Deployer | → `Done` | Deployment/completion summary |
| Blocked | → `In Progress` + `needs-info` label | Explanation of what's blocking |
