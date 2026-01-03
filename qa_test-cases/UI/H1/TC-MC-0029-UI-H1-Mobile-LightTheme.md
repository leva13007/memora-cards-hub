---
id: TC-MC-0029
title: "UI-kit: H1 – Mobile – Light Theme – Typography Tokens"
type: UI
priority: Medium
area: "ui-kit/typography"
component: "H1"
related-ticket: "MC-0003-UI-kit-Create-H1-component"
status: Active
created: 2025-12-11
updated: 2025-12-11
---

# TC-MC-0029 — UI: H1 – Mobile – Light Theme – Typography Tokens

## Objective

Validate that the `H1` UI component renders correctly on **Mobile** viewport in **Light theme**, using the expected typography design tokens and semantic `<h1>` behavior defined in ticket  
[MC-0003-UI-kit-Create-H1-component](../../../tickets/Story/MC-0003-UI-kit-Create-H1-component.md).

Specifically confirm on mobile range (<768px):

- correct `<h1>` semantics in the DOM
- correct font family (inheriting **Inter**)
- correct mobile font size from token `--font-size-h-1`
- correct font-weight via `--font-weight-bold`
- correct text color for **Light** theme via `--color-text`
- correct line-height
- no visual or spacing inconsistencies at small widths

---

## Preconditions

- Application or Storybook is running.
- The `H1` component is available (e.g., via Storybook story `UI / Atoms / H1`).
- Browser viewport width is within **mobile range <768px**.
- Application theme is set to **Light**.
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
| Device         | Mobile (simulated)       |
| Viewport       | < 768px                  |
| Theme          | Light                    |
| Browser        | Latest Chrome / Chromium |

Recommended specific widths:

| Scenario       | Width (px) |
|----------------|------------|
| Mobile check   | 375        |

---

## Steps

1. Open Storybook or the application in a desktop browser (or device emulator).
2. Set viewport width to a mobile value **<768px** (for example, **375px**).
3. Ensure the **Light** theme is active.
4. Navigate to the [H1 default story iframe](https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-h1--default&viewMode=story) or `H1` [Storybook docs page](https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-h1--docs) that showcases the `H1` component (`UI / Atoms / H1`).
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
11. Visually inspect the heading at mobile width for any spacing, wrapping, clipping, or layout issues.

---

## Expected Result

- The component renders a semantic heading element:
	- `<h1>…</h1>`
- `font-family` = inherit from (_Inter_) or **Inter**
- `font-size` = **1.5rem (Mobile)**, sourced from token `--font-size-h-1`
- `font-weight` = **700**, mapped from token `--font-weight-bold`
- `line-height` = **normal** (or browser-resolved equivalent)
- In **Light theme**:
	- `color` = `#0f172a` equals the resolved value of **`--color-text`**
- No unexpected spacing, clipping, overlaps, or rendering artifacts at mobile viewport widths

---

## Screenshots / Attachments (optional)

- Screenshot of `H1` rendering on Mobile + Light theme at ~375px width (showing default or example heading text)

![alt text](../../assets/image-29.png)

---

## Edge Cases

*(Not required for pass/fail, but recommended to observe)*

- Move viewport around the mobile breakpoint:
	- **≤767px** (mobile) should use `1.5rem` from `--font-size-h-1`
	- **≥768px** (tablet) should use `1.75rem` from `--font-size-h-1`
- Test long heading text that wraps to multiple lines at small mobile widths and verify line-height and spacing remain visually consistent.
- Verify that global theme toggling Light → Dark → Light correctly updates `--color-text` for H1 and does not break typography tokens.

---

## Notes

- This test case covers only **Mobile (<768px) + Light theme** for the `H1` component.
- Separate test cases should cover Dark theme and Desktop/Tablet breakpoints.
- Typography expectations must match the `H1` specification in MC-0003.

---

## Related

- Ticket: [MC-0003-UI-kit-Create-H1-component](../../../tickets/Story/MC-0003-UI-kit-Create-H1-component.md)
