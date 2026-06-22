# Attribution

This skill is a fork of an upstream open-source skill, vendored into
[marianomartene/skills](https://github.com/marianomartene/skills).

- **Upstream:** [obra/superpowers](https://github.com/obra/superpowers) — `skills/brainstorming`
- **Author:** Jesse Vincent
- **License:** MIT (see `LICENSE`)

## Notes

- **Local modification:** the upstream `description` ("You MUST use this before
  any creative work…") was narrowed to trigger on explicit brainstorm/design
  intent only, so it no longer auto-fires on every edit or bug fix. This is the
  only change from upstream; the skill body is unchanged.
- The terminal step invokes the [[writing-plans]] skill, which **is** installed
  alongside this one (`planning/writing-plans`), so the design → plan chain is
  complete.
- The optional Visual Companion (`scripts/`, `visual-companion.md`) starts a
  local browser server for mockups/diagrams; it is offered just-in-time, never
  upfront.
