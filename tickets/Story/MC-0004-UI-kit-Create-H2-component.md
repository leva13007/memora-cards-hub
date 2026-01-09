---
id: MC-0004
title: "UI-kit: Create H2 component"
type: Story            # Epic | Feature | Story | Task | Spike | Chore | Improvement
status: Done           # ToDo | Sprint ready | In Progress | In Review | Ready for testing | In testing | Issue found | Blocked | Done
priority: Medium       # Low | Medium | High | Critical
area: "ui-kit"  # ui-kit | backend | infra
author: "Oleh Levchenko"
assignee: ""
estimated:             # in story points
created: 2025-12-11
updated: 2026-01-03
started:               # YYYY-MM-DD
ended:                 # YYYY-MM-DD
sprint-id: MC-0001-Sprint-01
labels: ["frontend"]             # free-form tags (optional)
---

# MC-0004 — UI-kit: Create H2 component

## Description (required)

As a developer I want an **H2** typography atom in the UI kit that renders a semantic `<h2>` and uses the design system tokens for typography and color, so that section titles and secondary headings are consistent across themes and breakpoints.

The **H2** component should:
- Render a semantic `<h2>` element.
- Use token-driven typography (no hard-coded values in the component).
- Adapt to Mobile / Tablet / Desktop breakpoints via `--font-size-h-2`.
- Render correctly in Light / Dark themes via semantic tokens (e.g. `--color-text`).

## Design References (source of truth)

- Theming:
	- [Theming](../../design/foundations/theme.md)
- Breakpoints:
	- [Breakpoints](../../design/foundations/breakpoints.md)
- Tokens:
	- [Typography tokens](../../design/foundations/tokens.md#typography)
	- [Color tokens](../../design/foundations/tokens.md#colours)
- H2 design spec:
	- [DE-0003-H2](../../design/design/DE-0003-H2.md)

## Acceptance Criteria / Definition of Done (required)

1. Renders a semantic `<h2>` root element (no `as` prop; level is fixed).
2. Visual styling matches [design/design/DE-0003-H2.md](../../design/design/DE-0003-H2.md) across Mobile/Tablet/Desktop and Light/Dark themes.
3. Component does not hard-code numeric typography values; values are resolved via tokens.
4. Component does not manage or override theme locally (theme is controlled globally via `data-theme` per `design/foundations/theme.md`).
5. Component is available in Storybook under `UI / Atoms / H2`.

## Test Coverage  
(Manual or auto-generated)

- Related test cases:
	- [TC-MC-0031-UI-H2-Desktop-LightTheme](../../qa_test-cases/UI/H2/TC-MC-0031-UI-H2-Desktop-LightTheme.md)
	- [TC-MC-0032-UI-H2-Desktop-DarkTheme](../../qa_test-cases/UI/H2/TC-MC-0032-UI-H2-Desktop-DarkTheme.md)
	- [TC-MC-0033-UI-H2-Tablet-LightTheme](../../qa_test-cases/UI/H2/TC-MC-0033-UI-H2-Tablet-LightTheme.md)
	- [TC-MC-0034-UI-H2-Tablet-DarkTheme](../../qa_test-cases/UI/H2/TC-MC-0034-UI-H2-Tablet-DarkTheme.md)
	- [TC-MC-0035-UI-H2-Mobile-LightTheme](../../qa_test-cases/UI/H2/TC-MC-0035-UI-H2-Mobile-LightTheme.md)
	- [TC-MC-0036-UI-H2-Mobile-DarkTheme](../../qa_test-cases/UI/H2/TC-MC-0036-UI-H2-Mobile-DarkTheme.md)

## Related

- Depends on:
- Blocks:
- Duplicate of:
- Additional Links:
	- Storybook docs page:
		`https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-h2--docs`
	- Default story (element view):
		`https://leva13007.github.io/memora-cards-storybook/?path=/story/ui-atoms-h2--default`
	- Default story (iframe):
		`https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-h2--default&viewMode=story`

## Sprint

- [Sprint 01](../../sprints/MC-0001-Sprint-01.md)
