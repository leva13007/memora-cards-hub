---
id: TR-2025-12-22-06
title: "UI-kit: Container component verification"
type: UI              # Regression | Smoke | UI | E2E | Performance | Custom
scope: "ui-kit"
created: 2025-12-22
owner: "Oleh Levchenko"
environment: "storybook"         # local | dev | staging | production | storybook
status: Planned         # Planned | In Progress | Completed | Canceled
related-tickets:
	- MC-0005
---

# TR-2025-12-22-06 — UI-kit: Container component verification

## Purpose
Validate the `Container` layout component from `MC-0005` in Storybook, ensuring correct width behavior at each breakpoint, correct padding token usage, and correct `fluid` behavior.

---

## Scope

### In Scope
- Container non-fluid behavior (default):
	- Desktop (≥1280px): width 1200px
	- Tablet (768–1279px): width 700px
	- Mobile (<768px): width/max-width 100%
- Container fluid behavior:
	- width 100% at all breakpoints
- Layout token:
	- `padding-left/right: var(--container-padding, 0)` (default token value expected: `--container-padding: 1rem`)
- Breakpoint boundary checks as described in the related TCs

### Out of Scope
- App integration layouts (Storybook-only)
- Cross-browser testing
- Visual regression tooling

---

## Preconditions
- Storybook is available:
	- Docs: https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-container--docs
	- Story: https://leva13007.github.io/memora-cards-storybook/?path=/story/ui-atoms-container--default
- Browser devtools are available to inspect computed layout values (width/max-width/padding).

---

## Test Suite

| ID          | Title                          | Area          | Priority |
|-------------|--------------------------------|---------------|----------|
| TC-MC-0037  | UI: Container — Desktop        | ui-kit/layout | Medium   |
| TC-MC-0038  | UI: Container — Tablet         | ui-kit/layout | Medium   |
| TC-MC-0039  | UI: Container — Mobile         | ui-kit/layout | Medium   |
| TC-MC-0040  | UI: Container — Fluid          | ui-kit/layout | Medium   |

---

## Related Materials
- Ticket: `tickets/MC-0005-UI-kit-Create-Container-component.md`

---

## Notes
- If an issue is found, create a bug ticket and reference `TR-2025-12-22-06`.

---

## Executions
- EX-2025-12-23-01 — Oleh Levchenko — Storybook — Pending (`qa_executions/EX-2025-12-23-01-UI-kit-Container.md`)
