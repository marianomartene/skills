# Attribution

This skill is a fork of an upstream open-source skill, vendored into
[marianomartene/skills](https://github.com/marianomartene/skills).

- **Upstream:** [obra/superpowers](https://github.com/obra/superpowers) — `skills/brainstorming`
- **Author:** Jesse Vincent
- **License:** MIT (see `LICENSE`)

## Notes

- The skill's terminal step invokes a `writing-plans` skill, which is **not**
  part of this collection. Brainstorming still runs through design + approval;
  the final "create the implementation plan" handoff has no target here unless
  you also install `writing-plans` from upstream.
- The optional Visual Companion (`scripts/`, `visual-companion.md`) starts a
  local browser server for mockups/diagrams; it is offered just-in-time, never
  upfront.
- The `description` is intentionally aggressive ("You MUST use this before any
  creative work"), so it may auto-trigger ahead of implementation work. Kept
  faithful to upstream — narrow it if it fires too eagerly.
