# Issue tracker: Linear

Issues for this workspace live in Linear (team: Marianomartene / MM). Use the Linear MCP tools for all operations — never the `gh` CLI or local markdown files.

## Key operations

- **Read an issue**: `mcp__claude_ai_Linear__get_issue` with identifier (e.g. `MM-106`)
- **List issues**: `mcp__claude_ai_Linear__list_issues` with filters (`state`, `label`, `project`, `assignee: "me"`)
- **Create an issue**: `mcp__claude_ai_Linear__save_issue` with `title`, `description`, `teamId`
- **Update an issue** (status, labels, description): `mcp__claude_ai_Linear__save_issue` with the issue ID
- **Comment**: `mcp__claude_ai_Linear__save_comment` with `issueId` and `body`
- **List labels**: `mcp__claude_ai_Linear__list_issue_labels`
- **List projects**: `mcp__claude_ai_Linear__list_projects`

## Status flow

Backlog → Todo → In Progress → Review → Done

Use `save_issue` with `state` field to transition.

## Projects

| Project | Domain |
|---------|--------|
| `outbound` | Signal pipeline, lead sourcing, radar email |
| `linkedin` | LinkedIn outreach experiments |
| `inbound` | LinkedIn posts, newsletter, lead magnets |
| `sales` | Closing pipeline (human-only work) |
| `website` | marianomartene.com |
| `newsletter` | Newsletter content |

Assign issues to the relevant project when creating.

## When a skill says "publish to the issue tracker"

Create a Linear issue using `save_issue` in the appropriate project.

## When a skill says "fetch the relevant ticket"

Use `get_issue` with the identifier (e.g. `MM-106`).

## When a skill says "apply the ready-for-agent label"

Use `save_issue` with `labels: ["ready-for-agent"]`.

## Multi-client note

This workspace covers Mariano's own business only. Client work lives in separate Linear workspaces — run the setup skill again there.
