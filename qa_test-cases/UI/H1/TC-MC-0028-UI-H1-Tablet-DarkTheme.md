---
id: TC-MC-0028
title: "UI-kit: H1 – Tablet – Dark Theme – Typography Tokens"
type: UI
priority: Medium
area: "ui-kit/typography"
component: "H1"
related-ticket: "MC-0003-UI-kit-Create-H1-component"
status: Active
created: 2025-12-10
updated: 2025-12-10
---

# TC-MC-0028 — UI: H1 – Tablet – Dark Theme – Typography Tokens

## Objective

Validate that the `H1` UI component renders correctly on **Tablet** viewport in **Dark theme**, using the expected typography design tokens and semantic `<h1>` behavior defined in ticket  
[MC-0003-UI-kit-Create-H1-component](../../../tickets/Story/MC-0003-UI-kit-Create-H1-component.md).

Specifically confirm on tablet range (768–1279px):

- correct `<h1>` semantics in the DOM
- correct font family (inheriting **Inter**)
- correct tablet font size from token `--font-size-h-1`
- correct font-weight via `--font-weight-bold`
- correct text color for **Dark** theme via `--color-text`
- correct line-height
- no visual or spacing inconsistencies

---

## Preconditions

- Application or Storybook is running.
- The `H1` component is available (e.g., via Storybook story `UI / Atoms / H1`).
- Browser viewport width is within **tablet range 768–1279px**.
- Application theme is set to **Dark**.
- Design tokens are loaded:
	- `--color-text`
	- `--font-size-h-1`
	- `--font-weight-bold`
- Browser devtools are available to inspect computed styles.

---

## Test Data

_Static UI verification; no dynamic data required._

Environment assumptions:

| Parameter      | Value                    |
|----------------|--------------------------|
| Device         | Tablet (simulated)       |
| Viewport       | 768–1279px               |
| Theme          | Dark                     |
| Browser        | Latest Chrome / Chromium |

Recommended specific widths:

| Scenario       | Width (px) |
|----------------|------------|
| Tablet check   | 1024       |

---

## Steps

1. Open Storybook or the application in a desktop browser.
2. Set viewport width to a tablet value within **768–1279px** (for example, **1024px**).
3. Ensure the **Dark** theme is active.
4. Navigate to the [H1 default story iframe (Dark theme)](https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-h1--default&viewMode=story&globals=theme:dark) or `H1` [Storybook docs page](https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-h1--docs) that showcases the `H1` component (`UI / Atoms / H1`).
5. If the story supports controls/args for content, set the heading text to a simple value (for example, `"Dashboard"`). Otherwise, use the default example text shown in the story.
6. Identify a rendered `H1` element in the canvas area.
7. Open browser devtools and inspect the heading element.
8. In the **Elements** panel, verify that the rendered element is a semantic `<h1>` (not `<span>`, `<p>`, or another tag).
9. In the **Styles** or **Computed** panel, verify the following CSS properties on the `<h1>` element:
	- `font-family`
	- `font-size`
	- `font-weight`
	- `line-height`
	- `color`
10. Confirm that the typography styles originate from or match the expected design tokens:
	- `--font-size-h-1`
	- `--font-weight-bold`
	- `--color-text`
11. Visually inspect the heading at tablet width for any spacing, clipping, or layout issues.

---

## Expected Result

- The component renders a semantic heading element:
	- `<h1>…</h1>`
- `font-family` = inherit from (_Inter_) or **Inter**
- `font-size` = **1.75rem (Tablet)**, sourced from token `--font-size-h-1`
- `font-weight` = **700**, mapped from token `--font-weight-bold`
- `line-height` = **normal** (or browser-resolved equivalent)
- In **Dark theme**:
	- `color` = `#f5f7fb` equals the resolved value of **`--color-text`**
- No unexpected spacing, clipping, overlaps, or rendering artifacts at tablet viewport widths

---

## Screenshots / Attachments (optional)

- Screenshot of `H1` rendering on Tablet + Dark theme at ~1024px width (showing default or example heading text)

![alt text](../../assets/image-28.png)

---

## Edge Cases

*(Not required for pass/fail, but recommended to observe)*

- Move viewport just below and above the tablet range:
	- **≤767px** (mobile) should use `1.5rem` from `--font-size-h-1`
	- **≥1280px** (desktop) should use `2rem` from `--font-size-h-1`
- Test long heading text that wraps to multiple lines and verify line-height and spacing remain visually consistent at tablet width.
- Verify that global theme toggling Dark → Light → Dark correctly updates `--color-text` for H1 and does not break typography tokens.

---

## Notes

- This test case covers only **Tablet (768–1279px) + Dark theme** for the `H1` component.
- Separate test cases should cover Light theme and Desktop/Mobile breakpoints.
- Typography expectations must match the `H1` specification in MC-0003.

---

## Related

- Ticket: [MC-0003-UI-kit-Create-H1-component](../../../tickets/Story/MC-0003-UI-kit-Create-H1-component.md)
