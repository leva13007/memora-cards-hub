---
id: TR-2025-12-22-04
title: "UI-kit: H1 component verification"
type: UI              # Regression | Smoke | UI | E2E | Performance | Custom
scope: "ui-kit"
created: 2025-12-22
owner: "Oleh Levchenko"
environment: "storybook"         # local | dev | staging | production | storybook
status: Planned         # Planned | In Progress | Completed | Canceled
related-tickets:
	- MC-0003
---

# TR-2025-12-22-04 — UI-kit: H1 component verification

## Purpose
Run a manual UI verification for the `H1` typography atom described in `MC-0003` across breakpoints and themes, ensuring the component uses the correct semantic tag and token-driven styles.

---

## Scope

### In Scope
- `H1` semantics:
	- renders as `<h1>`
- Token-driven typography validation per existing H1 test cases
- Breakpoints:
	- Desktop ≥1280px
	- Tablet 768–1279px
	- Mobile <768px
- Themes:
	- Light
	- Dark

### Out of Scope
- Cross-browser testing
- Page-level usage rules ("only one H1 per page")
- Integration testing in the application (Storybook-only)

---

## Preconditions
- Storybook is available:
	- Docs: https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-h1--docs
	- Story: https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-h1--default&viewMode=story
- Theme switcher is available.
- Browser devtools are available for inspecting computed styles and the rendered tag.

---

## Test Suite

| ID          | Title                                 | Priority |
|-------------|---------------------------------------|----------|
| TC-MC-0025  | UI: H1 — Desktop — Light Theme        | Medium   |
| TC-MC-0026  | UI: H1 — Desktop — Dark Theme         | Medium   |
| TC-MC-0027  | UI: H1 — Tablet — Light Theme         | Medium   |
| TC-MC-0028  | UI: H1 — Tablet — Dark Theme          | Medium   |
| TC-MC-0029  | UI: H1 — Mobile — Light Theme         | Medium   |
| TC-MC-0030  | UI: H1 — Mobile — Dark Theme          | Medium   |

---

## Related Materials
- Ticket: `tickets/MC-0003-UI-kit-Create-H1-component.md`

---

## Notes
- If an issue is found, create a bug ticket and reference `TR-2025-12-22-04`.

---

## Executions
- (pending)
