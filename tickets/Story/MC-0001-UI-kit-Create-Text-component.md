---
id: MC-0001
title: "UI-kit: Create Text component(Light / Medium / Bold)"
type: Story            # Epic | Feature | Story | Task | Spike | Chore | Improvement
status: In testing           # ToDo | Sprint ready | In Progress | In Review | Ready for testing | In testing | Issue found | Blocked | Done
priority: Medium       # Low | Medium | High | Critical
area: "ui-kit"  # ui-kit | backend | infra
author: "Oleh Levchenko"
assignee: ""
estimated: 8            # in story points
created: 2025-12-08
updated: 2026-01-03
started:               # YYYY-MM-DD
ended:                 # YYYY-MM-DD
sprint-id: MC-0001-Sprint-01
labels: ["frontend"]             # free-form tags (optional)
---

# MC-0001 — UI-kit: Create Text component(Light / Medium / Bold)

## Description (required)

As a developer I want a set of **Text** typography atoms in the UI kit (`TextLight`, `TextMedium`, `TextBold`) that render semantic text elements and use design system tokens for typography and color, so that body text is consistent across themes and breakpoints.

The Text components should:
- Use token-driven typography (no hard-coded values in the components).
- Support responsive font sizing via `--fonts-size-text`.
- Support Light / Dark themes via semantic tokens (e.g. `--color-text`).
- Support a minimal API for semantic rendering (`as`) and semantic color intent (`variant`).

## Design References (source of truth)

- Theming:
	- [Theming](../../design/foundations/theme.md)
- Breakpoints:
	- [Breakpoints](../../design/foundations/breakpoints.md)
- Tokens:
	- [Typography tokens](../../design/foundations/tokens.md#typography)
	- [Color tokens](../../design/foundations/tokens.md#colours)
- Text design spec:
	- [DE-0004-Text](../../design/design/DE-0004-Text.md)

## Acceptance Criteria / Definition of Done (required)

1. Renders semantic text elements (default is `<span>`, can be changed via `as` prop).
2. Default semantic element is `<span>`, and `as` changes only the rendered tag (e.g. `<p>`) without changing typography tokens.
3. Shared typography matches [design/design/DE-0004-Text.md](../../design/design/DE-0004-Text.md) across Mobile/Tablet/Desktop and Light/Dark themes.
4. Variant mapping matches `design/design/DE-0004-Text.md`:
	- `variant="primary"` uses `color: var(--color-text)`
	- `variant="warning"` uses `color: var(--color-warning)`
5. Components do not hard-code numeric typography values; values are resolved via tokens.
6. Components do not manage or override theme locally (theme is controlled globally via `data-theme` per `design/foundations/theme.md`).
7. `TextLight`, `TextMedium`, `TextBold` are implemented and available in Storybook under `UI / Atoms / TextLight`, `UI / Atoms / TextMedium`, `UI / Atoms / TextBold`.

## Test Coverage  
(Manual or auto-generated)

- Related test cases:
  - [TC-MC-0001-UI-TextBold-Desktop-LightTheme](../../qa_test-cases/UI/TextBold/TC-MC-0001-UI-TextBold-Desktop-LightTheme.md)
  - [TC-MC-0002-UI-TextBold-Desktop-DarkTheme](../../qa_test-cases/UI/TextBold/TC-MC-0002-UI-TextBold-Desktop-DarkTheme.md)
  - [TC-MC-0003-UI-TextBold-Tablet-LightTheme](../../qa_test-cases/UI/TextBold/TC-MC-0003-UI-TextBold-Tablet-LightTheme.md)
  - [TC-MC-0004-UI-TextBold-Tablet-DarkTheme](../../qa_test-cases/UI/TextBold/TC-MC-0004-UI-TextBold-Tablet-DarkTheme.md)
  - [TC-MC-0005-UI-TextBold-Mobile-LightTheme](../../qa_test-cases/UI/TextBold/TC-MC-0005-UI-TextBold-Mobile-LightTheme.md)
  - [TC-MC-0006-UI-TextBold-Mobile-DarkTheme](../../qa_test-cases/UI/TextBold/TC-MC-0006-UI-TextBold-Mobile-DarkTheme.md)
  - [TC-MC-0007-UI-TextMedium-Desktop-LightTheme](../../qa_test-cases/UI/TextMedium/TC-MC-0007-UI-TextMedium-Desktop-LightTheme.md)
  - [TC-MC-0008-UI-TextMedium-Desktop-DarkTheme](../../qa_test-cases/UI/TextMedium/TC-MC-0008-UI-TextMedium-Desktop-DarkTheme.md)
  - [TC-MC-0009-UI-TextMedium-Tablet-LightTheme](../../qa_test-cases/UI/TextMedium/TC-MC-0009-UI-TextMedium-Tablet-LightTheme.md)
  - [TC-MC-0010-UI-TextMedium-Tablet-DarkTheme](../../qa_test-cases/UI/TextMedium/TC-MC-0010-UI-TextMedium-Tablet-DarkTheme.md)
  - [TC-MC-0011-UI-TextMedium-Mobile-LightTheme](../../qa_test-cases/UI/TextMedium/TC-MC-0011-UI-TextMedium-Mobile-LightTheme.md)
  - [TC-MC-0012-UI-TextMedium-Mobile-DarkTheme](../../qa_test-cases/UI/TextMedium/TC-MC-0012-UI-TextMedium-Mobile-DarkTheme.md)
  - [TC-MC-0013-UI-TextLight-Desktop-LightTheme](../../qa_test-cases/UI/TextLight/TC-MC-0013-UI-TextLight-Desktop-LightTheme.md)
  - [TC-MC-0014-UI-TextLight-Desktop-DarkTheme](../../qa_test-cases/UI/TextLight/TC-MC-0014-UI-TextLight-Desktop-DarkTheme.md)
  - [TC-MC-0015-UI-TextLight-Tablet-LightTheme](../../qa_test-cases/UI/TextLight/TC-MC-0015-UI-TextLight-Tablet-LightTheme.md)
  - [TC-MC-0016-UI-TextLight-Tablet-DarkTheme](../../qa_test-cases/UI/TextLight/TC-MC-0016-UI-TextLight-Tablet-DarkTheme.md)
  - [TC-MC-0017-UI-TextLight-Mobile-LightTheme](../../qa_test-cases/UI/TextLight/TC-MC-0017-UI-TextLight-Mobile-LightTheme.md)
  - [TC-MC-0018-UI-TextLight-Mobile-DarkTheme](../../qa_test-cases/UI/TextLight/TC-MC-0018-UI-TextLight-Mobile-DarkTheme.md)

## Related

- Depends on:
- Blocks:
- Duplicate of:
- Additional Links:
  - Storybook docs:
    - TextLight: `https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-textlight--docs`
    - TextMedium: `https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-textmedium--docs`
    - TextBold: `https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-textbold--docs`
  - Default stories (iframe):
    - TextLight: `https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-textlight--default&viewMode=story`
    - TextMedium: `https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-textmedium--default&viewMode=story`
    - TextBold: `https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-textbold--default&viewMode=story`

## Sprint

- [Sprint 01](../../sprints/MC-0001-Sprint-01.md)
