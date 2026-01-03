---
id: MC-0003
title: "UI-kit: Create H1 component"
type: Story            # Epic | Feature | Story | Task | Spike | Chore | Improvement
status: In testing           # ToDo | Sprint ready | In Progress | In Review | Ready for testing | In testing | Issue found | Blocked | Done
priority: Medium       # Low | Medium | High | Critical
area: "ui-kit"  # ui-kit | backend | infra
author: "Oleh Levchenko"
assignee: ""
estimated: 5            # in story points
created: 2025-12-10
updated: 2026-01-03
started:               # YYYY-MM-DD
ended:                 # YYYY-MM-DD
sprint-id: MC-0001-Sprint-01
labels: ["frontend"]             # free-form tags (optional)
---

# MC-0003 — UI-kit: Create H1 component

## Description (required)

As a developer I want an **H1** typography atom in the UI kit that renders a semantic `<h1>` and uses the design system tokens for typography and color, so that page titles and primary headings are consistent across themes and breakpoints.

The **H1** component should:
- Render a semantic `<h1>` element.
- Use token-driven typography (no hard-coded values in the component).
- Adapt to Mobile / Tablet / Desktop breakpoints via `--font-size-h-1`.
- Render correctly in Light / Dark themes via semantic tokens (e.g. `--color-text`).

## Design References (source of truth)

- Theming:
	- [Theming](../../design/foundations/theme.md)
- Breakpoints:
	- [Breakpoints](../../design/foundations/breakpoints.md)
- Tokens:
	- [Typography tokens](../../design/foundations/tokens.md#typography)
	- [Color tokens](../../design/foundations/tokens.md#colours)
- H1 design spec:
	- [DE-0002-H1](../../design/design/DE-0002-H1.md)

## Acceptance Criteria / Definition of Done (required)

1. Renders a semantic `<h1>` root element (no `as` prop; level is fixed).
2. Visual styling matches [design/design/DE-0002-H1.md](../../design/design/DE-0002-H1.md) across Mobile/Tablet/Desktop and Light/Dark themes.
3. Component does not hard-code numeric typography values; values are resolved via tokens.
4. Component does not manage or override theme locally (theme is controlled globally via `data-theme` per `design/foundations/theme.md`).
5. Component is available in Storybook under `UI / Atoms / H1`.

## Test Coverage  
(Manual or auto-generated)

- Related test cases:
	- [TC-MC-0025-UI-H1-Desktop-LightTheme](../../qa_test-cases/UI/H1/TC-MC-0025-UI-H1-Desktop-LightTheme.md)
	- [TC-MC-0026-UI-H1-Desktop-DarkTheme](../../qa_test-cases/UI/H1/TC-MC-0026-UI-H1-Desktop-DarkTheme.md)
	- [TC-MC-0027-UI-H1-Tablet-LightTheme](../../qa_test-cases/UI/H1/TC-MC-0027-UI-H1-Tablet-LightTheme.md)
	- [TC-MC-0028-UI-H1-Tablet-DarkTheme](../../qa_test-cases/UI/H1/TC-MC-0028-UI-H1-Tablet-DarkTheme.md)
	- [TC-MC-0029-UI-H1-Mobile-LightTheme](../../qa_test-cases/UI/H1/TC-MC-0029-UI-H1-Mobile-LightTheme.md)
	- [TC-MC-0030-UI-H1-Mobile-DarkTheme](../../qa_test-cases/UI/H1/TC-MC-0030-UI-H1-Mobile-DarkTheme.md)

## Related

- Depends on:
- Blocks:
- Duplicate of:
- Additional Links:
	- Storybook docs page:
		`https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-h1--docs`
	- Default story (element view):
		`https://leva13007.github.io/memora-cards-storybook/?path=/story/ui-atoms-h1--default`
	- Default story (iframe):
		`https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-h1--default&viewMode=story`

## Sprint

- [Sprint 01](../../sprints/MC-0001-Sprint-01.md)
