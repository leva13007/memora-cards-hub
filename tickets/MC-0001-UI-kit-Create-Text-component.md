---
id: MC-0001
title: "UI-kit: Create Text component(Light / Medium / Bold)"
type: Story            # Epic | Feature | Story | Task | Spike | Chore | Improvement
status: Open           # ToDo | Sprint ready | In Progress | In Review | Ready for testing | In testing | Issue found | Blocked | Done
priority: Medium       # Low | Medium | High | Critical
area: "ui-kit/typography"               # ui-kit/typography | ui-kit/buttons | app/editor | backend | infra
author: "Oleh Levchenko"
assignee: ""
created: 2025-12-08
updated: 2025-12-08
---

# MC-0001 — UI-kit: Create Text component(Light / Medium / Bold)

## Description
As a developer I want to have a Text component in the UI kit that supports Light, Medium, and Bold font weights so that I can maintain consistent typography across the application.

The Text component is a fundamental building block for displaying text in the application. It should support three font weights: Light, Medium, and Bold. This will allow developers to easily apply different text styles while ensuring consistency with the design system. The component should be flexible enough to handle different screen sizes and themes (Light and Dark).

---

## Requirements / Specifications
Implement three React components: __TextLight__, __TextMedium__, and __TextBold__.
- All the components must use:
  - `font-family: Inter`
  - `color: var(--color-text);`
  - `font-size: var(--fonts-size-text);`
  - `line-height: normal;`
- All the components must have responsive font-sizes for desktop/tablet/mobile:
  - Desktop: `1rem` (16px)
  - Tablet: `0.875rem` (14px)
  - Mobile: `0.75rem` (12px)
- All the components must support Light and Dark themes
  - Dark theme: `--color-text: #f5f7fb`
  - Light theme: `--color-text: #0f172a;`
- All the components must rely on design tokens:
  - `--color-text`
  - `--font-weight-light`
  - `--fonts-size-text`
- Component __TextLight__ must use:
  - `font-weight: var(--font-weight-light);`
  - token value: `300`
- Component __TextMedium__ must use:
  - `font-weight: var(--font-weight-normal);`
  - token value: `400`
- Component __TextBold__ must use:
  - `font-weight: var(--font-weight-bold);`
  - token value: `700`

### Component props

All Text components (__TextLight__, __TextMedium__, __TextBold__) must support the following props:

- `as`
  - Type: HTML tag string.
  - Default: `"span"`.
  - Behavior:
    - Controls which HTML tag is rendered for the Text component.
    - When `as="span"` (default), the component renders a `<span>` element.
    - When `as="p"` (paragraph), the component renders a `<p>` element.
  - The rendered element must preserve all typography styles and tokens defined above, regardless of tag.

- `variant`
  - Type: one of  `"primary"` | `"warning"`.
  - Default: `"primary"`.
  - Behavior:
    - Sets the visual variant of the component (for example, via a CSS class).
    - When `variant="primary"` (default):
      - `color` must use `var(--color-text)`.
    - When `variant="warning"`:
      - `color` must use `var(--color-warning)`.
  - Design token for warning color:
    - `--color-warning: #ec1515;` (for both Light and Dark themes).

---

## Acceptance Criteria  
1. When the Text components are rendered, they must display text with the correct font family `Inter`.
2. When the Text components are rendered, they must apply the correct `line-height: normal;`.
3. When the Text components are viewed on Desktop screens (viewport width ≥1280px), they must use font-size `1rem` (16px).
4. When the Text components are viewed on Tablet screens (viewport width between 768px and 1279px), they must use font-size `0.875rem` (14px).
5. When the Text components are viewed on Mobile screens (viewport width <768px), they must use font-size `0.75rem` (12px).
6. When the application theme is set to Dark and `variant="primary"`, the Text components must use `color: var(--color-text);` where `--color-text: #f5f7fb`.
7. When the application theme is set to Light and `variant="primary"`, the Text components must use `color: var(--color-text);` where `--color-text: #0f172a;`.
8. When `variant="warning"` (for any theme), the Text components must use `color: var(--color-warning);` where `--color-warning: #ec1515;`.
9. When the __TextLight__ component is rendered, it must apply `font-weight: var(--font-weight-light);` with token value `300`.
10. When the __TextMedium__ component is rendered, it must apply `font-weight: var(--font-weight-normal);` with token value `400`.
11. When the __TextBold__ component is rendered, it must apply `font-weight: var(--font-weight-bold);` with token value `700`.
12. When the Text components are rendered without passing the `as` prop, they must render a `<span>` element.
13. When the Text components are rendered with `as="p"`, they must render a `<p>` element.
14. Changing the `as` prop (for example, `span` → `p`) must not affect the applied typography tokens or the `variant` color behavior.

