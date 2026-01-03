
# Text (Light / Medium / Bold) — Design Reference

## 1. Purpose
Define the visual and semantic rules for the `Text` typography atoms so body text is consistent across themes and breakpoints.

## 2. Scope
Applies to the `TextLight`, `TextMedium`, and `TextBold` UI-kit components.
Does not define application-level typography hierarchy.

## 3. Terminology
- Breakpoint: Mobile / Tablet / Desktop (see `design/foundations/breakpoints.md`)
- Theme: Light / Dark
- Variant: a semantic color mapping applied to Text (`primary`, `warning`)
- `As` prop: a component prop that controls which HTML tag is rendered

## 4. Design Dependencies
- Breakpoints: [design/foundations/breakpoints.md](../foundations/breakpoints.md)
- Theming: [design/foundations/theme.md](../foundations/theme.md)
- Tokens:
	- [design/foundations/tokens.md#typography](../foundations/tokens.md#typography)
	- [design/foundations/tokens.md#colours](../foundations/tokens.md#colours)

## 5. Conceptual Model
`TextLight`, `TextMedium`, and `TextBold` are typography atoms that render semantic text elements with token-driven styles that adapt to the active theme and breakpoint.

## 6. Behavioral Rules
### 6.1 Semantic element
- Default rendering is an inline text element (`<span>`).
- The component may be rendered as another semantic text element (e.g. `<p>`) without changing typography tokens (see non-normative notes).

### 6.2 Shared typography rules
All Text variants are token-driven:
- Font family: `inherit` (must resolve to `Inter` via global typography stack)
- Line height: `normal`
- Font size: `var(--fonts-size-text)` (breakpoint-driven)

### 6.3 Font size by breakpoint
| Token             | Mobile   | Tablet    | Desktop |
|-------------------|----------|-----------|---------|
| --fonts-size-text | 0.75rem  | 0.875rem  | 1rem    |

### 6.4 Weight mapping
| Component      | Token                 |
|----------------|-----------------------|
| `TextLight`    | `var(--font-weight-light)`  |
| `TextMedium`   | `var(--font-weight-normal)` |
| `TextBold`     | `var(--font-weight-bold)`   |

### 6.5 Color variants
Text uses semantic color tokens:
- `primary` (default): `color: var(--color-text)` (theme-driven)
- `warning`: `color: var(--color-warning)`

## 7. States & Variants
- Themes: Light / Dark
- Breakpoints: Mobile / Tablet / Desktop
- Variants: `primary` (default), `warning`
- Default rendered HTML tag is `<span>`, may be overridden via `as` prop.

## 8. Layout & Responsiveness
- Text components must behave consistently across the product breakpoints and themes.

## 9. Tokens & Theming
### Required tokens
- `--fonts-size-text`
- `--font-weight-light`
- `--font-weight-normal`
- `--font-weight-bold`
- `--color-text`
- `--color-warning`

## 10. Accessibility
- When rendered as a non-heading text element, the chosen tag must remain semantically appropriate (e.g. paragraphs use `<p>`).
- Text color must remain readable in both themes.
	- Theme-dependent values are provided by design tokens scoped under the global theme activation model (see `design/foundations/theme.md`).

## 11. Rules & Constraints
- Tickets must not define numeric typography values; they must reference token names and this design doc.
- Text components must not hard-code font sizes; they must use `var(--fonts-size-text)`.
- Text components must not hard-code theme colors; they must use semantic tokens (`--color-text`, `--color-warning`).
- Theme is a global concern:
	- Text components must not manage or override the active theme locally (see `design/foundations/theme.md`).

## 12. Non-normative Implementation Notes
For clarity only (tokens are the source of truth):

## 13. Edge Cases
- N/A

## 14. Change Impact
- Any token changes to `--fonts-size-text`, font-weight tokens, or color tokens require re-running Text-related test runs.
- Changes may affect all body text throughout the product.
