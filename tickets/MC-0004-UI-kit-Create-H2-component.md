---
id: MC-0004
title: "UI-kit: Create H2 component"
type: Story            # Epic | Feature | Story | Task | Spike | Chore | Improvement
status: Open           # ToDo | Sprint ready | In Progress | In Review | Ready for testing | In testing | Issue found | Blocked | Done
priority: Medium       # Low | Medium | High | Critical
area: "ui-kit/typography"               # ui-kit/typography | ui-kit/buttons | app/editor | backend | infra
author: "Oleh Levchenko"
assignee: ""
created: 2025-12-11
updated: 2025-12-11
---

# MC-0004 — UI-kit: Create H2 component

## Description

As a developer I want to have an **H2** heading component in the UI kit that uses the semantic HTML `<h2>` tag and standardized typography tokens so that secondary headings and section titles are consistent across the application and align with the design system.

The **H2** component should:
- Render a semantic `<h2>` element.
- Use design tokens for font size, weight, and color instead of hard-coded values.
- Support responsive typography for Desktop, Tablet, and Mobile breakpoints.
- Integrate cleanly with the existing typography token system introduced in
	[MC-0001-UI-kit-Create-Text-component](./MC-0001-UI-kit-Create-Text-component.md) and extended in
	[MC-0003-UI-kit-Create-H1-component](./MC-0003-UI-kit-Create-H1-component.md).

Storybook references for H2 (to be implemented similarly to H1):
- Default story (iframe):  
	`https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-h2--default&viewMode=story`
- Storybook docs page:  
	`https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-h2--docs`

---

## Requirements / Specifications

Implement one React component: __H2__.

### Base styles

The `H2` component must render a semantic HTML heading element:

- Tag: `<h2>` (no `as` prop for this ticket; the H2 is always rendered as `<h2>`).

The `H2` component must use the following CSS properties and tokens:

- `color: var(--color-text);`
- `font-family: inherit;`  
	(Must resolve to **Inter** via the global typography stack.)
- `font-size: var(--font-size-h-2);`
- `font-weight: var(--font-weight-semi);`
- `line-height: normal;`

Design token requirements:

- `--font-weight-semi: 600`
- `--color-text` is theme-dependent:
	- **Light theme**: `--color-text: #0f172a`
	- **Dark theme**: `--color-text: #f5f7fb`
- `--font-size-h-2` is breakpoint-dependent:
	- **Desktop** (≥1280px): `--font-size-h-2: 1.5rem`
	- **Tablet** (768–1279px): `--font-size-h-2: 1.25rem`
	- **Mobile** (<768px): `--font-size-h-2: 1.125rem`

The component must **not** hard-code the pixel/rem values directly into component styles; it should rely on the design tokens above, which may be provided via CSS variables.

### Component semantics

- The `H2` component must always render a semantic `<h2>` element.
- The rendered `<h2>` element must apply all typography styles described above.
- The component is intended for section-level headings and subsections below the main page title (H1) and should follow logical heading hierarchy best practices (enforced at usage level, not by code).

### Component props

For this initial ticket, keep the API minimal and focused on content:

- `children`
	- Type: `ReactNode` (string or nested inline elements).
	- Required: **Yes**.
	- Behavior:
		- Represents the visible heading content inside the `<h2>` element.
		- Example: `<H2>Section title</H2>` renders `<h2>Section title</h2>` with all H2 typography tokens applied.

Additional props (such as `id`, `className`, or ARIA attributes) may be passed through via standard React `...rest` props, but they are out of scope for detailed specification in this ticket.

---

## Acceptance Criteria  

Typography and tokens:

1. When the `H2` component is rendered, it must render a semantic `<h2>` element.
2. When the `H2` component is rendered, it must use `font-family: inherit;` and resolve to the **Inter** font family (via the global typography stack).
3. When the `H2` component is rendered, it must apply `line-height: normal;`.
4. When the `H2` component is rendered, it must apply `font-weight: var(--font-weight-semi);` with token value `600`.
5. When the application theme is set to Light, the `H2` component must use `color: var(--color-text);` where `--color-text: #0f172a`.
6. When the application theme is set to Dark, the `H2` component must use `color: var(--color-text);` where `--color-text: #f5f7fb`.
7. When the `H2` component is viewed on Desktop screens (≥1280px), it must use `font-size: var(--font-size-h-2);` where `--font-size-h-2: 1.5rem`.
8. When the `H2` component is viewed on Tablet screens (between 768px and 1279px), it must use `font-size: var(--font-size-h-2);` where `--font-size-h-2: 1.25rem`.
9. When the `H2` component is viewed on Mobile screens (<768px), it must use `font-size: var(--font-size-h-2);` where `--font-size-h-2: 1.125rem`.
10. All visual behavior (font size, font family, font weight, color, line-height) must be driven by the design tokens listed above and not by hard-coded values, except where tokens themselves define explicit values.

Semantics and content:

11. When the `H2` component is rendered with `children="Section title"`, it must render `<h2>Section title</h2>` in the DOM (ignoring additional React wrappers and attributes).
12. The `H2` component must not expose an `as` prop in this initial version; the heading level is fixed to `<h2>`.

Storybook:

13. The `H2` component must be available in Storybook under `UI / Atoms / H2`.
14. The default Storybook story must be reachable via:  
		`https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-h2--default&viewMode=story`.
15. The Storybook docs page must be reachable via:  
		`https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-h2--docs`.

All criteria must be objectively verifiable (e.g., via Storybook, browser devtools, and responsive viewport testing).

---

## Test Coverage  
(Manual or auto-generated)

- Related test cases:
	- TC-MC-0031-UI-H2-Desktop-LightTheme
	- TC-MC-0032-UI-H2-Desktop-DarkTheme
	- TC-MC-0033-UI-H2-Tablet-LightTheme
	- TC-MC-0034-UI-H2-Tablet-DarkTheme
	- TC-MC-0035-UI-H2-Mobile-LightTheme
	- TC-MC-0036-UI-H2-Mobile-DarkTheme

---

## Edge Cases  

Potential pitfalls or scenarios that must be considered:

- Very long H2 text that wraps onto multiple lines (check line-height and spacing).
- H2 used inside different layout containers (verify no clipping or overflow).
- H2 rendered on very small mobile widths (<320px) to verify readability.
- Using multiple `H2` components under a single `H1` and ensuring logical heading hierarchy in templates.

---

## Related  

- Depends on:
- Related:
	- [MC-0003 — UI-kit: Create H1 component](./MC-0003-UI-kit-Create-H1-component.md)
- Additional Links:
	- Figma: …
	- PR: …
	- Docs: …

---

## Sprint
- [Sprint 01](../sprints/MC-0001-Sprint-01.md)
