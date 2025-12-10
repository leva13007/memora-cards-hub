---
id: MC-0002
title: "UI-kit: Create TextLink component"
type: Story            # Epic | Feature | Story | Task | Spike | Chore | Improvement
status: Open           # ToDo | Sprint ready | In Progress | In Review | Ready for testing | In testing | Issue found | Blocked | Done
priority: Medium       # Low | Medium | High | Critical
area: "ui-kit/typography"               # ui-kit/typography | ui-kit/buttons | app/editor | backend | infra
author: "Oleh Levchenko"
assignee: ""
created: 2025-12-10
updated: 2025-12-10
labels: []             # free-form tags
links:
  figma: ""
  pr: ""
  design-doc: ""
  related-tickets:
    - MC-0001-UI-kit-Create-Text-component
---

# MC-0002 — UI-kit: Create TextLink component

## Description
As a developer I want to have a **TextLink** component in the UI kit that visually matches the `TextMedium` typography but behaves like a link, so that I can add in-content navigation using a consistent, accessible design.

The **TextLink** component should:
- Reuse the same typography styles as `TextMedium` (font family, font size, line height, and font weight).
- Apply dedicated link color tokens for default and hover states in both Light and Dark themes.
- Expose a minimal API for navigation-like usage (`to` and `content`) while keeping Storybook navigation behavior turned off.

Storybook references for **TextLink**:
- Default story (iframe):  
	`https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-textlink--default&viewMode=story`
- Storybook docs page:  
	`https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-textlink--docs`

---

## Requirements / Specifications

Implement one React component: __TextLink__.

### Base styles

The `TextLink` component must reuse the same base typography tokens and behavior as the `TextMedium` component defined in ticket MC-0001:

- `font-family: inherit;`  
	(Must resolve to **Inter** via the global typography stack.)
- `font-size: var(--fonts-size-text);`
- `line-height: normal;`
- `font-weight: var(--font-weight-normal);` (token value: `400`)
- Responsive font-sizes for desktop/tablet/mobile (via `--fonts-size-text`):
  - Desktop: `1rem` (16px)
  - Tablet: `0.875rem` (14px)
  - Mobile: `0.75rem` (12px)

### Link color tokens and behavior

Instead of using `--color-text` like `TextMedium`, `TextLink` must rely on dedicated link tokens and styles:

- Base color style:
  - `color: var(--color-link);`
- Hover color style:
  - On hover, `color: var(--color-link-hover);`
- Other visual styles:
  - `cursor: pointer;`
  - `text-decoration: unset;` (no underline by default; any decoration is controlled by design tokens / CSS, not the browser default)

Theme-specific token values:

- **Light theme**:
  - `--color-link: #1a73e8;`
  - `--color-link-hover: #174ea6;`
- **Dark theme**:
  - `--color-link: #8ab4f8;`
  - `--color-link-hover: #174ea6;`

The component must rely on design tokens:

- `--fonts-size-text`
- `--font-weight-normal`
- `--color-link`
- `--color-link-hover`

### Component semantics

- The `TextLink` component must render a semantic HTML anchor element:
  - `<a>`
- The rendered `<a>` element must apply all typography and link styles described above.
- Storybook navigation behavior for the underlying `<a>` should be **turned off** (for example, by using a dummy `href` or Storybook controls) so that clicking links in stories does not navigate away from the Storybook UI.

### Component props

The `TextLink` component must support at least the following props:

- `to`
  - Type: `string`.
  - Required: **Yes** (for production usage; in Storybook it may use a placeholder value when not set).
  - Behavior:
    - Maps directly to the anchor `href` attribute.
    - When `to="https://example.com"`, the component must render `<a href="https://example.com">…</a>`.

- `content`
  - Type: `string`.
  - Required: **Yes**.
  - Default example value: `"The TextLink text content"`.
  - Behavior:
    - Sets the visible text content inside the `<a>` element.
    - When `content="The TextLink text content"` and `to="/path"`, the rendered markup must be:
      - `<a href="/path">The TextLink text content</a>`

The component may later support additional optional props (for example, `target`, `rel`, or `aria-*` attributes), but those are out of scope for this initial ticket unless explicitly added.

---

## Acceptance Criteria  
1. When the `TextLink` component is rendered, it must use the `Inter` font family.
2. When the `TextLink` component is rendered, it must apply `line-height: normal;`.
3. When the `TextLink` component is viewed on Desktop screens (≥1193px), it must use font-size `1rem` (16px) via `var(--fonts-size-text)`.
4. When the `TextLink` component is viewed on Tablet screens (between 768px and 1192px), it must use font-size `0.875rem` (14px) via `var(--fonts-size-text)`.
5. When the `TextLink` component is viewed on Mobile screens (<768px), it must use font-size `0.75rem` (12px) via `var(--fonts-size-text)`.
6. When the `TextLink` component is rendered, it must apply `font-weight: var(--font-weight-normal);` with token value `400`.
7. When the application theme is set to Light, the `TextLink` component must use `color: var(--color-link);` where `--color-link: #1a73e8;` in its default (non-hover) state.
8. When the application theme is set to Dark, the `TextLink` component must use `color: var(--color-link);` where `--color-link: #8ab4f8;` in its default (non-hover) state.
9. When the pointer hovers over the `TextLink` component in Light theme, the `color` must change to `var(--color-link-hover);` where `--color-link-hover: #174ea6;`.
10. When the pointer hovers over the `TextLink` component in Dark theme, the `color` must change to `var(--color-link-hover);` where `--color-link-hover: #174ea6;`.
11. When the `TextLink` component is rendered, it must apply `cursor: pointer;` and `text-decoration: unset;` (no browser default underline).
12. When the `TextLink` component is rendered with `to="/somewhere"` and `content="The TextLink text content"`, it must render an anchor element `<a href="/somewhere">The TextLink text content</a>`.
13. When the `TextLink` component is rendered without a `to` value in Storybook, it must not navigate the browser away from the Storybook UI (navigation behavior must be effectively turned off in stories).
14. All visual behavior (font size, font family, font weight, colors, line-height) must be driven by the design tokens listed above and not by hard-coded values, except where tokens themselves define explicit values.

All criteria must be objectively verifiable.

---

## Test Coverage  
(Manual or auto-generated)

- Related test cases:
  - TC-MC-XXXX — TextLink – Desktop – Light Theme
  - TC-MC-YYYY — TextLink – Desktop – Dark Theme
  - TC-MC-ZZZZ — TextLink – Tablet/Mobile – Light/Dark Theme
- Scenarios to validate:
  - Typographic consistency with `TextMedium` across breakpoints.
  - Link color and hover behavior in Light and Dark themes.
  - Proper mapping of `to` → `href` and `content` → visible text.
  - No unexpected navigation when interacting with Storybook stories.

---

## Edge Cases  
Potential pitfalls or scenarios that must be considered:

- Very long link text (wrapping, multi-line behavior, and hover state on wrapped text).
- Links placed inside dense text blocks (spacing and legibility at small font sizes).
- Links inside dark backgrounds with Dark theme active (contrast remains acceptable using `--color-link` and `--color-link-hover`).
- Missing or empty `content` causing an empty anchor; should be prevented by props typing/usage.
- Non-HTTP `to` values (for example, `mailto:` or `#hash`) should still map correctly to `href` without breaking styles.

---

## Related  
- Depends on: [MC-0001 — UI-kit: Create Text component](./MC-0001-UI-kit-Create-Text-component.md)
- Blocks: …
- Duplicate of: …
- Additional Links:
  - Figma: …
  - PR: …
  - Docs: …
