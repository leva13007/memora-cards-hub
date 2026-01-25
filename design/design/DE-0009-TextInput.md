# TextInput — Design Reference (DE-0009)

## 1. Purpose
Define the visual, behavioral, and accessibility rules of the `TextInput` atom so forms across Memora stay consistent, readable, and accessible. This spec covers labels, error messaging, default and invalid styling, and disabled behavior.

## 2. Scope
- Applies to single-line text inputs used for forms, filters, and simple search fields.
- Covers two visual states: **Primary** (default) and **Invalid** (error), plus the **Disabled** state.
- Specifies label placement, error text behavior, typography, spacing, and focus affordances.
- Excludes multi-line textarea, masked inputs, and complex components (e.g., combo boxes, date pickers).

## 3. Terminology
- **Label**: Text describing the input, rendered above the field when provided.
- **Helper / Error text**: Supporting copy below the field. Error text uses the warning color token.
- **Primary state**: Default, valid styling.
- **Invalid state**: Displays error styling when validation fails.
- **Disabled**: Input cannot be interacted with; visuals show reduced emphasis.

## 4. Design Dependencies
- Typography: [DE-0004-Text](./DE-0004-Text.md) — `TextMedium` is the base for labels, input text, and error.
- Icons (optional prefix/suffix in future work): [DE-0007-Icons](./DE-0007-Icons.md).
- Buttons / other controls may pair with TextInput but are out of scope.
- Tokens & foundations:
	- [design/foundations/tokens.md](../foundations/tokens.md)
	- [design/foundations/breakpoints.md](../foundations/breakpoints.md)
	- [design/foundations/theme.md](../foundations/theme.md)

## 5. Conceptual Model
- Composition: `Label` (optional) → `Input field` (TextMedium typography) → `Helper/Error text` (optional).
- Input is rendered as `<input type="text">` (or email/password variations) with a 1px border, 8px vertical padding, and 12px horizontal padding by default.
- Layout is vertical stack with consistent spacing: `label` sits 0.375rem above the input, error text sits 0.375rem below.

## 6. Behavioral Rules
- Focus: On focus, the input border color changes to `--color-link` with a 2px outline for accessibility.
- Invalid state: When invalid, border color changes to `--color-warning`, and error text appears below the input.
- Disabled state: Input and associated text reduce opacity to 0.7 and block pointer events.
- Placeholder text uses the same typography but at 60% opacity.

## 7. States & Visuals

| State     | Border color               | Background                    | Text color                 | Label                        | Error text                   |
|-----------|----------------------------|-------------------------------|----------------------------|------------------------------|------------------------------|
| Primary   | `--color-text`             | `--color-bg`                  | `--color-text`             | Label text `--color-text`    |                              |
| Invalid   | `--color-warning`          | `--color-warning` @ 15% alpha | `--color-warning`          | Label text `--color-warning` | Error text `--color-warning` |
| Disabled  | `--color-text` @ 15% alpha | `--color-grey`                | `--color-text` @ 15% alpha | Label hidden or muted        |                              |

### 7.1 Focus state
- On focus, border color changes to `--color-link`.
- Outline: `2px solid var(--color-link, currentColor)`.

### 7.2 Label Rules
1. Labels, when provided, render above the input using `TextMedium` typography (same tokens as body text) and `--color-text`.
2. Required indicators (e.g., `*`) appear within the label; use `--color-warning` for the indicator only.
3. Label spacing: 0.375rem gap between label and input.

### 7.3 Error Text Rules
1. Error text is optional and renders only when the field is invalid.
2. Error message sits 0.375rem below the input and left-aligns with the field content.
3. Typography: uses `TextMedium` tokens with `--color-warning`.
4. Error text must set `role="alert"` for screen readers.

## 8. Layout & Responsiveness
- Default width is fluid; component stretches to the width of its container while preserving internal padding.
- Minimum tap target height: 40px on Desktop/Tablet, 36px on Mobile (padding may adjust slightly per breakpoint to keep this minimum).
- Horizontal padding: 12px Desktop/Tablet, 10px Mobile; vertical padding: 8px Desktop/Tablet, 6px Mobile.
- Label, field, and error text always align on the same left edge; right edge follows container width.
- When placed in responsive grids, ensure gutter spacing keeps at least 16px clearance between adjacent inputs.

## 9. Tokens & Theming
- Typography: `TextMedium`.
- Colors:
	- Primary text/border: `--color-text`
	- Focus outline: `--color-link`
	- Error text/border: `--color-warning`
	- Error background: `--color-warning` @ 15% alpha
  - Disabled text/border: `--color-text` @ 15% alpha
	- Placeholder: `--color-text` @ 60% opacity
- Border radius reuses the global control radius token `--border-radius`.
- Background follows theme: `--color-bg` for primary, `--color-warning` @ 15% alpha for invalid, `--color-grey` for disabled.
- Do not hardcode values outside of tokens; any new token additions must be documented in `design/foundations/tokens.md` first.

## 10. Accessibility
- Every input must be associated with a visible label using `label for` / `id`, or `aria-labelledby` when labels are not adjacent.
- Set `aria-invalid="true"` when the field is in the Invalid state.
- Error text must be referenced via `aria-describedby` so screen readers announce supporting copy; error text additionally uses `role="alert"` for immediate announcement.
- Disabled fields use the native `disabled` attribute; if rendered via custom element, apply `aria-disabled="true"` and prevent focus.
- Focus outline must always be visible and meet WCAG contrast against the background.

## 11. Rules & Constraints
1. TextInput must never change height when switching between primary/invalid/disabled states.
2. Error state should not appear until after a validation event (blur, submit, or explicit validation trigger).
3. Component must not introduce custom font sizes; rely on `TextMedium` tokens to inherit responsive typography.
4. Icons or adornments (future enhancement) must not break spacing rules; they sit inside the input while maintaining minimum padding.

## 12. Non-normative Implementation Notes
- Recommended structure:
	```html
	<div class="text-input">
	  <label>Label</label>
	  <input />
	  <p class="error-text">Helper/error</p>
	</div>
	```
- Use CSS custom properties for colors/padding so consuming apps can theme without rewriting styles.
- To support prefix/suffix icons, wrap the `<input>` in an inline-flex container with gap tokens, ensuring the actual input element still fills remaining width.
- Validation logic should be decoupled from UI; input accepts `state="invalid"` or similar prop driven by upstream forms.

## 13. Edge Cases
- Empty label: component renders without label but still must include an accessible name (e.g., `aria-label`).
- Long labels or error text must wrap, never truncate; keep 4px spacing even when multi-line.
- Inputs inside tight containers (e.g., modal sidebars) must retain minimum width of 200px; below that, typography may wrap but padding stays constant.
- When both disabled and invalid states are requested, disabled takes precedence (no error color, opacity applied, `aria-invalid` remains `false`).

## 14. Change Impact
- Updates to `TextMedium` typography tokens affect label/input/error sizing.
- Changes to warning token (`--color-warning`) require QA updates for invalid state.
- Accessibility changes (e.g., ARIA guidance) must be propagated to QA test cases and Storybook docs.
