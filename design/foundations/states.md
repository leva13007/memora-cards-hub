# Component States

This document centralizes guidance for common UI states (default, hover, active, focus-visible, disabled, loading, error, success) so individual component specs can reference a shared source of truth.

## 1. Purpose
- Define how global states should look and behave across the design system.
- Align color, motion, and accessibility expectations for repeated patterns.
- Reduce duplication inside component-specific specs.

## 2. Scope
- Applies to interactive UI-kit atoms/molecules (buttons, links, inputs, icons, etc.).
- Covers visual + behavioral considerations for each state listed below.
- Does **not** prescribe component-specific props or API shapes; those live in individual DE docs.

## 3. States Overview
Provide a concise summary for each state; expand in dedicated sections.

| State          | Description                                           | Typical Usage                             |
|----------------|-------------------------------------------------------|-------------------------------------------|
| Default        | Resting appearance                                    | Base rendering when no interaction occurs |
| Hover          | Pointer hover feedback                                | Desktop pointer interactions              |
| Active/Pressed | Momentary pressed/down state                          | Mouse/touch press                         |
| Focus-visible  | Keyboard focus indicator                              | Accessibility compliance                  |
| Disabled       | Non-interactive / muted                               | Forms, buttons, icons when unavailable    |
| Loading        | Temporary busy indicator                              | Async actions                             |
| Error          | Validation or failure feedback                        | Inputs, banners                           |
| Success        | Positive confirmation                                 | Alerts, badges                            |

## 4. Default State
_(Add token references and description for standard resting appearance.)_

## 5. Hover State
_(Describe color shifts, elevation changes, timing, and device applicability.)_

## 6. Active / Pressed State
_(Document pressed behavior, animations, and tactile cues.)_

## 7. Focus-visible State
_(Explain outline styles, contrast requirements, and usage of `:focus-visible`.)_

## 8. Disabled State
_(Detail opacity, interaction blocking, and how to communicate disabled state to assistive tech.)_
Default state for disabled elements should use `opacity: 0.7` and apply the following styles:
  - Cursor: `not-allowed`
  - Pointer events: `none`
  - Color tokens: use muted variants if available (e.g., `--color-text` @ 15% alpha)
  - Maintain layout and spacing to avoid content shifts.

## 9. Loading State
_(Specify spinners/skeletons, aria-busy expectations, and transitions.)_

## 10. Error State
_(Reference color tokens such as `--color-warning`, icon usage, and messaging placement.)_

## 11. Success State
_(Define success hues, iconography, and duration of highlighting.)_

## 12. Accessibility Considerations
- Ensure each state change is perceivable without relying solely on color.
- Pair color changes with iconography or text where necessary.
- Keep keyboard focus styles consistent and compliant with WCAG contrast.

## 13. Tokens & References
- Colors: [design/foundations/tokens.md](./tokens.md)
- Typography: [design/design/DE-0004-Text.md](../design/DE-0004-Text.md)
- Components: reference individual DE docs for state-specific overrides.

## 14. Change Log
| Date       | Change                              | Owner |
|------------|-------------------------------------|-------|
| 2026-01-30 | Initial skeleton created             | TBD   |
