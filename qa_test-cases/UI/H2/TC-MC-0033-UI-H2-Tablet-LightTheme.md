---
id: TC-MC-0033
title: "UI-kit: H2 – Tablet – Light Theme – Typography Tokens"
type: UI
priority: Medium
area: "ui-kit/typography"
component: "H2"
related-ticket: "MC-0004-UI-kit-Create-H2-component"
status: Active
created: 2025-12-11
updated: 2025-12-11
---

# TC-MC-0033 — UI: H2 – Tablet – Light Theme – Typography Tokens

## Objective

Validate that the `H2` UI component renders correctly on **Tablet** viewport in **Light theme**, using the expected typography design tokens and semantic `<h2>` behavior defined in ticket  
[MC-0004-UI-kit-Create-H2-component](../../../tickets/MC-0004-UI-kit-Create-H2-component.md).

Specifically confirm on tablet range (768–1279px):

- correct `<h2>` semantics in the DOM
- correct font family (inheriting **Inter**)
- correct tablet font size from token `--font-size-h-2`
- correct font-weight via `--font-weight-semi`
- correct text color for **Light** theme via `--color-text`
- correct line-height
- no visual or spacing inconsistencies

---

## Preconditions

- Application or Storybook is running.
- The `H2` component is available (e.g., via Storybook story `UI / Atoms / H2`).
- Browser viewport width is within **tablet range 768–1279px**.
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
| Device         | Tablet (simulated)       |
| Viewport       | 768–1279px               |
| Theme          | Light                    |
| Browser        | Latest Chrome / Chromium |

Recommended specific widths:

| Scenario       | Width (px) |
|----------------|------------|
| Tablet check   | 1024       |

---

## Steps

1. Open Storybook or the application in a desktop browser.
2. Set viewport width to a tablet value within **768–1279px** (for example, **1024px**).
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
11. Visually inspect the heading at tablet width for any spacing, clipping, or layout issues.

---

## Expected Result

- The component renders a semantic heading element:
	- `<h2>…</h2>`
- `font-family` = inherit from (_Inter_) or **Inter**
- `font-size` = **1.25rem (Tablet)**, sourced from token `--font-size-h-2`
- `font-weight` = **600**, mapped from token `--font-weight-semi`
- `line-height` = **normal** (or browser-resolved equivalent)
- In **Light theme**:
	- `color` = `#0f172a` equals the resolved value of **`--color-text`**
- No unexpected spacing, clipping, overlaps, or rendering artifacts at tablet viewport widths

---

## Screenshots / Attachments (optional)

- Screenshot of `H2` rendering on Tablet + Light theme at ~1024px width (showing default or example heading text)

![alt text](../../assets/image-33.png)

---

## Edge Cases  
*(Not required for pass/fail, but recommended to observe)*

- Move viewport just below and above the tablet range:
	- **≤767px** (mobile) should use `1.125rem` from `--font-size-h-2`
	- **≥1280px** (desktop) should use `1.5rem` from `--font-size-h-2`
- Test long heading text that wraps to multiple lines and verify line-height and spacing remain visually consistent at tablet width.
- Verify that global theme toggling Light → Dark → Light correctly updates `--color-text` for H2 (even though this test focuses on Light theme, brief Dark check can reveal token wiring issues).

---

## Notes

- This test case covers only **Tablet (768–1279px) + Light theme** for the `H2` component.
- Separate test cases should cover Dark theme and Desktop/Mobile breakpoints.
- Typography expectations must match the `H2` specification in MC-0004.

---

## Related

- Ticket: [MC-0004](../../../tickets/MC-0004-UI-kit-Create-H2-component.md)
- Related test cases (planned or existing):
	- [TC-MC-0031 – H2 – Desktop – Light Theme](./TC-MC-0031-UI-H2-Desktop-LightTheme.md)
	- (future) H2 – Tablet – Dark Theme
	- (future) H2 – Mobile – Light/Dark Theme
	- [TC-MC-0009 – TextMedium – Tablet – Light Theme](../TextMedium/TC-MC-0009-UI-TextMedium-Tablet-LightTheme.md)
	- [TC-MC-0021 – TextLink – Tablet – Light Theme](../TextLink/TC-MC-0021-UI-TextLink-Tablet-LightTheme.md)
