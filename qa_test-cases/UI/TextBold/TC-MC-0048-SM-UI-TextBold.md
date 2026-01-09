---
id: TC-MC-0048-SM
title: "SM / UI: TextBold — Storybook page loads without errors"
type: Smoke              # UI | Functional | Integration | E2E | Regression | Smoke
priority: High           # Low | Medium | High | Critical
area: "ui-kit/typography"
component: "TextBold"
related-ticket: "MC-0001-UI-kit-Create-Text-component"
status: Active           # Active | Draft | Deprecated
created: 2026-01-06
updated: 2026-01-06
---

# TC-MC-0048-SM — SM / UI: TextBold — Storybook page loads without errors

## Objective
Quick smoke check that the `TextBold` Storybook story loads successfully and does not produce runtime errors.

## Preconditions
- Internet access is available.
- Browser is available (Chrome/Chromium recommended).
- DevTools can be opened to inspect Console.

## Test Data
N/A

## Steps
1. Open the TextBold Storybook story (iframe):
	- Story: [link](https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-textbold--default&viewMode=story)
2. Wait for the story to fully load.
3. Verify the page is not blank and the story content is rendered.
4. Open DevTools → Console.
5. Verify there are **no runtime errors** related to rendering the story (no red error stack traces).
6. Verify there is no Storybook error overlay / “Something went wrong” screen.

## Expected Result
- The Storybook iframe page loads successfully.
- The `TextBold` story renders content.
- No runtime errors are shown in the Console.
- No error overlay is shown.

## Screenshots / Attachments

![alt text](../../assets/image-1.png)

## Edge Cases
- Hard refresh the page (Cmd+Shift+R) and re-check that it still loads without errors.

## Notes
- This is a smoke test only; it does not validate typography tokens or variants.

## Related

- Ticket: [MC-0001-UI-kit-Create-Text-component](../../../tickets/Story/MC-0001-UI-kit-Create-Text-component.md)
