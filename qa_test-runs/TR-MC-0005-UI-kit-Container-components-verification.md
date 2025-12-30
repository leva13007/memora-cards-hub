---
id: TR-MC-0005-UI-kit-Container-components-verification
title: "UI-kit: Container component verification"
type: UI              # Regression | Smoke | UI | E2E | Performance | Custom
scope: "ui-kit"
created: 2025-12-22
owner: "Oleh Levchenko"
environment: "storybook"         # local | dev | staging | production | storybook
status: Planned         # Planned | In Progress | Completed | Canceled
related-tickets:
	- MC-0005-UI-kit-Create-Container-component
---

# TR-MC-0005-UI-kit-Container-components-verification — UI-kit: Container component verification

## Purpose
Validate the `Container` layout component from [MC-0005: UI-kit: Create Container component](../tickets/MC-0005-UI-kit-Create-Container-component.md) in Storybook, ensuring correct width behavior at each breakpoint, correct padding token usage, and correct `fluid` behavior.

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
| [TC-MC-0037](../qa_test-cases/UI/Container/TC-MC-0037-UI-Container-Desktop.md)  | UI: Container — Desktop        | ui-kit/layout | Medium   |
| [TC-MC-0038](../qa_test-cases/UI/Container/TC-MC-0038-UI-Container-Tablet.md)  | UI: Container — Tablet         | ui-kit/layout | Medium   |
| [TC-MC-0039](../qa_test-cases/UI/Container/TC-MC-0039-UI-Container-Mobile.md)  | UI: Container — Mobile         | ui-kit/layout | Medium   |
| [TC-MC-0040](../qa_test-cases/UI/Container/TC-MC-0040-UI-Container-Fluid.md)  | UI: Container — Fluid          | ui-kit/layout | Medium   |

---

## Related Materials
- Ticket: [MC-0005: UI-kit: Create Container component](../tickets/MC-0005-UI-kit-Create-Container-component.md)

---

## Notes

---

## Executions
- [EX-MC-0005-2025-12-27: First execution of TR-MC-0005](../qa_executions/EX-MC-0005-2025-12-23.md)