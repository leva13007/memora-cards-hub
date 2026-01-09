---
id: TC-MC-0031
title: "UI-kit: H2 – Desktop – Light Theme – Typography Tokens"
type: UI
priority: Medium
area: "ui-kit/typography"
component: "H2"
related-ticket: "MC-0004-UI-kit-Create-H2-component"
status: Active
created: 2025-12-11
updated: 2025-12-11
---

# TC-MC-0031 — UI: H2 – Desktop – Light Theme – Typography Tokens

## Objective

Validate that the `H2` UI component renders correctly on **Desktop** viewport in **Light theme**, using the expected typography design tokens and semantic `<h2>` behavior defined in ticket  
[MC-0004-UI-kit-Create-H2-component](../../../tickets/Story/MC-0004-UI-kit-Create-H2-component.md).

Specifically confirm on desktop viewport (≥1280px):

- correct `<h2>` semantics in the DOM
- correct font family (inheriting **Inter**)
- correct desktop font size from token `--font-size-h-2`
- correct font-weight via `--font-weight-semi`
- correct text color for **Light** theme via `--color-text`
- correct line-height
- no visual or spacing inconsistencies

---

## Preconditions

- Application or Storybook is running.
- The `H2` component is available (e.g., via Storybook story `UI / Atoms / H2`).
- Browser viewport width is ≥ **1280px** (desktop breakpoint).
- Application theme is set to **Light**.
- Design tokens are loaded:
	- `--color-text`
	- `--font-size-h-2`
	- `--font-weight-semi`
- Browser devtools are available to inspect computed styles.

---

## Test Data

_Static UI verification; no dynamic data required._

Environment assumptions:

| Parameter      | Value                    |
|----------------|--------------------------|
| Device         | Desktop                  |
| Viewport       | ≥ 1280px                 |
| Theme          | Light                    |
| Browser        | Latest Chrome / Chromium |

---

## Steps

1. Open Storybook or the application in a desktop browser.
2. Set viewport width to **≥ 1280px**.
3. Ensure the **Light** theme is active.
4. Navigate to the [H2 default story iframe](https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-h2--default&viewMode=story) or `H2` [Storybook docs page](https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-h2--docs) that showcases the `H2` component (`UI / Atoms / H2`).
5. If the story supports controls/args for content, set the heading text to a simple value (for example, `"Section title"`). Otherwise, use the default example text shown in the story.
6. Identify a rendered `H2` element in the canvas area.
7. Open browser devtools and inspect the heading element.
8. In the **Elements** panel, verify that the rendered element is a semantic `<h2>` (not `<span>`, `<p>`, or another tag).
9. In the **Styles** or **Computed** panel, verify the following CSS properties on the `<h2>` element:
	- `font-family`
	- `font-size`
	- `font-weight`
	- `line-height`
	- `color`
10. Confirm that the typography styles originate from or match the expected design tokens:
	- `--font-size-h-2`
	- `--font-weight-semi`
	- `--color-text`
11. Visually inspect the heading at desktop width for any spacing, clipping, or layout issues.

---

## Expected Result

- The component renders a semantic heading element:
	- `<h2>…</h2>`
- `font-family` = inherit from (_Inter_) or **Inter**
- `font-size` = **1.5rem** for desktop, sourced from token `--font-size-h-2`
- `font-weight` = **600**, mapped from token `--font-weight-semi`
- `line-height` = **normal** (or browser-resolved equivalent)
- In **Light theme**:
	- `color` = `#0f172a` equals the resolved value of **`--color-text`**
- No unexpected spacing, clipping, overlaps, or rendering artifacts at desktop viewport widths

---

## Screenshots / Attachments (optional)

- Screenshot of `H2` rendering on Desktop + Light theme at ≥1280px width (showing default or example heading text)

![alt text](../../assets/image-31.png)

---

## Edge Cases

*(Not required for pass/fail, but recommended to observe)*
- Test long heading text that wraps to multiple lines and verify line-height and spacing remain visually consistent.
- Verify that global theme toggling Light → Dark → Light correctly updates `--color-text` for H2 (even though this test focuses on Light theme, brief Dark check can reveal token wiring issues).

---

## Notes

- This test case covers only **Desktop (≥1280px) + Light theme** for the `H2` component.
- Separate test cases should cover Dark theme and Tablet/Mobile breakpoints.
- Typography expectations must match the `H2` specification in MC-0004.

---

## Related

- Ticket: [MC-0004-UI-kit-Create-H2-component](../../../tickets/Story/MC-0004-UI-kit-Create-H2-component.md)
