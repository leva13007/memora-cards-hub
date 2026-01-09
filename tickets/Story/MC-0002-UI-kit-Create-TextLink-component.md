---
id: MC-0002
title: "UI-kit: Create TextLink component"
type: Story            # Epic | Feature | Story | Task | Spike | Chore | Improvement
status: Done           # ToDo | Sprint ready | In Progress | In Review | Ready for testing | In testing | Issue found | Blocked | Done
priority: Medium       # Low | Medium | High | Critical
area: "ui-kit"  # ui-kit | backend | infra
author: "Oleh Levchenko"
assignee: ""
estimated: 5            # in story points
created: 2025-12-11
updated: 2026-01-03
started:               # YYYY-MM-DD
ended:                 # YYYY-MM-DD
sprint-id: MC-0001-Sprint-01
labels: ["frontend"]             # free-form tags (optional)
---

# MC-0002 — UI-kit: Create TextLink component

## Description (required)

As a developer I want a **TextLink** component in the UI kit that renders a semantic link (`<a href="…">`) while using the same typography baseline as `TextMedium`, so in-content navigation is consistent, accessible, and theme-aware.

The **TextLink** component should:
- Match `TextMedium` typography rules.
- Use semantic link color tokens for default/hover states.
- Provide a clear focus-visible status indicator.

## Design References (source of truth)

- Theming:
	- [Theming](../../design/foundations/theme.md)
- Breakpoints:
	- [Breakpoints](../../design/foundations/breakpoints.md)
- Tokens:
	- [Typography tokens](../../design/foundations/tokens.md#typography)
	- [Color tokens](../../design/foundations/tokens.md#colours)
- Shared text typography spec:
	- [DE-0004-Text](../../design/design/DE-0004-Text.md)
- Links design spec:
	- [DE-0005-Links](../../design/design/DE-0005-Links.md)

## Acceptance Criteria / Definition of Done (required)

1. Renders a semantic `<a>` element and maps the destination prop to `href`.
2. Typography matches `TextMedium` baseline per `design/design/DE-0004-Text.md`.
3. Link interaction styles match `design/design/DE-0005-Links.md` (default/hover color tokens, cursor, text-decoration rules).
4. Implements keyboard focus styling.
5. Component does not hard-code numeric token values; values are resolved via tokens from `design/foundations/tokens.md`.
6. Component does not manage or override theme locally (theme is controlled globally via `data-theme` per `design/foundations/theme.md`).
7. Storybook stories do not navigate away from Storybook UI when clicking the link (use a safe `href` in stories).
8. Component is available in Storybook under `UI / Atoms / TextLink`.

## Test Coverage  
(Manual or auto-generated)

- Related test cases:
  - [TC-MC-0019-UI-TextLink-Desktop-LightTheme](../../qa_test-cases/UI/TextLink/TC-MC-0019-UI-TextLink-Desktop-LightTheme.md)
  - [TC-MC-0020-UI-TextLink-Desktop-DarkTheme](../../qa_test-cases/UI/TextLink/TC-MC-0020-UI-TextLink-Desktop-DarkTheme.md)
  - [TC-MC-0021-UI-TextLink-Tablet-LightTheme](../../qa_test-cases/UI/TextLink/TC-MC-0021-UI-TextLink-Tablet-LightTheme.md)
  - [TC-MC-0022-UI-TextLink-Tablet-DarkTheme](../../qa_test-cases/UI/TextLink/TC-MC-0022-UI-TextLink-Tablet-DarkTheme.md)
  - [TC-MC-0023-UI-TextLink-Mobile-LightTheme](../../qa_test-cases/UI/TextLink/TC-MC-0023-UI-TextLink-Mobile-LightTheme.md)
  - [TC-MC-0024-UI-TextLink-Mobile-DarkTheme](../../qa_test-cases/UI/TextLink/TC-MC-0024-UI-TextLink-Mobile-DarkTheme.md)
  - [TC-MC-0044-UI-TextLink-accessibility](../../qa_test-cases/UI/TextLink/TC-MC-0044-UI-TextLink-accessibility.md)

## Related  

- Depends on: 
  - [MC-0001 — UI-kit: Create Text component](./MC-0001-UI-kit-Create-Text-component.md)
- Blocks:
- Duplicate of:
- Additional Links:
  - Storybook docs page: `https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-textlink--docs`
	- Default story (iframe): `https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-textlink--default&viewMode=story`

## Sprint

- [Sprint 01](../../sprints/MC-0001-Sprint-01.md)
