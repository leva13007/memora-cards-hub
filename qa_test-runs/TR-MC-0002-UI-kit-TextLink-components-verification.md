---
id: TR-2025-12-22-03
title: "UI-kit: TextLink component verification"
type: UI              # Regression | Smoke | UI | E2E | Performance | Custom
scope: "ui-kit"
created: 2025-12-22
owner: "Oleh Levchenko"
environment: "storybook"         # local | dev | staging | production | storybook
status: Planned         # Planned | In Progress | Completed | Canceled
related-tickets:
	- MC-0002
---

# TR-2025-12-22-03 — UI-kit: TextLink component verification

## Purpose
Validate `TextLink` UI-kit component behavior and styling across breakpoints and themes, and confirm the keyboard accessibility focus indicator (`:focus-visible`) required by `MC-0002`.

---

## Scope

### In Scope
- `TextLink` rendering and `to` → `href` mapping (Storybook-safe behavior)
- Typography/link tokens validation via existing theme/breakpoint TCs
- Link hover behavior (token `--color-link-hover`)
- Accessibility:
	- focus-visible outline `.link:focus-visible { outline: 1px solid var(--color-link, currentColor); }`
	- keyboard reachability (Tab)
- Breakpoints:
	- Desktop ≥1280px
	- Tablet 768–1279px
	- Mobile <768px
- Themes:
	- Light
	- Dark

### Out of Scope
- Full cross-browser validation
- App-level routing behavior (Storybook navigation should be disabled)
- Visual regression tooling

---

## Preconditions
- Storybook is available:
	- Docs: https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-textlink--docs
	- Story: https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-textlink--default&viewMode=story
- Theme switcher is available (or equivalent Storybook control).
- Browser devtools available for computed styles and focus inspection.

---

## Test Suite

| ID          | Title                                               | Priority |
|-------------|-----------------------------------------------------|----------|
| TC-MC-0019  | UI: TextLink — Desktop — Light Theme                | Medium   |
| TC-MC-0020  | UI: TextLink — Desktop — Dark Theme                 | Medium   |
| TC-MC-0021  | UI: TextLink — Tablet — Light Theme                 | Medium   |
| TC-MC-0022  | UI: TextLink — Tablet — Dark Theme                  | Medium   |
| TC-MC-0023  | UI: TextLink — Mobile — Light Theme                 | Medium   |
| TC-MC-0024  | UI: TextLink — Mobile — Dark Theme                  | Medium   |
| TC-MC-0044  | UI: TextLink — Accessibility (keyboard focus)       | High     |

---

## Related Materials
- Ticket: `tickets/MC-0002-UI-kit-Create-TextLink-component.md`

---

## Notes
- If a failure is found, open a bug ticket and reference `TR-2025-12-22-03`.

---

## Executions
- (pending)
