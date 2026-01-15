# Buttons — Design Reference (DE-0008)

## 1. Purpose
Define the core visual, behavioral, and accessibility rules for the `Button` atom so product teams can ship call-to-action elements with consistent styling, icon alignment, and disabled handling across Memora surfaces.

## 2. Scope
- Applies to the base `Button` atom rendered as a semantic `<button>`.
- Covers three visual variants: **Primary**, **Warning**, **Secondary**.
- Specifies icon placement (leading icon), typography, sizing, and disabled treatment.
- Does **not** cover button groups, floating action buttons, split buttons, or routing logic.

## 3. Terminology
- **Variant**: visual treatment defined by background, border, and color tokens.
- **Tone**: semantic meaning (primary action, warning/destructive, secondary/ghost).
- **Icon**: optional graphic placed to the left of the text.
- **Leading icon**: icon rendered before the label text.
- **Disabled state**: non-interactive state sharing the same layout but with reduced opacity (0.7 as specified).

## 4. Design Dependencies
- Typography: [DE-0004-Text](./DE-0004-Text.md) (Buttons inherit `TextMedium` styles.)
- Icons: [DE-0007-Icons](./DE-0007-Icons.md) (Button icons reuse Icon atom rules.)
- Tokens & breakpoints:
  - [design/foundations/tokens.md](../foundations/tokens.md)
  - [design/foundations/breakpoints.md](../foundations/breakpoints.md)
- Theming: [design/foundations/theme.md](../foundations/theme.md)

## 5. Conceptual Model
- A Button is a **single-line** control with optional icon + text.
- Text always uses the `TextMedium` token stack (font family, size, weight, line-height) per breakpoint.
- Icons inherit color from the current text color via `currentColor` and size themselves relative to the `TextMedium` font size.
- Disabled buttons keep layout/spacing identical to enabled buttons but reduce overall opacity to **0.7** and block pointer events.

## 6. Variants
Border should be applied as per the variant table below.
Border-radius: `--border-radius-button` : `0.25rem` for all variants.

### 6.1 Semantic element
- Buttons must render as a semantic `<button>` element by default.

### 6.2 Visual variants
| Variant   | Background        | Border                        | Text/Icon color       | Usage |
|-----------|-------------------|-------------------------------|-----------------------|-------|
| Primary   | `--color-link`    | `--color-link`                 | `--color-text`        | High-emphasis CTAs            |
| Warning   | `--color-warning` | `--color-warning`                 | `--color-text-white`  | Destructive / caution actions |
| Secondary | `--color-bg-secondary` | `1px solid --color-text`      | `--color-text`        | Ghost / low-emphasis actions  |

### 6.2 Visual variants - Hover states
| Variant   | Background              | Border                        | Text/Icon color       |
|-----------|-------------------------|-------------------------------|-----------------------|
| Primary   | `--color-link-hover`    | `--color-link-hover`          | `--color-text`        |
| Warning   | `--color-warning-hover` | `--color-warning-hover`       | `--color-text-white`  |
| Secondary | `--color-bg-secondary-hover` | `1px solid --color-text`      | `--color-text`        |

Other baseline styles:
- Cursor: `pointer`

### 6.3 Focus-visible (accessibility)
Keyboard focus must be clearly visible.

Required focus-visible style:

`outline: 1px solid var(--color-link, currentColor)`

Notes:
- The focus indicator must remain visible in both themes.
- Focus styling must use `:focus-visible` (not only `:focus`).

### 6.4 Icon Rules
1. Icons are optional and appear **only to the left** of the text.
2. Icon size tracks the text size:
   - Desktop (`--fonts-size-text` = 1rem) → icon box 16px (matching `TextMedium` line-height) by default.
   - Tablet → icon 14px.
   - Mobile → icon 12px.
3. Icon color uses `currentColor`, so variant/tone automatically applies.
4. Spacing between icon and text: `0.5rem`.
5. When no text is provided, button should fall back to icon-only configuration (future enhancement) but still honor min width and accessible label.

## 7. States & Variants
- Themes: Light / Dark
- States: default, hover, focus-visible
- No additional variants are defined in this document.
- 
### 7.1 Disabled State
- Apply `opacity: 0.7` to the entire button (affects background, text, icon, and border).
- Disable pointer interactions (`pointer-events: none` when rendered as `<button disabled>` or `aria-disabled="true"`).
- Do not change layout, padding, or spacing; icon alignment must remain intact.

## 8. Layout & Responsiveness
- Horizontal padding: `1rem`
- Vertical padding: `0.625rem`

## 9. Tokens & Theming
### Required tokens
- `--fonts-size-text`
- `--font-weight-semi`
- `--color-link`
- `--color-link-hover`
- `--color-warning`
- `--color-warning-hover`
- `--color-text`
- `--color-text-white`
- `--color-bg-secondary`
- `--color-bg-secondary-hover`

## 10. Accessibility
- Default rendering should be `<button type="button">` with the appropriate `type` override for forms.
- Provide `aria-disabled` when using non-button elements.
- Focus state must be visible for keyboard users (e.g., 2px outline using `--color-link`).
- Ensure icon-only buttons are supplied with `aria-label` or visually hidden text.
