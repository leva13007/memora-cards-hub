---
id: TC-MC-0003
title: "UI-kit: TextBold – Tablet – Light Theme – Typography Tokens"
type: UI
priority: Medium
area: "ui-kit/typography"
component: "TextBold"
related-ticket: "MC-0001-UI-kit-Create-Text-component"
status: Active
created: 2025-12-09
updated: 2025-12-09
---

# TC-MC-0003 — UI: TextBold – Tablet – Light Theme – Typography Tokens

## Objective

Validate that the `TextBold` UI component renders correctly on **Tablet** viewport in **Light theme**, using the expected typography design tokens and computed styles defined in ticket  
[MC-0001-UI-kit-Create-Text-component](../tickets/MC-0001-UI-kit-Create-Text-component.md).

Specifically confirm on tablet range (768–1192px):

- correct font family
- correct tablet font size from token `--fonts-size-text`
- correct font-weight via `--font-weight-semi`
- correct text color (`--color-text`)
- correct line-height
- no visual or spacing inconsistencies

---

## Preconditions

- Application or Storybook is running.
- The `TextBold` component is available (e.g., via Storybook story `UI / Atoms / TextBold`).
- Browser viewport width is within **tablet range 768–1192px**.
- Application theme is set to **Light**.
- Design tokens are loaded:
	- `--color-text`
	- `--fonts-size-text`
	- `--font-weight-semi`
- Browser devtools are available to inspect computed styles.

---

## Test Data

_Static UI verification; no dynamic data required._

Environment assumptions:

| Parameter      | Value                    |
|----------------|--------------------------|
| Device         | Tablet (simulated)       |
| Viewport       | 768–1192px               |
| Theme          | Light                    |
| Browser        | Latest Chrome / Chromium |

Recommended specific widths:

| Scenario       | Width (px) |
|----------------|------------|
| Tablet check   | 1024       |

---

## Steps

1. Open Storybook or the application in a desktop browser.
2. Set viewport width to a tablet value within **768–1192px** (for example, **1024px**).
3. Ensure the **Light** theme is active.
4. Navigate to the [page](https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-textbold--default&viewMode=story) or [Storybook story](https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-textbold--docs) that showcases the `TextBold` component (`UI / Atoms / TextBold`).
5. Identify a sample `TextBold` text element (e.g., “Sample Bold Text”).
6. Open browser devtools and inspect the element.
7. In the **Styles** or **Computed** panel, verify the following CSS properties:
	 - `font-family`
	 - `font-size`
	 - `font-weight`
	 - `line-height`
	 - `color`
8. Confirm that the styles originate from or match the expected design tokens:
	 - `--fonts-size-text`
	 - `--font-weight-semi`
	 - `--color-text`

---

## Expected Result

- `font-family` = inherit from (_Inter_) or **Inter**
- `font-size` = **0.875rem (14px)** for tablet, sourced from `--fonts-size-text`
- `font-weight` = **600**, mapped from token `--font-weight-semi`
- `line-height` = **normal** (or browser-resolved equivalent)
- `color` equals the resolved value of **`--color-text`** for **Light theme** (`#0f172a`)
- No unexpected spacing, clipping, overlaps, or rendering artifacts

---

## Screenshots / Attachments (optional)

- Screenshot of component rendering on Tablet + Light theme at ~1024px width

![alt text](./assets/image-2.png)

---

## Edge Cases  
*(Not required for pass/fail, but recommended to observe)*

- Move viewport just below and above the tablet range:
	- **≤767px** (mobile) should use `0.75rem` font-size
	- **≥1193px** (desktop) should use `1rem` font-size
- Toggle Light → Dark → Light and verify color token re-evaluates correctly back to Light theme value.
- Test long text wrapping to ensure no layout shifts at tablet width.

---

## Notes

- This test case covers only **Tablet (768–1192px) + Light theme**.
- Complementary test cases cover Desktop and Dark theme variants.

---

## Related

- Ticket: [MC-0001](../tickets/MC-0001-UI-kit-Create-Text-component.md)
- Related test cases:
	- [TC-MC-0001 – TextBold – Desktop – Light Theme](./TC-MC-0001-UI-TextBold-Desktop-LightTheme.md)
	- [TC-MC-0002 – TextBold – Desktop – Dark Theme](./TC-MC-0002-UI-TextBold-Desktop-DarkTheme.md)
	- (future) Tablet / Mobile + Dark theme

