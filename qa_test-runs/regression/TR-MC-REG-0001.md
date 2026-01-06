---
id: TR-MC-REG-0001
title: "Sprint 01: UI-kit regression verification — Storybook manual run"
type: Regression        # Regression | Smoke | UI | E2E | Performance | Custom
scope: "ui-kit"
created: 2026-01-06
owner: "Oleh Levchenko"
environment: "storybook"         # local | dev | staging | production | storybook
status: Planned         # Planned | In Progress | Completed | Canceled
related-tickets:
	- MC-0001-UI-kit-Create-Text-component
	- MC-0002-UI-kit-Create-TextLink-component
	- MC-0003-UI-kit-Create-H1-component
	- MC-0004-UI-kit-Create-H2-component
	- MC-0005-UI-kit-Create-Container-component
	- MC-0006-UI-kit-Create-Breadcrumbs-component
---

# TR-MC-REG-0001 — Sprint 01: UI-kit regression verification — Storybook manual run

## Purpose
Fast, repeatable regression check for Sprint 01 UI-kit components in Storybook.
Focuses on the highest-risk surface area: theme correctness, core rendering/semantics, and required accessibility behavior.

## Scope
### In Scope
- Components:
	- `TextLight`, `TextMedium`, `TextBold` (MC-0001)
	- `TextLink` (MC-0002)
	- `H1` (MC-0003)
	- `H2` (MC-0004)
	- `Container` (MC-0005)
	- `Breadcrumbs` (MC-0006)
- Themes:
	- Light
	- Dark
- Breakpoints:
	- Desktop (primary)
	- Tablet (for `TextMedium` only)
	- Mobile (for `TextMedium` only)

### Out of Scope
- Full breakpoint matrix (Tablet/Mobile) — covered by the full run `qa_test-runs/full/TR-MC-0001.md`
- Cross-browser testing
- App-level routing/integration
- Performance profiling

## Preconditions
- Storybook is available and includes stories for all components listed above.
- Theme switcher is available (or Storybook provides theme toggle via toolbar).
- Browser devtools are available (DOM inspection + computed styles + accessibility tree).

## Test Suite

| Test Case ID | Title | Priority |
|-------------------------------------------------------------------------------------------------|-------------------------------------------------|--------|
| [TC-MC-0001](../../qa_test-cases/UI/TextBold/TC-MC-0001-UI-TextBold-Desktop-LightTheme.md)			| UI: TextBold — Desktop — Light Theme						| Medium |
| [TC-MC-0002](../../qa_test-cases/UI/TextBold/TC-MC-0002-UI-TextBold-Desktop-DarkTheme.md)				| UI: TextBold — Desktop — Dark Theme							| Medium |
| [TC-MC-0007](../../qa_test-cases/UI/TextMedium/TC-MC-0007-UI-TextMedium-Desktop-LightTheme.md)	| UI: TextMedium — Desktop — Light Theme					| Medium |
| [TC-MC-0008](../../qa_test-cases/UI/TextMedium/TC-MC-0008-UI-TextMedium-Desktop-DarkTheme.md)		| UI: TextMedium — Desktop — Dark Theme						| Medium |
| [TC-MC-0009](../qa_test-cases/UI/TextMedium/TC-MC-0009-UI-TextMedium-Tablet-LightTheme.md)			| UI: TextMedium — Tablet — Light Theme						| Medium |
| [TC-MC-0011](../qa_test-cases/UI/TextMedium/TC-MC-0011-UI-TextMedium-Mobile-LightTheme.md)			| UI: TextMedium — Mobile — Light Theme						| Medium |
| [TC-MC-0013](../../qa_test-cases/UI/TextLight/TC-MC-0013-UI-TextLight-Desktop-LightTheme.md)		| UI: TextLight — Desktop — Light Theme						| Medium |
| [TC-MC-0014](../../qa_test-cases/UI/TextLight/TC-MC-0014-UI-TextLight-Desktop-DarkTheme.md)			| UI: TextLight — Desktop — Dark Theme						| Medium |
| [TC-MC-0019](../../qa_test-cases/UI/TextLink/TC-MC-0019-UI-TextLink-Desktop-LightTheme.md)			| UI: TextLink — Desktop — Light Theme						| Medium |
| [TC-MC-0020](../../qa_test-cases/UI/TextLink/TC-MC-0020-UI-TextLink-Desktop-DarkTheme.md)				| UI: TextLink — Desktop — Dark Theme							| Medium |
| [TC-MC-0044](../../qa_test-cases/UI/TextLink/TC-MC-0044-UI-TextLink-accessibility.md)						| UI: TextLink — Accessibility (keyboard focus)		| High	|
| [TC-MC-0025](../../qa_test-cases/UI/H1/TC-MC-0025-UI-H1-Desktop-LightTheme.md)									| UI: H1 — Desktop — Light Theme									| Medium |
| [TC-MC-0026](../../qa_test-cases/UI/H1/TC-MC-0026-UI-H1-Desktop-DarkTheme.md)										| UI: H1 — Desktop — Dark Theme										| Medium |
| [TC-MC-0031](../../qa_test-cases/UI/H2/TC-MC-0031-UI-H2-Desktop-LightTheme.md)									| UI: H2 — Desktop — Light Theme									| Medium |
| [TC-MC-0032](../../qa_test-cases/UI/H2/TC-MC-0032-UI-H2-Desktop-DarkTheme.md)										| UI: H2 — Desktop — Dark Theme										| Medium |
| [TC-MC-0037](../../qa_test-cases/UI/Container/TC-MC-0037-UI-Container-Desktop.md)								| UI: Container — Desktop													| Medium |
| [TC-MC-0040](../../qa_test-cases/UI/Container/TC-MC-0040-UI-Container-Fluid.md)									| UI: Container — Fluid														| Medium |
| [TC-MC-0041](../../qa_test-cases/UI/Breadcrumbs/TC-MC-0041-UI-Breadcrumbs-composition-rules.md)	| UI: Breadcrumbs — Composition rules (links vs text) | Medium |
| [TC-MC-0042](../../qa_test-cases/UI/Breadcrumbs/TC-MC-0042-UI-Breadcrumbs-separators.md)				| UI: Breadcrumbs — Separators										| Medium |
| [TC-MC-0043](../../qa_test-cases/UI/Breadcrumbs/TC-MC-0043-UI-Breadcrumbs-accessibility-and-semantics.md) | UI: Breadcrumbs — Accessibility & semantics | High |

## Related Materials
- Full run (breakpoints/themes matrix):
	- [TR-MC-0001](../full/TR-MC-0001.md)
- Tickets:
	- [MC-0001](../../tickets/MC-0001-UI-kit-Create-Text-component.md)
	- [MC-0002](../../tickets/MC-0002-UI-kit-Create-TextLink-component.md)
	- [MC-0003](../../tickets/MC-0003-UI-kit-Create-H1-component.md)
	- [MC-0004](../../tickets/MC-0004-UI-kit-Create-H2-component.md)
	- [MC-0005](../../tickets/MC-0005-UI-kit-Create-Container-component.md)
	- [MC-0006](../../tickets/MC-0006-UI-kit-Create-Breadcrumbs-component.md)

## Entry Criteria
- Ticket implementation is complete.
- Storybook builds successfully.
- No known blocking issues related to the components under test.

## Exit Criteria
- All listed test cases are executed.
- No **Critical** or **High** severity issues are open.
- Any discovered issues are logged as tickets and linked to this run.

## Notes
- N/A

## Executions
- (none yet)
