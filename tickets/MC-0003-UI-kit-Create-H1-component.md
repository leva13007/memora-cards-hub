---
id: MC-0003
title: "UI-kit: Create H1 component"
type: Story            # Epic | Feature | Story | Task | Spike | Chore | Improvement
status: Open           # ToDo | Sprint ready | In Progress | In Review | Ready for testing | In testing | Issue found | Blocked | Done
priority: Medium       # Low | Medium | High | Critical
area: "ui-kit/typography"               # ui-kit/typography | ui-kit/buttons | app/editor | backend | infra
author: "Oleh Levchenko"
assignee: ""
created: 2025-12-10
updated: 2025-12-10
---

# MC-0003 — UI-kit: Create H1 component

## Description

As a developer I want to have an **H1** heading component in the UI kit that uses the semantic HTML `<h1>` tag and standardized typography tokens so that page titles and primary headings are consistent across the application and align with the design system.

The **H1** component should:
- Render a semantic `<h1>` element.
- Use design tokens for font size, weight, and color instead of hard-coded values.
- Support responsive typography for Desktop, Tablet, and Mobile breakpoints.
- Integrate cleanly with the existing typography token system introduced in
	[MC-0001-UI-kit-Create-Text-component](./MC-0001-UI-kit-Create-Text-component.md).

Storybook references for H1:
- Default story (iframe):  
	`https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-h1--default&viewMode=story`
- Storybook docs page:  
	`https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-h1--docs`

---

## Requirements / Specifications

Implement one React component: __H1__.

### Base styles

The `H1` component must render a semantic HTML heading element:

- Tag: `<h1>` (no `as` prop for this ticket; the H1 is always rendered as `<h1>`).

The `H1` component must use the following CSS properties and tokens:

- `color: var(--color-text);`
- `font-family: inherit;`  
	(Must resolve to **Inter** via the global typography stack.)
- `font-size: var(--font-size-h-1);`
- `font-weight: var(--font-weight-bold);`
- `line-height: normal;`

Design token requirements:

- `--font-weight-bold: 700`
- `--color-text` is theme-dependent:
	- **Light theme**: `--color-text: #0f172a`
	- **Dark theme**: `--color-text: #f5f7fb`
- `--font-size-h-1` is breakpoint-dependent:
	- **Desktop** (≥1280px): `--font-size-h-1: 2rem`
	- **Tablet** (768–1279px): `--font-size-h-1: 1.75rem`
	- **Mobile** (<768px): `--font-size-h-1: 1.5rem`

The component must **not** hard-code the pixel/rem values directly into component styles; it should rely on the design tokens above, which may be provided via CSS variables.

### Component semantics

- The `H1` component must always render a semantic `<h1>` element.
- The rendered `<h1>` element must apply all typography styles described above.
- The component is intended for page-level or section-level primary headings and should be used once per page where possible, according to accessibility and SEO best practices (enforced at usage level, not by code).

### Component props

For this initial ticket, keep the API minimal and focused on content:

- `children`
	- Type: `ReactNode` (string or nested inline elements).
	- Required: **Yes**.
	- Behavior:
		- Represents the visible heading content inside the `<h1>` element.
		- Example: `<H1>Dashboard</H1>` renders `<h1>Dashboard</h1>` with all H1 typography tokens applied.

Additional props (such as `id`, `className`, or ARIA attributes) may be passed through via standard React `...rest` props, but they are out of scope for detailed specification in this ticket.

---

## Acceptance Criteria  

Typography and tokens:

1. When the `H1` component is rendered, it must render a semantic `<h1>` element.
2. When the `H1` component is rendered, it must use `font-family: inherit;` and resolve to the **Inter** font family (via the global typography stack).
3. When the `H1` component is rendered, it must apply `line-height: normal;`.
4. When the `H1` component is rendered, it must apply `font-weight: var(--font-weight-bold);` with token value `700`.
5. When the application theme is set to Light, the `H1` component must use `color: var(--color-text);` where `--color-text: #0f172a`.
6. When the application theme is set to Dark, the `H1` component must use `color: var(--color-text);` where `--color-text: #f5f7fb`.
7. When the `H1` component is viewed on Desktop screens (≥1280px), it must use `font-size: var(--font-size-h-1);` where `--font-size-h-1: 2rem`.
8. When the `H1` component is viewed on Tablet screens (between 768px and 1279px), it must use `font-size: var(--font-size-h-1);` where `--font-size-h-1: 1.75rem`.
9. When the `H1` component is viewed on Mobile screens (<768px), it must use `font-size: var(--font-size-h-1);` where `--font-size-h-1: 1.5rem`.
10. All visual behavior (font size, font family, font weight, color, line-height) must be driven by the design tokens listed above and not by hard-coded values, except where tokens themselves define explicit values.

Semantics and content:

11. When the `H1` component is rendered with `children="Page title"`, it must render `<h1>Page title</h1>` in the DOM (ignoring additional React wrappers and attributes).
12. The `H1` component must not expose an `as` prop in this initial version; the heading level is fixed to `<h1>`.

Storybook:

13. The `H1` component must be available in Storybook under `UI / Atoms / H1`.
14. The default Storybook story must be reachable via:  
		`https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-h1--default&viewMode=story`.
15. The Storybook docs page must be reachable via:  
		`https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-h1--docs`.

All criteria must be objectively verifiable (e.g., via Storybook, browser devtools, and responsive viewport testing).

---

## Test Coverage  
(Manual or auto-generated)

- Related test cases:
	- TC-MC-0025-UI-H1-Desktop-LightTheme
	- TC-MC-0026-UI-H1-Desktop-DarkTheme
	- TC-MC-0027-UI-H1-Tablet-LightTheme
	- TC-MC-0028-UI-H1-Tablet-DarkTheme
	- TC-MC-0029-UI-H1-Mobile-LightTheme
	- TC-MC-0030-UI-H1-Mobile-DarkTheme

---

## Edge Cases  

Potential pitfalls or scenarios that must be considered:

- Very long H1 text that wraps onto multiple lines (check line-height and spacing).
- H1 used inside different layout containers (verify no clipping or overflow).
- H1 rendered on very small mobile widths (<320px) to verify readability.
- Using multiple `H1` components on the same page (allowed technically, but may be discouraged by design/SEO guidelines).

---

## Related  

- Depends on:
- Related:
- Additional Links:
	- Figma: …
	- PR: …
	- Docs: …

---

## Sprint
- [Sprint 01](../sprints/MC-0001-Sprint-01.md)
