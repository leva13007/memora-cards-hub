---
id: MC-0008
title: "UI-kit: Create Buttons components"
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

# MC-0008 — UI-kit: Create Buttons components

## Description (required)
Introduce the `Button` atom described in [DE-0008-Buttons](../../design/design/DE-0008-Buttons.md) so product teams can ship consistent call-to-action controls with shared variants, typography, icon alignment, and accessibility guarantees.

Goals:
- Ship three variants (`primary`, `warning`, `secondary`) mapped to the color tokens defined in the spec, including hover, focus-visible, active, and disabled states.
- Support an optional leading icon slot that reuses the Icon atom and automatically syncs size/color to the text label.
- Ensure TextMedium typography, padding, and token-driven spacing apply uniformly across breakpoints.
- Provide Storybook documentation & controls for variant, size, icon, and disabled props, plus guidance for icon-only usage.

## Design References (source of truth)

- Buttons spec: [DE-0008-Buttons](../../design/design/DE-0008-Buttons.md)
- Typography: [DE-0004-Text](../../design/design/DE-0004-Text.md)
- Icons: [DE-0007-Icons](../../design/design/DE-0007-Icons.md)
- Tokens:
	- [design/foundations/tokens.md](../../design/foundations/tokens.md)
	- [design/foundations/theme.md](../../design/foundations/theme.md)

## Acceptance Criteria / Definition of Done (required)
1. Provide a `Button` component that renders a semantic `<button>` by default (with `type` override) and supports the props: `variant`, `disabled`, `icon`, `onClick`, `fullWidth`, `ariaLabel` (for icon-only future use).
2. `variant="primary" | "warning" | "secondary"` applies the background, border, and text/icon colors from DE-0008, including hover/active/focus-visible token transitions; focus-visible outline uses `--color-link` (primary/secondary) or `--color-warning` (warning).
3. `icon` prop renders the Icon atom to the left of the label, keeps spacing defined in the spec (0.5rem), inherits `currentColor`, and scales with typography tokens per breakpoint.
4. Disabled state applies `opacity: 0.7`, blocks pointer/keyboard interaction (`disabled` attribute or `aria-disabled`), and preserves layout/spacing.
5. Component exposes Storybook stories under `UI / Atoms / Button` that document all variants, disabled state, icon usage, and accessibility guidance; stories load with no console errors.
6. README/Storybook docs list required tokens, icon alignment rules, and usage guidelines; API docs explain how to supply `aria-label` for icon-only buttons.

## Test Coverage  
(Manual or auto-generated)

- Related test cases:
	- (TBD) `TC-MC-0055-UI-Button-primary-desktop`
	- (TBD) `TC-MC-0056-UI-Button-warning-accessibility`
	- (TBD) `TC-MC-0057-SM-UI-Button` (Storybook smoke)

## Related  
- Depends on:
	- [MC-0007-UI-kit-Create-Icon-components](./MC-0007-UI-kit-Create-Icon-components.md) (icon assets)
- Blocks:
	- Future feature tickets requiring actionable CTAs
- Duplicate of:
- Additional Links:
	- Storybook docs: `https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-button--docs`
	- Storybook story: `https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-button--default&viewMode=story`

## Sprint
- [Sprint 02](../../sprints/MC-0002-Sprint-02.md)

