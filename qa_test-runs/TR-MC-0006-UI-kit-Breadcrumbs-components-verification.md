---
id: TR-2025-12-22-07
title: "UI-kit: Breadcrumbs component verification"
type: UI              # Regression | Smoke | UI | E2E | Performance | Custom
scope: "ui-kit"
created: 2025-12-22
owner: "Oleh Levchenko"
environment: "storybook"         # local | dev | staging | production | storybook
status: Planned         # Planned | In Progress | Completed | Canceled
related-tickets:
	- MC-0006
---

# TR-2025-12-22-07 — UI-kit: Breadcrumbs component verification

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
- Ticket: `tickets/MC-0006-UI-kit-Create-Breadcrumbs-component.md`
- Test cases:
	- `qa_test-cases/UI/Breadcrumbs/TC-MC-0041-UI-Breadcrumbs-composition-rules.md`
	- `qa_test-cases/UI/Breadcrumbs/TC-MC-0042-UI-Breadcrumbs-separators.md`
	- `qa_test-cases/UI/Breadcrumbs/TC-MC-0043-UI-Breadcrumbs-accessibility-and-semantics.md`

---

## Notes
- This run intentionally avoids re-testing typography token correctness of `TextLink` / `TextMedium` (covered by their own suites).
- If an issue is found, create a bug ticket and reference `TR-2025-12-22-07`.

---

## Executions
- (pending)

