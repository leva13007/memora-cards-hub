# TextArea — Design Reference (DE-0010)

## 1. Purpose
Define the Memora `TextArea` atom so multi-line input fields remain visually consistent with `TextInput`, while supporting longer text entry, error messaging, and disabled behavior.

## 2. Scope
- Applies to multi-line text entry rendered via `<textarea>`.
- Shares the same states as `TextInput`: **Primary**, **Invalid**, **Disabled**.
- Adds requirements for default height (3 rows) and non-resizable behavior.
- Excludes rich text editors, auto-growing text areas, or drag-resizable controls.

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
- Default rendered element: `<textarea rows="3" autocomplete="off" spellcheck="true">`.
- Layout spacing matches TextInput: 0.375rem between label and field, 0.375rem between field and error text.
- Height grows with content when `rows` prop is increased, but users cannot drag to resize (CSS `resize: none`).

## 6. Behavioral Rules
- Focus, invalid, and disabled behaviors mirror TextInput (border colors, opacity, pointer blocking).
- Default height: 3 rows (~ `line-height * 3` + vertical padding). Developers can override via `rows` prop, but min is 2 rows.
- Scrollbar appears when text exceeds visible area; internal padding remains constant.
- Placeholder text uses same typography at 60% opacity.

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
- Width: fluid (fills container) with minimum width 240px.
- Height: default rows = 3; calculate using `line-height * rows + vertical padding * 2`. On Desktop, ~120px; adjust per breakpoint to keep comfortable line spacing.
- `resize: none` to prevent browser drag handles. Auto-grow can be implemented programmatically but is not default behavior.
- Maintain 16px horizontal gutters between adjacent TextAreas.

## 9. Tokens & Theming
- Typography: `TextMedium` for label/value.
- Colors follow TextInput tokens: `--color-text`, `--color-link`, `--color-warning`, `--color-bg`, `--color-grey`.
- Border radius uses `--border-radius`.
- Padding: horizontal 12px Desktop/Tablet, 10px Mobile; vertical 8px Desktop/Tablet, 6px Mobile.
- Max height token (optional) may be added later; until then, `max-height` defaults to `line-height * 8 rows` to avoid runaway growth.

## 10. Accessibility
- Associate labels via `for`/`id` or `aria-labelledby`.
- Use `aria-invalid="true"` when in Invalid state.
- Reference error text via `aria-describedby`; error text uses `role="alert"` for immediate screen reader feedback.
- Disabled fields should use native `disabled` attribute; if not possible, set `aria-disabled` and remove from tab order.
- Ensure focus outline meets contrast requirements; multiline fields typically require more obvious focus rings due to larger area.

## 11. Rules & Constraints
1. No user-resizable handles (`resize: none`).
2. Height changes only when `rows` prop or auto-grow logic updates; state changes alone must not alter height.
3. Tokens drive all spacing, colors, typography; do not hardcode values.
4. Multi-line content must never obscure the label; label remains above even when content scrolls.

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
- When `rows` is set below 2 or above 10, clamp to `[2, 10]` to maintain usability (optional guard).
- Copy/paste of formatted text should degrade gracefully (strip unsupported formatting by default).
- Disabled + invalid request: disabled visual takes precedence; no warning border, `aria-invalid` remains `false`.

## 14. Change Impact
- Any change to TextInput tokens/behavior must be mirrored here to keep parity.
- Updates to `--color-warning` or `--color-link` require QA/test case updates for TextArea as well.
- If auto-grow or resize behavior is revisited, update QA assets and component API docs accordingly.
