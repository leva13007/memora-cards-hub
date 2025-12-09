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
updated: YYYY-MM-DD
labels: []             # free-form tags
links:
  figma: ""
  pr: ""
  design-doc: ""
  related-tickets: []
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
  - `font-weight: var(--font-weight-semi);`
  - token value: `600`

---

## Acceptance Criteria  
1. When the Text components are rendered, they must display text with the correct font family `Inter`.
2. When the Text components are rendered, they must apply the correct `line-height: normal;`.
3. When the Text components are viewed on Desktop screen > 1193px, they must use font-size `1rem` (16px).
4. When the Text components are viewed on Tablet screen between 768px and 1192px, they must use font-size `0.875rem` (14px).
5. When the Text components are viewed on Mobile screen < 768px, they must use font-size `0.75rem` (12px).
6. When the application theme is set to Dark, the Text components must use `--color-text: #f5f7fb`.
7. When the application theme is set to Light, the Text components must use `--color-text: #0f172a;`.
8. When the __TextLight__ component is rendered, it must apply `font-weight: var(--font-weight-light);` with token value `300`.
9. When the __TextMedium__ component is rendered, it must apply `font-weight: var(--font-weight-normal);` with token value `400`.
10. When the __TextBold__ component is rendered, it must apply `font-weight: var(--font-weight-semi);` with token value `600`.

All criteria must be objectively verifiable.

---

## Test Coverage  
(Manual or auto-generated)

- Related test cases:
  - TC-MC-XXXX
  - TC-MC-YYYY
- Scenarios to validate:
  - …
  - …

---

## Edge Cases  
Potential pitfalls or scenarios that must be considered:

- …

---

## Related  
- Depends on: …
- Blocks: …
- Duplicate of: …
- Additional Links:
  - Figma: …
  - PR: …
  - Docs: …
