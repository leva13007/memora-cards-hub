---
id: MC-0002-Sprint-02
title: Sprint 02
start-date: 2026-02-03
end-date: 2026-02-28
---

# Sprint 02

## Goals
Deliver the remaining UI-kit building blocks required for Cards: the shared Icon atom plus Buttons, TextInput, and TextArea components. This sprint focuses on implementing the specs from DE-0007 / DE-0008 / DE-0009 / DE-0010, wiring token-driven states (hover, focus-visible, disabled), documenting Storybook usage, and ensuring accessibility coverage before integrating these atoms/molecules downstream.

---

## Scope

### In Scope
- Icon atom with curated glyph set and size/tone controls.
- Button atom with primary/warning/secondary variants and optional leading icon.
- TextInput atom with label/helper/error handling and validation states.
- TextArea atom with multiline behavior, 3-row default, and resize restrictions.

### Out of Scope
- Consuming these components inside application flows.
- Advanced patterns (auto-grow text areas, icon-only button variants beyond documented scope).

---

## Tickets list
- [MC-0007: UI-kit: Create Icon components](../tickets/Story/MC-0007-UI-kit-Create-Icon-components.md)
- [MC-0008: UI-kit: Create Buttons component](../tickets/Story/MC-0008-UI-kit-Create-Buttons-components.md)
- [MC-0009: UI-kit: Create TextInput component](../tickets/Story/MC-0009-UI-kit-Create-TextInput-components.md)
- [MC-0010: UI-kit: Create TextArea component](../tickets/Story/MC-0010-UI-kit-Create-TextArea-components.md)

---

## Sprint QA Report
- [SR-MC-0002-Sprint-02: QA Sprint Report for Sprint 02](../qa_sprint_report/SR-MC-0002-Sprint-02.md)

---

## Notes
- Coordinate token changes with `design/foundations/tokens.md` before landing component code.
- Storybook stories for all four components are required prior to QA sign-off.
