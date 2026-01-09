# Container — Design Reference

## 1. Purpose
Defines a horizontal layout primitive used to constrain and center page content.

## 2. Scope
Applies to the Container component only.
Does not define typography, vertical spacing, or grid behavior.

## 3. Terminology
- Breakpoint: Mobile / Tablet / Desktop (see `design/foundations/breakpoints.md`)
- Fluid container: full-width layout mode

## 4. Design Dependencies
- Breakpoints: [design/foundations/breakpoints.md](../foundations/breakpoints.md)
- Tokens: [design/foundations/tokens.md#container](../foundations/tokens.md#container)

## 5. Conceptual Model
Container is a layout primitive that constrains and centers page content horizontally.

## 6. Behavioral Rules
### 6.1 Width behavior by breakpoint (non-fluid mode)
| Mobile     | Tablet    | Desktop   |
|------------|-----------|-----------|
| Full-width | 720px     | 1200px    |

### 6.2 Fluid mode override
When the Container is rendered with `fluid = true`:

- The container is **full-width at all breakpoints**.
- All fixed-width constraints are ignored.
- Horizontal padding rules still apply.

Fluid mode overrides all breakpoint-specific width behavior.

### 6.3 Horizontal centering & padding
- Container content is horizontally centered using automatic left/right margins.
- Horizontal padding is applied using the `--container-padding` token at all breakpoints.

## 7. States & Variants
- `fluid = true | false`

## 8. Layout & Responsiveness
Container must behave consistently across the product breakpoints

## 9. Tokens & Variables
### Required tokens
- `--container-padding`

## 10. Accessibility
N/A (pure layout component)

## 11. Rules & Constraints
- Tickets must not define pixel values
- Container must not apply typography styles
- Mobile breakpoint is always fluid

## 12. Non-normative Implementation Notes
- Default (non-fluid)
  - Centered: `margin-left/right: auto`
  - Padding: `padding-left/right: var(--container-padding, 0)`
  - Width behavior by breakpoint:
    - Desktop/Tablet: fixed width using `--container-width`
    - Mobile: full width (fluid)
- Fluid
  - Always full width
  - Must not be constrained by the breakpoint width token

### Component API (non-normative)
- `children` (required)
	- Type: `ReactNode`
- `fluid` (optional)
	- Type: `boolean`
	- Default: `false`
	- Behavior:
		- `false` (default): width follows the design spec (via `--container-width`) per breakpoint
		- `true`: always full-width.

## 13. Edge Cases
- N/A

## 14. Change Impact
- Requires re-running container-related test runs
- May affect layout of all pages using Container
