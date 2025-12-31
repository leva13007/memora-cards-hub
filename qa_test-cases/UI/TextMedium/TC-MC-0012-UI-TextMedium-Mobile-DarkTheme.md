---
id: TC-MC-0012
title: "UI-kit: TextMedium – Mobile – Dark Theme – Typography Tokens"
type: UI
priority: Medium
area: "ui-kit/typography"
component: "TextMedium"
related-ticket: "MC-0001-UI-kit-Create-Text-component"
status: Active
created: 2025-12-10
updated: 2025-12-10
---

# TC-MC-0012 — UI: TextMedium – Mobile – Dark Theme – Typography Tokens

## Objective

Validate that the `TextMedium` UI component renders correctly on **Mobile** viewport in **Dark theme**, using the expected typography design tokens and computed styles defined in ticket  
[MC-0001-UI-kit-Create-Text-component](../../../tickets/MC-0001-UI-kit-Create-Text-component.md).

Specifically confirm on mobile range (<768px):

- correct font family
- correct mobile font size from token `--fonts-size-text`
- correct font-weight via `--font-weight-normal`
- correct text color for **Dark** theme when `variant="primary"`
- correct behavior when `variant="warning"`
- correct default `as` prop (`<span>`) and optional `as="p"` behavior
- correct line-height
- no visual or spacing inconsistencies

---

## Preconditions

- Application or Storybook is running.
- The `TextMedium` component is available (e.g., via Storybook story `UI / Atoms / TextMedium`).
- Browser viewport width is within **mobile range < 768px**.
- Application theme is set to **Dark**.
- Design tokens are loaded:
	- `--color-text`
	- `--fonts-size-text`
	- `--font-weight-normal`
- Browser devtools are available to inspect computed styles.

---

## Test Data

_Static UI verification; no dynamic data required._

Environment assumptions:

| Parameter      | Value                    |
|----------------|--------------------------|
| Device         | Mobile (simulated)       |
| Viewport       | < 768px                  |
| Theme          | Dark                     |
| Browser        | Latest Chrome / Chromium |

Recommended specific widths:

| Scenario       | Width (px) |
|----------------|------------|
| Mobile check   | 375        |

---

## Steps

1. Open Storybook or the application in a desktop browser (or device emulator).
2. Set viewport width to a mobile value **< 768px** (for example, **375px**).
3. Ensure the **Dark** theme is active.
4. Navigate to the [page](https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-textmedium--default&viewMode=story&globals=theme:dark) or [Storybook story](https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-textmedium--docs) that showcases the `TextMedium` component (`UI / Atoms / TextMedium`).
5. Identify a sample `TextMedium` text element (e.g., "Sample Medium Text").
6. Open browser devtools and inspect the element.
7. In the **Styles** or **Computed** panel, verify the following CSS properties:
	- `font-family`
	- `font-size`
	- `font-weight`
	- `line-height`
	- `color`
8. Confirm that the styles originate from or match the expected design tokens:
	- `--fonts-size-text`
	- `--font-weight-normal`
	- `--color-text`

9. Toggle `variant` prop or visit the page with different variants:
	- Set `variant="primary"` or open the [page](https://leva13007.github.io/memora-cards-storybook/iframe.html?args=&id=ui-atoms-textmedium--primary&viewMode=story&globals=theme:dark) and verify color uses `--color-text`.
	- Set `variant="warning"` or open the [page](https://leva13007.github.io/memora-cards-storybook/iframe.html?globals=&args=&id=ui-atoms-textmedium--warning&viewMode=story&globals=theme:dark) and verify color uses `--color-warning`.

10. Toggle `as` prop or visit the page with different variants:
	- Without passing `as` or when `as="span"` or open the [page](https://leva13007.github.io/memora-cards-storybook/iframe.html?globals=&args=&id=ui-atoms-textmedium--span&viewMode=story&globals=theme:dark), verify the element is rendered as `<span>`.
	- Set `as="p"` or open the [page](https://leva13007.github.io/memora-cards-storybook/iframe.html?globals=&args=&id=ui-atoms-textmedium--paragraph&viewMode=story&globals=theme:dark), verify the element is rendered as `<p>`.
	- In both cases, confirm typography tokens (font-size, weight, line-height, variant color) remain correct.

---

## Expected Result

- `font-family` = inherit from (_Inter_) or **Inter**
- `font-size` = **0.75rem (12px)** for mobile, sourced from `--fonts-size-text`
- `font-weight` = **400**, mapped from token `--font-weight-normal`
- `line-height` = **normal** (or browser-resolved equivalent)
- When `variant="primary"`, `color` = `#f5f7fb` equals the resolved value of **`--color-text`** for **Dark theme**
- When `variant="warning"`, `color` = `#ec1515` equals the resolved value of **`--color-warning`** (for both Light and Dark themes)
- When `as` is not provided, the rendered element is `<span>`
- When `as="p"`, the rendered element is `<p>` and typography tokens remain unchanged
- No unexpected spacing, clipping, overlaps, or rendering artifacts

---

## Screenshots / Attachments (optional)

- Screenshot of component rendering on Mobile + Dark theme at ~375px width

![alt text](../../assets/image-12.png)

---

## Edge Cases

*(Not required for pass/fail, but recommended to observe)*

- Move viewport just below and above the mobile range:
	- Around **767px** to confirm tablet font-size **0.875rem** is applied
- Toggle Dark → Light → Dark and verify color token re-evaluates correctly for `variant="primary"` and does not affect `variant="warning"` using `--color-warning`.
- Test long text wrapping and multi-line content to ensure no layout shifts at small mobile widths.

---

## Notes

- This test case covers only **Mobile (<768px) + Dark theme** for the `TextMedium` component.
- Complementary test cases cover Tablet, Desktop, and Light theme variants.

---

## Related

- Ticket: [MC-0001-UI-kit-Create-Text-component](../../../tickets/MC-0001-UI-kit-Create-Text-component.md)
