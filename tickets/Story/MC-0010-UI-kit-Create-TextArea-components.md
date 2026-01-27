---
id: MC-0010
title: "UI-kit: Create TextArea component"
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

# MC-0010 — UI-kit: Create TextArea component

## Description (required)
Implement the multi-line `TextArea` atom that extends the TextInput visual system to longer text entry, following [DE-0010-TextArea](../../design/design/DE-0010-TextArea.md). The component should honor the 3-row default height, disabled/invalid states, label + error messaging, and accessibility contracts.

Goals:
- Provide a `<textarea>` wrapper that shares typography, padding, and tokens with TextInput but disallows browser resizing (`resize: none`).
- Support optional label above and error text below, ensuring only one supporting text block appears at a time.
- Expose props for `rows`, `minRows`, `maxRows` (optional), `state`, `disabled`, `fullWidth`, and `ariaLabel` for no-label scenarios.
- Document usage and states in Storybook.

## Design References (source of truth)

- TextArea spec: [DE-0010-TextArea](../../design/design/DE-0010-TextArea.md)
- TextInput base reference: [DE-0009-TextInput](../../design/design/DE-0009-TextInput.md)
- Typography: [DE-0004-Text](../../design/design/DE-0004-Text.md)
- Tokens & foundations:
	- [design/foundations/tokens.md](../../design/foundations/tokens.md)
	- [design/foundations/breakpoints.md](../../design/foundations/breakpoints.md)
	- [design/foundations/theme.md](../../design/foundations/theme.md)

## Acceptance Criteria / Definition of Done (required)
1. `TextArea` renders a semantic `<textarea>` with default `rows=3`, and disables drag resizing.
2. Invalid state applies `--color-warning` border/background per DE-0010, sets `aria-invalid="true"`, and shows error text below using `role="alert"`;
3. Disabled state applies `opacity: 0.7`, uses native `disabled` attribute (or `aria-disabled` fallback), blocks pointer events, and keeps layout unchanged.
4. Component maintains TextInput-aligned padding, typographic tokens, and focus outlines (`2px` high-contrast ring) across breakpoints.
5. Storybook docs at `UI / Atoms / TextArea` showcase states, rows adjustments, disabled/invalid demos, and accessibility guidance with no console errors.

## Test Coverage  
(Manual or auto-generated)

- Related test cases:
	- (TBD) `TC-MC-0061-UI-TextArea-primary-desktop`
	- (TBD) `TC-MC-0062-UI-TextArea-invalid-accessibility`
	- (TBD) `TC-MC-0063-SM-UI-TextArea`

## Related  
- Depends on:
	- [MC-0009-UI-kit-Create-TextInput-component](./MC-0009-UI-kit-Create-TextInput-components.md) for shared tokens & patterns
- Blocks:
	- Future feature forms requiring multi-line inputs
- Duplicate of:
- Additional Links:
	- Storybook docs: `https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-textarea--docs`
	- Storybook story: `https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-textarea--default&viewMode=story`

## Sprint
- [Sprint 02](../../sprints/MC-0002-Sprint-02.md)
