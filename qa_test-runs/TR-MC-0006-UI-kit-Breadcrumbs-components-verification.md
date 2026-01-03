---
id: TR-MC-0006-UI-kit-Breadcrumbs-components-verification
title: "UI-kit: Breadcrumbs component verification"
type: UI              # Regression | Smoke | UI | E2E | Performance | Custom
scope: "ui-kit"
created: 2025-12-22
owner: "Oleh Levchenko"
environment: "storybook"         # local | dev | staging | production | storybook
status: Planned         # Planned | In Progress | Completed | Canceled
related-tickets:
	- MC-0006-UI-kit-Create-Breadcrumbs-component
---

# TR-MC-0006-UI-kit-Breadcrumbs-components-verification — UI-kit: Breadcrumbs component verification

## Purpose
Validate the `Breadcrumbs` molecule from `MC-0006` in Storybook: composition rules (links vs current page), separator behavior (including `TextMedium` usage), wrapping behavior, and required accessibility/semantics.

---

## Scope

### In Scope
- Rendering rules:
	- non-last item with `link` renders as `TextLink`
	- item without `link` renders as `TextMedium`
	- last item is always `TextMedium` and never a link (even if `link` provided)
	- last item has `aria-current="page"`
- Separators:
	- default separator is `/`
	- separators render only between items (N-1)
	- separators are rendered using `TextMedium`
	- separators have `aria-hidden="true"`
- Wrapping:
	- breadcrumbs can wrap onto multiple lines by default
- Semantics / a11y:
	- `nav[aria-label="breadcrumbs"]` with `ol` + `li`
	- keyboard focus goes only through real links (not separators, not current page)

### Out of Scope
- Truncation / single-line behavior (explicitly out of scope in `MC-0006`)
- Cross-browser testing
- Visual regression tooling

---

## Preconditions
- Storybook is available:
	- Docs: https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-molecules-breadcrumbs--docs
	- Story: https://leva13007.github.io/memora-cards-storybook/?path=/story/ui-molecules-breadcrumbs--default
- Browser devtools are available:
	- DOM inspection (to validate link vs non-link, `aria-current`, separators)
	- Accessibility tree inspection (to validate landmark/roles and `aria-hidden`)

---

## Test Suite

| ID          | Title                                             | Area               | Priority |
|-------------|---------------------------------------------------|--------------------|----------|
| TC-MC-0041  | UI: Breadcrumbs — Composition rules (links vs text) | ui-kit/molecules   | Medium   |
| TC-MC-0042  | UI: Breadcrumbs — Separators                      | ui-kit/molecules   | Medium   |
| TC-MC-0043  | UI: Breadcrumbs — Accessibility & semantics       | ui-kit/molecules   | High     |

---

## Related Materials
- Ticket: [MC-0006: UI-kit: Create Breadcrumbs component](../tickets/Story/MC-0006-UI-kit-Create-Breadcrumbs-component.md)

---

## Notes

---

## Executions
- [EX-MC-0006-2025-12-27: First execution of TR-MC-0006](../qa_executions/EX-MC-0006-2025-12-23.md)
