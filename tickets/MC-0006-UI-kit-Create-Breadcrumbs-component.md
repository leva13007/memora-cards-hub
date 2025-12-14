---
id: MC-0006
title: "UI-kit: Create Breadcrumbs component"
type: Story            # Epic | Feature | Story | Task | Spike | Chore | Improvement
status: Open           # ToDo | Sprint ready | In Progress | In Review | Ready for testing | In testing | Issue found | Blocked | Done
priority: Medium       # Low | Medium | High | Critical
area: "ui-kit/molecules"               # ui-kit/typography | ui-kit/molecules | ui-kit/atoms | ui-kit/buttons | app/editor | backend | infra
author: "Oleh Levchenko"
assignee: ""
created: 2025-12-13
updated: 2025-12-13
---

# MC-0006 — UI-kit: Create Breadcrumbs component

## Description
As a developer I want to have a Breadcrumbs component in the UI kit so that I can show a clear navigation path and improve orientation in the app.

Breadcrumbs is a **Molecule** component composed of existing typography atoms:
- `TextLink` for items that have a link (except the last item)
- `TextMedium` for items without a link and for the last/current item

Storybook location:
- `UI / Molecules / Breadcrumbs`

---

## Requirements / Specifications

### Component API

#### `items` (required)
- Type:
	- `Array<{ label: string; link?: string }>`
- Behavior:
	- Render items in the same order as provided.
	- If `link` is provided:
		- Render item as `TextLink` **unless** it is the last item.
	- If `link` is not provided:
		- Render as `TextMedium`.
	- The **last item must always be rendered as `TextMedium`** and **must not be a link**, even if `link` is provided in data.

#### `separator` (optional)
- Type: `string`
- Default: `'/'`
- Behavior:
	- Render the separator between items.
	- Separator visual must be rendered using `TextMedium` (so it follows typography tokens consistently).
		- When a string is provided (default `'/'`), it must be passed as the `TextMedium` content.
	- Separator must not be focusable/clickable.
	- Separator must be ignored by screen readers (see Accessibility).

#### Wrapping behavior
- Breadcrumbs must support **wrapping onto multiple lines** by default (recommended CSS: `white-space: normal; flex-wrap: wrap;`).
- Truncation / single-line behavior is **out of scope** for this ticket.

#### `dataTestId` (optional)
- Type: `string`
- Purpose: deterministic selectors for QA/automation.

### Markup and accessibility
- The component must render a semantic navigation region:
	- Root element: `<nav aria-label="breadcrumbs">`.
	- Inside: ordered list `<ol>`.
	- Each breadcrumb item: `<li>`.
- The last item must have:
	- `aria-current="page"`.
- Separators must include:
	- `aria-hidden="true"`.

### Test IDs
If `dataTestId` is provided:
- Root `nav`: `data-testid={dataTestId}`
- Item wrapper `li`: `data-testid={`${dataTestId}-item-${index}`}`
- Separator: `data-testid={`${dataTestId}-separator-${index}`}` (between item `index` and `index + 1`)

### Responsive behavior (breakpoints)
Breadcrumbs must behave consistently across the product breakpoints:
- Desktop: viewport width **≥1280px**
- Tablet: viewport width **768–1279px**
- Mobile: viewport width **<768px**

No breakpoint-specific styling is required by this ticket unless discovered during implementation, but **wrapping layout** must be validated at all breakpoints.

---

## Implementation Notes (non-blocking)
- Use existing `TextLink` and `TextMedium` tokens/styles. Breadcrumbs shouldn’t redefine typography tokens.
- Ensure separators don’t break selection and don’t receive focus.

---

## Acceptance Criteria
1. Breadcrumbs renders inside a `<nav aria-label="breadcrumbs">` element.
2. Breadcrumbs uses an `<ol>` with `<li>` for each item.
3. For each item where `link` is specified and the item is **not** the last item:
	 - The item is rendered using `TextLink`.
4. For each item where `link` is **not** specified:
	 - The item is rendered using `TextMedium`.
5. The last item is always rendered using `TextMedium` and never as a `TextLink`, even if `link` is provided.
6. The last item has `aria-current="page"`.
7. The default separator is `/` and is rendered between all items (except after the last item).
8. Separators are rendered using `TextMedium` and have `aria-hidden="true"`.

9. Breadcrumbs content can wrap onto multiple lines.
10. If `dataTestId` is provided, the component renders test ids for root, items, and separators as specified in this ticket.
11. The component behavior is verified at breakpoints:
		- Desktop (≥1280px)
		- Tablet (768–1279px)
		- Mobile (<768px)

All criteria must be objectively verifiable.

---

## Test Coverage
(Manual or auto-generated)

Suggested manual QA scenarios:
- Items rendering:
	- 1 item only (single current page)
	- multiple items with mixture of linked and non-linked items
	- last item provided with `link` should still be non-link
- Separator rendering:
	- default `/`
	- custom separator (string and ReactNode)
- Wrapping:
	- very long labels (verify wrapping)
- Accessibility:
	- correct `nav` label and `aria-current` value
	- separators ignored by screen readers
- Responsive validation (layout correctness):
	- Desktop ≥1280px, Tablet 768–1279px, Mobile <768px

---

## Edge Cases
- `items` is an empty array:
	- Decide expected implementation behavior (recommended): render nothing or render empty `<nav>` without errors.
- Very long breadcrumb labels:
	- should not overflow container and should wrap.
- Custom separator as ReactNode (e.g., icon):
	- must remain `aria-hidden`.
- Clickability:
	- only linked items should be interactive; separators and current page must not be.

---

## Related
- Storybook docs: https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-molecules-breadcrumbs--docs
- Storybook story: https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-molecules-breadcrumbs--default&viewMode=story
- Depends on:
	- [MC-0001 (Text components: TextMedium)](./MC-0001-UI-kit-Create-Text-component.md)
	- [MC-0002 (TextLink)](./MC-0002-UI-kit-Create-TextLink-component.md)

