---
id: MC-0009
title: "UI-kit: Create TextInput component"
type: Story            # Epic | Feature | Story | Task | Spike | Chore | Improvement
status: ToDo           # ToDo | Sprint ready | In Progress | In Review | Ready for testing | In testing | Issue found | Blocked | Done
priority: Medium       # Low | Medium | High | Critical
area: "ui-kit"
author: "Oleh Levchenko"
assignee: ""
estimated: 5            # story points
created: 2026-01-27
updated: 2026-01-27
started:
ended:
sprint-id: MC-0002-Sprint-02
labels: ["frontend"]
---

# MC-0009 — UI-kit: Create TextInput component

## Description (required)
Introduce the `TextInput` atom so forms within the Memora UI kit have a consistent single-line input with labels, helper/error messaging, accessibility semantics, and disabled treatment defined in [DE-0009-TextInput](../../design/design/DE-0009-TextInput.md).

Key capabilities:
- Primary + Invalid visual states with `TextMedium` typography, tokenized borders, and focus outlines.
- Optional label rendered above the field and error text below (only one visible at a time).
- Disabled behavior reusing opacity 0.7 and blocking interaction while keeping layout intact.
- Placeholder styling at 60% opacity using the same typography stack.
- Storybook documentation covering variants, validation states, and accessibility guidance.

## Design References (source of truth)

- TextInput spec: [DE-0009-TextInput](../../design/design/DE-0009-TextInput.md)
- Typography: [DE-0004-Text](../../design/design/DE-0004-Text.md)
- Tokens & foundations:
	- [design/foundations/tokens.md](../../design/foundations/tokens.md)
	- [design/foundations/breakpoints.md](../../design/foundations/breakpoints.md)
	- [design/foundations/theme.md](../../design/foundations/theme.md)

## Acceptance Criteria / Definition of Done (required)
1. `TextInput` renders a semantic `<input type="text">`
2. Label renders above the input using `TextMedium`, ties to the field via `id`/`for`, and can show a required indicator using `--color-warning`.
3. Invalid state applies `--color-warning` border, sets `aria-invalid="true"`, and shows error text below (using `role="alert"`) while helper text is hidden.
4. Disabled state applies `opacity: 0.7`, blocks pointer/keyboard interaction (native `disabled` or `aria-disabled`), and keeps spacing unchanged.
5. Component supports helper text referenced through `aria-describedby`; only one supporting text block visible at a time.
6. Storybook stories live under `UI / Atoms / TextInput`, include controls for state/disabled/helper/error, and no console errors occur; docs page explains accessibility usage.

## Test Coverage  
(Manual or auto-generated)

- Related test cases:
	- (TBD) `TC-MC-0058-UI-TextInput-primary-desktop`
	- (TBD) `TC-MC-0059-UI-TextInput-invalid-accessibility`
	- (TBD) `TC-MC-0060-SM-UI-TextInput`

## Related  
- Depends on:
	- [MC-0004-UI-kit-Create-H2-component](./MC-0004-UI-kit-Create-H2-component.md) for typography tokens (indirect)
- Blocks:
	- Future forms requiring standardized text entry
- Duplicate of:
- Additional Links:
	- Storybook docs: `https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-textinput--docs`
	- Storybook story: `https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-textinput--default&viewMode=story`

## Sprint
- [Sprint 02](../../sprints/MC-0002-Sprint-02.md)

