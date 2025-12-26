---
id: TR-MC-0001-UI-kit-Text-components-verification
title: "UI-kit: Text components (Light/Medium/Bold) — Storybook manual run"
type: UI              # Regression | Smoke | UI | E2E | Performance | Custom
scope: "ui-kit"
created: 2025-12-22
owner: "Oleh Levchenko"
environment: "storybook"         # local | dev | staging | production | storybook
status: Planned         # Planned | In Progress | Completed | Canceled
related-tickets:
	- MC-0001-UI-kit-Create-Text-component
---

# TR-MC-0001 — UI Kit: Text component verification (Light/Medium/Bold) — Storybook manual run

## Purpose
Run a focused manual verification of the UI-kit Text typography components created in `MC-0001`:
- `TextLight`
- `TextMedium`
- `TextBold`

Validate responsive font sizes, theme colors, font-weight tokens, and core props behavior (`as`, `variant`).

---

## Scope

### In Scope
- `TextLight`, `TextMedium`, `TextBold` verification per `MC-0001` acceptance criteria
- Breakpoints:
	- Desktop ≥1280px
	- Tablet 768–1279px
	- Mobile <768px
- Themes:
	- Light
	- Dark
- Variants:
	- `primary` and `warning`
- `as` prop behavior (`span` default, `p` option)

### Out of Scope
- Cross-browser matrix (Safari/Firefox/etc.)
- Integration with other UI components.
- Full app-level integration (only UI-kit components / Storybook)
- Accessibility beyond basic semantic rendering.
- Performance profiling

---

## Preconditions
- Storybook is available and includes stories for:
	- `UI / TextBold`
	- `UI / TextMedium`
	- `UI / TextLight`
- Theme switcher is available (or Storybook provides theme toggle via toolbar).
- Browser devtools are available to inspect computed styles and tokens.

---

## Test Suite

| ID          | Title                                       | Priority |
|-------------|---------------------------------------------|----------|
| TC-MC-0001  | UI: TextBold — Desktop — Light Theme        | Medium   |
| TC-MC-0002  | UI: TextBold — Desktop — Dark Theme         | Medium   |
| TC-MC-0003  | UI: TextBold — Tablet — Light Theme         | Medium   |
| TC-MC-0004  | UI: TextBold — Tablet — Dark Theme          | Medium   |
| TC-MC-0005  | UI: TextBold — Mobile — Light Theme         | Medium   |
| TC-MC-0006  | UI: TextBold — Mobile — Dark Theme          | Medium   |
| TC-MC-0007  | UI: TextMedium — Desktop — Light Theme      | Medium   |
| TC-MC-0008  | UI: TextMedium — Desktop — Dark Theme       | Medium   |
| TC-MC-0009  | UI: TextMedium — Tablet — Light Theme       | Medium   |
| TC-MC-0010  | UI: TextMedium — Tablet — Dark Theme        | Medium   |
| TC-MC-0011  | UI: TextMedium — Mobile — Light Theme       | Medium   |
| TC-MC-0012  | UI: TextMedium — Mobile — Dark Theme        | Medium   |
| TC-MC-0013  | UI: TextLight — Desktop — Light Theme       | Medium   |
| TC-MC-0014  | UI: TextLight — Desktop — Dark Theme        | Medium   |
| TC-MC-0015  | UI: TextLight — Tablet — Light Theme        | Medium   |
| TC-MC-0016  | UI: TextLight — Tablet — Dark Theme         | Medium   |
| TC-MC-0017  | UI: TextLight — Mobile — Light Theme        | Medium   |
| TC-MC-0018  | UI: TextLight — Mobile — Dark Theme         | Medium   |
---

## Related Materials
- Ticket: [MC-0001: UI-kit: Create Text component (Light / Medium / Bold)](../tickets/MC-0001-UI-kit-Create-Text-component.md)

---

## Entry Criteria

- Ticket MC-0001 implementation is complete.
- Storybook builds successfully.
- No known blocking issues related to typography tokens.

---

## Exit Criteria

- All listed test cases are executed.
- No **Critical** or **High** severity issues are open.
- Any discovered issues are logged as tickets and linked to this run.

---

## Notes

---

## Executions
- [EX-MC-0001-2025-12-23: First execution of TR-MC-0001](../qa_executions/EX-MC-0001-2025-12-23.md)