All criteria must be objectively verifiable.

---

## Test Coverage  
(Manual or auto-generated)

- Related test cases:
  - [TC-MC-0001-UI-TextBold-Desktop-LightTheme](../qa_test-cases/UI/TextBold/TC-MC-0001-UI-TextBold-Desktop-LightTheme.md)
  - [TC-MC-0002-UI-TextBold-Desktop-DarkTheme](../qa_test-cases/UI/TextBold/TC-MC-0002-UI-TextBold-Desktop-DarkTheme.md)
  - [TC-MC-0003-UI-TextBold-Tablet-LightTheme](../qa_test-cases/UI/TextBold/TC-MC-0003-UI-TextBold-Tablet-LightTheme.md)
  - [TC-MC-0004-UI-TextBold-Tablet-DarkTheme](../qa_test-cases/UI/TextBold/TC-MC-0004-UI-TextBold-Tablet-DarkTheme.md)
  - [TC-MC-0005-UI-TextBold-Mobile-LightTheme](../qa_test-cases/UI/TextBold/TC-MC-0005-UI-TextBold-Mobile-LightTheme.md)
  - [TC-MC-0006-UI-TextBold-Mobile-DarkTheme](../qa_test-cases/UI/TextBold/TC-MC-0006-UI-TextBold-Mobile-DarkTheme.md)
  - [TC-MC-0007-UI-TextMedium-Desktop-LightTheme](../qa_test-cases/UI/TextMedium/TC-MC-0007-UI-TextMedium-Desktop-LightTheme.md)
  - [TC-MC-0008-UI-TextMedium-Desktop-DarkTheme](../qa_test-cases/UI/TextMedium/TC-MC-0008-UI-TextMedium-Desktop-DarkTheme.md)
  - [TC-MC-0009-UI-TextMedium-Tablet-LightTheme](../qa_test-cases/UI/TextMedium/TC-MC-0009-UI-TextMedium-Tablet-LightTheme.md)
  - [TC-MC-0010-UI-TextMedium-Tablet-DarkTheme](../qa_test-cases/UI/TextMedium/TC-MC-0010-UI-TextMedium-Tablet-DarkTheme.md)
  - [TC-MC-0011-UI-TextMedium-Mobile-LightTheme](../qa_test-cases/UI/TextMedium/TC-MC-0011-UI-TextMedium-Mobile-LightTheme.md)
  - [TC-MC-0012-UI-TextMedium-Mobile-DarkTheme](../qa_test-cases/UI/TextMedium/TC-MC-0012-UI-TextMedium-Mobile-DarkTheme.md)
  - [TC-MC-0013-UI-TextLight-Desktop-LightTheme](../qa_test-cases/UI/TextLight/TC-MC-0013-UI-TextLight-Desktop-LightTheme.md)
  - [TC-MC-0014-UI-TextLight-Desktop-DarkTheme](../qa_test-cases/UI/TextLight/TC-MC-0014-UI-TextLight-Desktop-DarkTheme.md)
  - [TC-MC-0015-UI-TextLight-Tablet-LightTheme](../qa_test-cases/UI/TextLight/TC-MC-0015-UI-TextLight-Tablet-LightTheme.md)
  - [TC-MC-0016-UI-TextLight-Tablet-DarkTheme](../qa_test-cases/UI/TextLight/TC-MC-0016-UI-TextLight-Tablet-DarkTheme.md)
  - [TC-MC-0017-UI-TextLight-Mobile-LightTheme](../qa_test-cases/UI/TextLight/TC-MC-0017-UI-TextLight-Mobile-LightTheme.md)
  - [TC-MC-0018-UI-TextLight-Mobile-DarkTheme](../qa_test-cases/UI/TextLight/TC-MC-0018-UI-TextLight-Mobile-DarkTheme.md)
---

## Edge Cases  
Potential pitfalls or scenarios that must be considered:

- …

---

## Related  
- Depends on:
- Blocks:
- Duplicate of:
- Additional Links:
  - Figma: …
  - PR: …
  - Docs: …

---

## Sprint
- [Sprint 01](../sprints/MC-0001-Sprint-01.md)
