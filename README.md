# Skills

Agent skills for Claude Code — built for GTM engineering, n8n automation, and AI-assisted development.

Install all skills:

```bash
git clone https://github.com/marianomartene/skills ~/.claude/skills
```

Or copy individual folders into `~/.claude/skills/`.

---

## Index

### N8N

| Skill | Description |
|-------|-------------|
| [n8n-code-javascript](n8n/n8n-code-javascript/) | JS Code-node patterns — `$input`, `$json`, `$node`, SplitInBatches, `pairedItem`, production gotchas |
| [n8n-code-python](n8n/n8n-code-python/) | Python Code-node patterns (use JS 95% of the time; Python for stdlib-only tasks) |
| [n8n-expression-syntax](n8n/n8n-expression-syntax/) | Validate `{{ }}` syntax, fix common expression errors, map data between nodes |
| [n8n-mcp-tools-expert](n8n/n8n-mcp-tools-expert/) | Tool selection and parameter formats — consult before any n8n-mcp call |
| [n8n-node-configuration](n8n/n8n-node-configuration/) | Operation-aware config — required fields per operation, `displayOptions`, `patchNodeField` vs full update |
| [n8n-validation-expert](n8n/n8n-validation-expert/) | Interpret validation errors, distinguish false positives, guide auto-fix |
| [n8n-workflow-patterns](n8n/n8n-workflow-patterns/) | Proven architectural patterns: webhook, HTTP API, database, AI, batch, scheduled |
| [workflow-hello-world](n8n/workflow-hello-world/) | Create a cloud workflow on a cron schedule or webhook and validate trigger behavior end to end |

### GTM / Outbound

| Skill | Description |
|-------|-------------|
| [build-tam](gtm/build-tam/) | Build a Total Addressable Market list by sourcing accounts and contacts from Apollo, Crustdata, PDL, and others |
| [clay-to-deepline](gtm/clay-to-deepline/) | Convert a Clay table configuration into local Deepline scripts with parity validation |
| [content-ops](gtm/content-ops/) | Content production operations — drafting, scheduling, and publishing workflows |
| [deepline-analytics](gtm/deepline-analytics/) | Answer GTM metrics, pipeline, revenue, and funnel questions via Deepline's semantic layer |
| [deepline-feedback](gtm/deepline-feedback/) | Send bug reports or product feedback to the Deepline team with session transcript |
| [deepline-gtm](gtm/deepline-gtm/) | Outbound prospecting, enrichment, qualification, waterfall enrichment, scoring, and campaigns via Deepline |
| [deepline-quickstart](gtm/deepline-quickstart/) | Run a quick Deepline demo recipe end to end |
| [find-qualified-titles](gtm/find-qualified-titles/) | Find real role-holders at known company domains from an ICP before running paid people search |
| [niche-signal-discovery](gtm/niche-signal-discovery/) | Discover first-party signals that differentiate Closed Won vs Closed Lost accounts for ICP analysis |
| [portfolio-prospecting](gtm/portfolio-prospecting/) | Find companies backed by a specific investor or accelerator, find contacts, build personalized outbound |

### Dev / Code

| Skill | Description |
|-------|-------------|
| [agent-browser](dev/agent-browser/) | Browser automation CLI for AI agents — navigate, fill forms, screenshot, scrape, test web apps (needs the `agent-browser` CLI). ↗ fork |
| [diagnose](dev/diagnose/) | Disciplined diagnosis loop for hard bugs — reproduce, minimise, hypothesise, instrument, fix, regression-test |
| [frontend-design](dev/frontend-design/) | Create distinctive, production-grade frontend interfaces with high design quality |
| [improve-codebase-architecture](dev/improve-codebase-architecture/) | Architecture review and improvement for existing codebases |
| [prototype](dev/prototype/) | Rapidly prototype logic and features with minimal scaffolding |
| [web-design-guidelines](dev/web-design-guidelines/) | Review UI code against the live Web Interface Guidelines (accessibility, UX, best practices). ↗ fork |

### Planning / Writing

| Skill | Description |
|-------|-------------|
| [brainstorming](planning/brainstorming/) | Turn ideas into designs/specs through collaborative dialogue before any implementation; optional browser visual companion. ↗ fork |
| [grill-me](planning/grill-me/) | Relentless interview to stress-test a plan or design — resolves every branch of the decision tree |
| [grill-with-docs](planning/grill-with-docs/) | Same as grill-me but grounded in attached documentation or specs |
| [handoff](planning/handoff/) | Compact the current conversation into a handoff document for another agent to pick up |
| [humanizer](planning/humanizer/) | Remove signs of AI-generated writing from text |
| [to-issues](planning/to-issues/) | Break a plan or PRD into independently-grabbable Linear issues using tracer-bullet vertical slices |
| [to-prd](planning/to-prd/) | Turn conversation context into a PRD and publish it to the issue tracker |

### Meta

| Skill | Description |
|-------|-------------|
| [linkedin-url-lookup](meta/linkedin-url-lookup/) | Resolve LinkedIn profile URLs from name + company with strict identity validation |
| [setup-mariano-skills](meta/setup-mariano-skills/) | Bootstrap this skill set into a new Claude Code environment |
| [write-a-skill](meta/write-a-skill/) | Create new agent skills with proper structure, progressive disclosure, and bundled resources |

---

## Usage

Skills activate automatically when you invoke them by name in Claude Code:

```
/build-tam
/deepline-gtm
/diagnose
```

Or reference them naturally in your prompt — Claude Code routes to the matching skill.

---

## Forked skills

Skills marked **↗ fork** are vendored from upstream open-source repos, kept faithful to the original. Each carries its own `LICENSE` and an `ATTRIBUTION.md` with source and author.

| Skill | Upstream | Author | License |
|-------|----------|--------|---------|
| agent-browser | [vercel-labs/agent-browser](https://github.com/vercel-labs/agent-browser) | Vercel | Apache-2.0 |
| web-design-guidelines | [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills) | Vercel | MIT |
| brainstorming | [obra/superpowers](https://github.com/obra/superpowers) | Jesse Vincent | MIT |

---

Built for [Claude Code](https://claude.ai/code) · by [Mariano Martene](https://marianomartene.com)
