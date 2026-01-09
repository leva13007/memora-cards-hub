---
id: MC-0006
title: "UI-kit: Create Breadcrumbs component"
type: Story            # Epic | Feature | Story | Task | Spike | Chore | Improvement
status: Done           # ToDo | Sprint ready | In Progress | In Review | Ready for testing | In testing | Issue found | Blocked | Done
priority: Medium       # Low | Medium | High | Critical
area: "ui-kit"  # ui-kit | backend | infra
author: "Oleh Levchenko"
assignee: ""
estimated: 5            # in story points
created: 2025-12-13
updated: 2025-12-13
started:               # YYYY-MM-DD
ended:                 # YYYY-MM-DD
sprint-id: MC-0001-Sprint-01
labels: ["frontend"]             # free-form tags (optional)
---

# MC-0006 — UI-kit: Create Breadcrumbs component

## Description (required)

Create a `Breadcrumbs` navigation **molecule** so pages can show a clear path to the current location while reusing existing typography atoms. The component should:
- Compose `TextLink` for non-last items with `link` and `TextMedium` for non-linked items and the current page.
- Render semantic navigation markup.
- Always render the last item as the current page (`TextMedium`, `aria-current="page"`, never a link).
- Render separators via `TextMedium`, `aria-hidden="true"`, not focusable, and support multi-line wrapping across breakpoints.

## Design References (source of truth)

- Breadcrumbs spec: [DE-0006-Breadcrumbs](../../design/design/DE-0006-Breadcrumbs.md)
- Typography (Text): [DE-0004-Text](../../design/design/DE-0004-Text.md)
- Links: [DE-0005-Links](../../design/design/DE-0005-Links.md)

## Acceptance Criteria / Definition of Done (required)

1. Renders a `<nav aria-label="breadcrumbs">` containing an `<ol>` with `<li>` items.
2. Accepts `items: Array<{ label: string; link?: string }>` and renders them in order.
3. Non-last items with `link` render as `TextLink`; items without `link` render as `TextMedium`.
4. The last item renders as `TextMedium` with `aria-current="page"` and never as a link, even when `link` is provided.
5. Separators render only between items, default to `'/'`, use `TextMedium`, are not focusable, and include `aria-hidden="true"`.
6. Supports custom string `separator` values without breaking accessibility rules.
7. Component is available in Storybook under `UI / Molecules / Breadcrumbs`.

## Test Coverage  
(Manual or auto-generated)

- Related test cases:
	- [TC-MC-0041-UI-Breadcrumbs-composition-rules](../../qa_test-cases/UI/Breadcrumbs/TC-MC-0041-UI-Breadcrumbs-composition-rules.md)
	- [TC-MC-0042-UI-Breadcrumbs-separators](../../qa_test-cases/UI/Breadcrumbs/TC-MC-0042-UI-Breadcrumbs-separators.md)
	- [TC-MC-0043-UI-Breadcrumbs-accessibility-and-semantics](../../qa_test-cases/UI/Breadcrumbs/TC-MC-0043-UI-Breadcrumbs-accessibility-and-semantics.md)

## Related

- Depends on:
	- [MC-0001 (Text components: TextMedium)](./MC-0001-UI-kit-Create-Text-component.md)
	- [MC-0002 (TextLink)](./MC-0002-UI-kit-Create-TextLink-component.md)
- Blocks:
- Duplicate of:
- Additional Links:
	- Storybook docs page: `https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-molecules-breadcrumbs--docs`
	- Default story (iframe): `https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-molecules-breadcrumbs--default&viewMode=story`

## Sprint

- [Sprint 01](../../sprints/MC-0001-Sprint-01.md)
