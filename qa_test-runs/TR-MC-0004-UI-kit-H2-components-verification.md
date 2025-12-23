---
id: TR-2025-12-22-05
title: "UI-kit: H2 component verification"
type: UI              # Regression | Smoke | UI | E2E | Performance | Custom
scope: "ui-kit"
created: 2025-12-22
owner: "Oleh Levchenko"
environment: "storybook"         # local | dev | staging | production | storybook
status: Planned         # Planned | In Progress | Completed | Canceled
related-tickets:
	- MC-0004
---

# TR-2025-12-22-05 — UI-kit: H2 component verification

## Purpose
Run a manual UI verification for the `H2` typography atom described in `MC-0004` across breakpoints and themes, ensuring the component uses the correct semantic tag and token-driven styles.

---

## Scope

### In Scope
- `H2` semantics:
	- renders as `<h2>`
- Token-driven typography validation per existing H2 test cases
- Breakpoints:
	- Desktop ≥1280px
	- Tablet 768–1279px
	- Mobile <768px
- Themes:
	- Light
	- Dark

### Out of Scope
- Cross-browser testing
- Heading hierarchy usage rules (usage-level best practices)
- Integration testing in the application (Storybook-only)

---

## Preconditions
- Storybook is available:
	- Docs: https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-h2--docs
	- Story: https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-h2--default&viewMode=story
- Theme switcher is available.
- Browser devtools are available for inspecting computed styles and the rendered tag.

---

## Test Suite

| ID          | Title                                 | Priority |
|-------------|---------------------------------------|----------|
| TC-MC-0031  | UI: H2 — Desktop — Light Theme        | Medium   |
| TC-MC-0032  | UI: H2 — Desktop — Dark Theme         | Medium   |
| TC-MC-0033  | UI: H2 — Tablet — Light Theme         | Medium   |
| TC-MC-0034  | UI: H2 — Tablet — Dark Theme          | Medium   |
| TC-MC-0035  | UI: H2 — Mobile — Light Theme         | Medium   |
| TC-MC-0036  | UI: H2 — Mobile — Dark Theme          | Medium   |

---

## Related Materials
- Ticket: `tickets/MC-0004-UI-kit-Create-H2-component.md`

---

## Notes
- If an issue is found, create a bug ticket and reference `TR-2025-12-22-05`.

---

## Executions
- EX-MC-0005-2025-12-23 — Oleh Levchenko — Storybook — Pending (`qa_executions/EX-MC-0005-2025-12-23.md`)
