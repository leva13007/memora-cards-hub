---
id: MC-0005
title: "UI-kit: Create Container component"
type: Story            # Epic | Feature | Story | Task | Spike | Chore | Improvement
status: Open           # ToDo | Sprint ready | In Progress | In Review | Ready for testing | In testing | Issue found | Blocked | Done
priority: Medium       # Low | Medium | High | Critical
area: "ui-kit/layout"  # ui-kit/typography | ui-kit/buttons | app/editor | backend | infra
author: "Oleh Levchenko"
assignee: ""
created: 2025-12-12
updated: 2025-12-12
---

# MC-0005 — UI-kit: Create Container component

## Description

As a developer I want to have a **Container** layout component in the UI kit that wraps page content in a centered, responsive column with consistent horizontal padding, so that pages and sections can share a common layout skeleton across Desktop, Tablet, and Mobile.

The **Container** component should:
- Render a semantic HTML `<div>` wrapper element.
- Center itself within the viewport using automatic horizontal margins.
- Apply consistent horizontal padding based on a layout token `--container-padding`.
- Use breakpoint-specific widths for Desktop and Tablet.
- Use fluid width behavior on Mobile.
- Support a `fluid` prop to make the container 100% wide at any breakpoint.

Storybook references for Container:
- Storybook docs page:  
	`https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-container--docs`
- Default story (element view):  
	`https://leva13007.github.io/memora-cards-storybook/?path=/story/ui-atoms-container--default`

---

## Requirements / Specifications

Implement one React component: **Container**.

### Base styles

The `Container` component must render a semantic HTML block element:

- Tag: `<div>`
- The component is a **pure layout wrapper** and must not impose any typography styles.

By default (non-fluid), the `Container` component must apply:

- `margin-left: auto;`
- `margin-right: auto;`
- `padding-left: var(--container-padding, 0);`
- `padding-right: var(--container-padding, 0);`

Layout token requirement:

- `--container-padding: 1rem;`
	- This token defines the horizontal padding on both sides of the content area.
	- The component must **not** hard-code `1rem` directly into styles; it must rely on `var(--container-padding, 0)`.

### Responsive behavior

The `Container` must use breakpoint-specific widths when `fluid` is **false** or not provided.

Breakpoints for this component must align with the global responsive system used in typography tickets (for example, [MC-0004](./MC-0004-UI-kit-Create-H2-component.md)):

- **Desktop**: viewport width **≥1280px**
- **Tablet**: viewport width **768–1279px**
- **Mobile**: viewport width **<768px**

Widths by breakpoint when `fluid` is **false** or omitted:

- **Desktop (≥1280px)**
	- `width: 1200px`
- **Tablet (768–1279px)**
	- `width: 700px`
- **Mobile (<768px)**
	- `width: 100%;`
	- `max-width: 100%;`

Behavior summary (non-fluid):

- On **Desktop (≥1280px)** viewports, the container is a fixed-width column of `1200px`, centered via `margin-left/right: auto`.
- On **Tablet (768–1279px)** viewports, the container is a fixed-width column of `700px`, centered via `margin-left/right: auto`.
- On **Mobile (<768px)** viewports, the container spans the available width with `width: 100%; max-width: 100%;` while still applying horizontal padding from `--container-padding`.

### Component props

Initial API (minimal):

- `children`
	- Type: `ReactNode`.
	- Required: **Yes**.
	- Behavior: content rendered inside the layout wrapper `<div>`.
- `fluid`
	- Type: `boolean`.
	- Required: No.
	- Default: `false`.
	- Behavior:
		- When `fluid` is **true**, the container must use `width: 100%;` regardless of breakpoint.
		- When `fluid` is **true**, any fixed width for Desktop/Tablet (e.g., `1200px` or `700px`) must **not** constrain the container; instead, it stretches to fill the available horizontal space.
		- Horizontal padding via `--container-padding` must still apply when `fluid` is true.

Additional props (e.g., `className`, `style`, `id`, `data-*`, ARIA attributes) may be accepted via spread props and forwarded to the root `<div>`, but they are out of scope for detailed specification in this ticket.

---

## Acceptance Criteria

Layout and semantics:

1. When the `Container` component is rendered, it must use a semantic `<div>` as the root element.
2. The root `<div>` must apply `margin-left: auto; margin-right: auto;` to center the container within the viewport.
3. The root `<div>` must apply `padding-left: var(--container-padding, 0);` and `padding-right: var(--container-padding, 0);`.
4. The horizontal padding must be driven by the `--container-padding` token with default value `1rem` (not hard-coded).

Responsive behavior (non-fluid):

5. On **Desktop** viewports, when `fluid` is `false` or not provided, the container must have `width: 1200px`.
6. On **Tablet** viewports, when `fluid` is `false` or not provided, the container must have `width: 700px`.
7. On **Mobile** viewports, when `fluid` is `false` or not provided, the container must have `width: 100%; max-width: 100%;`.
8. In all cases above, the container must remain horizontally centered via auto margins and padded using `--container-padding`.

Fluid behavior:

9. When `fluid` is set to `true`, the container must use `width: 100%;` at all breakpoints (Desktop, Tablet, Mobile).
10. When `fluid` is `true`, the container must **not** be constrained by the fixed widths `1200px` (Desktop) or `700px` (Tablet).
11. When `fluid` is `true`, the container must still honor horizontal padding defined by `--container-padding`.

Tokenization and implementation:

12. The component must not hard-code the `1rem` padding value; instead it must use `var(--container-padding, 0)` so that theming or layout tokens can override it.
13. All layout behavior (padding, centering) must be compatible with existing global layout and typography tokens (e.g., it must not override the font tokens used by typography components inside the container).

Storybook:

14. The `Container` component must be available in Storybook under `UI / Atoms / Container`.
15. The default documented configuration page must be reachable via:  
	`https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-container--docs`.
16. The default story rendering the actual container element must be reachable via:  
	`https://leva13007.github.io/memora-cards-storybook/?path=/story/ui-atoms-container--default`.

---

## Test Coverage

Manual or automated tests should validate at least the following scenarios (can be covered in separate QA test cases):

- **Desktop, Tablet, Mobile (non-fluid)**:
	- Correct root `<div>` semantics.
	- Correct centering via `margin-left/right: auto`.
	- Correct horizontal padding from `--container-padding`.
	- Width = `1200px` on Desktop, `700px` on Tablet, `100%` on Mobile.
- **Fluid mode**:
	- With `fluid={true}` (or equivalent), container width becomes `100%` on all breakpoints.
	- Padding from `--container-padding` remains applied.
- **Token override**:
	- Overriding `--container-padding` (e.g., via a theme or parent wrapper) correctly changes the effective left/right padding without code changes.
- **Content wrapping**:
	- Child typography components (`H1`, `H2`, `Text`, `TextLink`, etc.) render correctly inside the container and are not affected by container-level styles other than layout.

---

## Edge Cases

Potential pitfalls or scenarios that must be considered:

- Very small mobile widths (e.g., <320px) where horizontal padding might significantly reduce usable content width.
- Container used inside other layout wrappers (e.g., nested containers or grids) and ensuring centering behavior is still correct.
- Pages that intentionally use `fluid` containers for full-bleed content versus fixed-width containers for standard content.
- Overriding `--container-padding` to `0` and ensuring the container still behaves correctly without horizontal padding.

---

## Related

- Depends on / interacts with:

- Future work:
	- Grid or layout primitives that may compose multiple `Container` instances.
	- Page templates that standardize header/body/footer using `Container`.
