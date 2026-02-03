# TextArea — Design Reference (DE-0010)

## 1. Purpose
Define the Memora `TextArea` atom so multi-line input fields remain visually consistent with `TextInput`, while supporting longer text entry, error messaging, and disabled behavior.

## 2. Scope
- Applies to multi-line text entry rendered via `<textarea>`.
- Shares the same states as `TextInput`: **Primary**, **Invalid**, **Disabled**.
- Adds requirements for default height (3 rows) and non-resizable behavior.

## 3. Terminology
- **Row**: A single line of text in the textarea; default = 3 rows on load.
- **Primary state**: Default visual presentation.
- **Invalid state**: Error condition with warning colors and message.
- **Disabled**: Non-interactive, lower-contrast styling.

## 4. Design Dependencies
- Typography: [DE-0004-Text](./DE-0004-Text.md) — TextMedium for labels, value, error copy.
- Icons (future adornments): [DE-0007-Icons](./DE-0007-Icons.md).
- Base single-line reference: [DE-0009-TextInput](./DE-0009-TextInput.md) (TextArea inherits all tokens and states unless overridden here).
- Foundations:
	- [design/foundations/tokens.md](../foundations/tokens.md)
	- [design/foundations/breakpoints.md](../foundations/breakpoints.md)
	- [design/foundations/theme.md](../foundations/theme.md)

## 5. Conceptual Model
- Structure: `Label` (optional) → `Textarea field` → `Error text`.
- Default rendered element: `<textarea rows="3" autocomplete="off" spellcheck="true">` with a border, vertical padding, and horizontal padding.
- Height grows with content when `rows` prop is increased, but users cannot drag to resize (CSS `resize: none`).
- Layout is vertical stack with consistent spacing.

## 6. Behavioral Rules
- Focus, invalid, and disabled behaviors mirror TextInput (border colors, opacity, pointer blocking).
- Default height: 3 rows (~ `line-height * 3` + vertical padding). Developers can override via `rows` prop, but min is 2 rows.
- Scrollbar appears when text exceeds visible area; internal padding remains constant.
- Placeholder text uses same typography at 70% opacity.

## 7. States & Visuals

| State     | Border color          | Background              | Text color           | Label                        | Error text                   |
|-----------|-----------------------|-------------------------|----------------------|------------------------------|------------------------------|
| Primary   | `--color-text`        | `--color-bg`            | `--color-text`       | Label text `--color-text`    |                              |
| Invalid   | `--color-warning`     | `--color-warning` @ 70% | `--color-warning`    | Label text `--color-warning` | Error text `--color-warning` |
| Disabled  | `--color-text` @ 70%	| `--color-grey`          | `--color-text` @ 70% | Label hidden or muted        |                              |

### 7.1 Focus state
- On focus, border color changes to `--color-link`.
- Outline: `var(--outline) solid var(--color-link, currentColor)`.

### 7.2 Label Rules
1. Labels, when provided, render above the input using `TextMedium` typography (same tokens as body text) and `--color-text`.
2. Label spacing: `--size-5` gap between label and input.
3. ~~Required indicators (e.g., `*`) appear within the label; use `--color-warning` for the indicator only.~~

### 7.3 Error Text Rules
1. Error text is optional and renders only when the field is invalid.
2. Error message sits `--size-5` below the input and left-aligns with the field content.
3. Typography: uses `TextMedium` tokens with `--color-warning`.
4. Error text must set `role="alert"` for screen readers.

## 8. Layout & Responsiveness
- Default `width` is fluid; component stretches to the width of its container while preserving internal padding.
- ~~Minimum tap target height: 40px on Desktop/Tablet, 36px on Mobile (padding may adjust slightly per breakpoint to keep this minimum).~~
- Horizontal padding: `--gap-horizontal`; vertical padding: `--gap-vertical`.
- Label, field, and error text always align on the same left edge; right edge follows container width.
- `Label` sits `--size-5` above the input, `error text` sits `--size-5` below
- ~~When placed in responsive grids, ensure gutter spacing keeps at least 16px clearance between adjacent inputs.~~
- Height: default rows = 3; calculate using `line-height * rows + vertical padding * 2`. On Desktop, ~120px; adjust per breakpoint to keep comfortable line spacing.
- `resize: none` to prevent browser drag handles. Auto-grow can be implemented programmatically but is not default behavior.

## 9. Tokens & Theming
- Typography: `TextMedium`.
- Colors:
	- Primary text/border: `--color-text`
	- Focus outline: `--color-link`
	- Error text/border: `--color-warning`
	- Error background: `--color-warning` @ 70%
  - Disabled text/border: `--color-text` @ 70%
	- Placeholder: `--color-text` @ 70% opacity
- Border radius reuses the global control radius token `--border-radius`.
- Background follows theme: `--color-bg` for primary, `--color-warning` @ 70% for invalid, `--color-grey` for disabled.
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
- Recommended DOM:
	```html
	<div class="text-area">
		<label>Label</label>
		<textarea rows="3"></textarea>
		<p class="error-text">Error</p>
	</div>
	```
- Apply `resize: none` and `overflow: auto` to the textarea.
- Consider exposing `minRows`/`maxRows` props for auto-grow implementations while keeping default at 3 rows.
- Reuse TextInput CSS variables to keep visual parity; only height differs.

## 13. Edge Cases
- Empty label: require `aria-label` for accessibility.
- Extremely long text should scroll inside the textarea; maintain internal padding and show scrollbar.
- Copy/paste of formatted text should degrade gracefully (strip unsupported formatting by default).
- Disabled + invalid request: disabled visual takes precedence; no warning border, `aria-invalid` remains `false`.

## 14. Change Impact
- Any change to TextInput tokens/behavior must be mirrored here to keep parity.
- Updates to `--color-warning` or `--color-link` require QA/test case updates for TextArea as well.
- If auto-grow or resize behavior is revisited, update QA assets and component API docs accordingly.
