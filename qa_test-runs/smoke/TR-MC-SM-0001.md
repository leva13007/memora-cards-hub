---
id: TR-MC-SM-0001
title: "Sprint 01: UI-kit smoke — Storybook availability check"
type: Smoke             # Regression | Smoke | UI | E2E | Performance | Custom
scope: "ui-kit"
created: 2026-01-06
owner: "Oleh Levchenko"
environment: "storybook"        # local | dev | staging | production | storybook
status: Planned          # Planned | In Progress | Completed | Canceled
related-tickets:
	- MC-0001-UI-kit-Create-Text-component
	- MC-0002-UI-kit-Create-TextLink-component
	- MC-0003-UI-kit-Create-H1-component
	- MC-0004-UI-kit-Create-H2-component
	- MC-0005-UI-kit-Create-Container-component
	- MC-0006-UI-kit-Create-Breadcrumbs-component
---

# TR-MC-SM-0001 — Sprint 01: UI-kit smoke — Storybook availability check

## Purpose
Confirm that every Sprint 01 UI-kit story opens in Storybook without blank screens, runtime console errors, or error overlays. This run acts as a quick guardrail after deployments or Storybook rebuilds.

## Scope
### In Scope
- Smoke-level load validation for default stories of:
	- `Container`
	- `H1`
	- `H2`
	- `TextBold`
	- `TextLight`
	- `TextMedium`
	- `TextLink`
	- `Breadcrumbs`
- Desktop viewport in Light theme (Storybook default)

### Out of Scope
- Token, layout, accessibility, and theme matrix validation (covered by regression/full runs)
- Tablet/Mobile breakpoints
- Dark theme rendering specifics

## Preconditions
- Storybook deployment `https://leva13007.github.io/memora-cards-storybook` is reachable.
- Network connection is stable; browser (Chrome/Chromium) available.
- DevTools Console can be opened to observe runtime errors.

## Test Suite

| Test Case ID | Title | Priority |
|---------------------------------------------------------------------------------------|---------------------------------------------------------------|----------|
| [TC-MC-0045-SM](../../qa_test-cases/UI/Container/TC-MC-0045-SM-UI-Container.md)   | SM / UI: Container — Storybook page loads without errors     | High     |
| [TC-MC-0046-SM](../../qa_test-cases/UI/H1/TC-MC-0046-SM-UI-H1.md)                 | SM / UI: H1 — Storybook page loads without errors            | High     |
| [TC-MC-0047-SM](../../qa_test-cases/UI/H2/TC-MC-0047-SM-UI-H2.md)                 | SM / UI: H2 — Storybook page loads without errors            | High     |
| [TC-MC-0048-SM](../../qa_test-cases/UI/TextBold/TC-MC-0048-SM-UI-TextBold.md)     | SM / UI: TextBold — Storybook page loads without errors      | High     |
| [TC-MC-0049-SM](../../qa_test-cases/UI/TextLight/TC-MC-0049-SM-UI-TextLight.md)   | SM / UI: TextLight — Storybook page loads without errors     | High     |
| [TC-MC-0050-SM](../../qa_test-cases/UI/TextLink/TC-MC-0050-SM-UI-TextLink.md)     | SM / UI: TextLink — Storybook page loads without errors      | High     |
| [TC-MC-0051-SM](../../qa_test-cases/UI/TextMedium/TC-MC-0051-SM-UI-TextMedium.md) | SM / UI: TextMedium — Storybook page loads without errors    | High     |
| [TC-MC-0052-SM](../../qa_test-cases/UI/Breadcrumbs/TC-MC-0052-SM-UI-Breadcrumbs.md) | SM / UI: Breadcrumbs — Storybook page loads without errors | High     |

## Related Materials
- Regression reference: [TR-MC-REG-0001](../regression/TR-MC-REG-0001.md)
- Component tickets:
	- [MC-0001](../../tickets/Story/MC-0001-UI-kit-Create-Text-component.md)
	- [MC-0002](../../tickets/Story/MC-0002-UI-kit-Create-TextLink-component.md)
	- [MC-0003](../../tickets/Story/MC-0003-UI-kit-Create-H1-component.md)
	- [MC-0004](../../tickets/Story/MC-0004-UI-kit-Create-H2-component.md)
	- [MC-0005](../../tickets/Story/MC-0005-UI-kit-Create-Container-component.md)
	- [MC-0006](../../tickets/Story/MC-0006-UI-kit-Create-Breadcrumbs-component.md)

## Entry Criteria
- Latest UI-kit tickets are merged and Storybook build succeeds.
- No open blockers impacting Storybook availability.
- Test environment URL matches the links referenced in each smoke test case.

## Exit Criteria
- All smoke test cases executed at least once.
- No Critical/High severity issues remain open; any findings logged with links to this run.

## Notes
- Intended to run before/after each Storybook publish or when a dependency update lands.

## Executions
- (none yet)

