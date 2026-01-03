---
id: MC-0005
title: "UI-kit: Create Container component"
type: Story            # Epic | Feature | Story | Task | Spike | Chore | Improvement
status: In testing           # ToDo | Sprint ready | In Progress | In Review | Ready for testing | In testing | Issue found | Blocked | Done
priority: Medium       # Low | Medium | High | Critical
area: "ui-kit"  # ui-kit | backend | infra
author: "Oleh Levchenko"
assignee: ""
estimated: 5            # in story points
created: 2025-12-12
updated: 2025-12-12
started: 2025-12-12
ended: 2025-12-12
sprint-id: MC-0001-Sprint-01
labels: ["frontend"]             # free-form tags (optional)
---

# MC-0005 — UI-kit: Create Container component

## Description (required)

As a developer I want to have a **Container** layout component in the UI kit that wraps page content in a centered, responsive column with consistent horizontal padding, so that pages and sections can share a common layout skeleton across Desktop, Tablet, and Mobile.

The **Container** component should:
- Render a semantic HTML `<div>` wrapper element.
- Center itself within the viewport using automatic horizontal margins.
- Apply consistent horizontal padding.
- Use breakpoint-specific width behavior defined by design.
- Use fluid width behavior at any breakpoint when `fluid` is enabled.
- Support a `fluid` prop to make the container 100% wide at any breakpoint.

## Design References (source of truth)

- Breakpoints:
  - [Breakpoints](../../design/foundations/breakpoints.md)
- Tokens:
	- [Container tokens](../../design/foundations/tokens.md#container)
- Container design spec:
	- [DE-0001-Container](../../design/design/DE-0001-container.md)

## Acceptance Criteria / Definition of Done (required)

1. Renders a semantic `<div>` root element.
2. Container ensures horizontal centering according to design references.
3. Container applies horizontal spacing defined by layout tokens.
4. When `fluid` is omitted/`false`, width behavior matches `design/design/DE-0001-container.md` across Mobile/Tablet/Desktop.
5. When `fluid` is `true`, the container is full width at all breakpoints.
6. Component is available in Storybook under `UI / Atoms / Container`.

## Test Coverage  
(Manual or auto-generated)

- Related test cases:
	- [TC-MC-0037-UI-Container-Desktop](../../qa_test-cases/UI/Container/TC-MC-0037-UI-Container-Desktop.md)
	- [TC-MC-0038-UI-Container-Tablet](../../qa_test-cases/UI/Container/TC-MC-0038-UI-Container-Tablet.md)
	- [TC-MC-0039-UI-Container-Mobile](../../qa_test-cases/UI/Container/TC-MC-0039-UI-Container-Mobile.md)
	- [TC-MC-0040-UI-Container-Fluid](../../qa_test-cases/UI/Container/TC-MC-0040-UI-Container-Fluid.md)

## Related

- Depends on:
- Blocks:
- Duplicate of:
- Additional Links:
  - Storybook references for Container:
    - Storybook docs page:  
    	`https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-container--docs`
    - Default story (element view):  
    	`https://leva13007.github.io/memora-cards-storybook/?path=/story/ui-atoms-container--default`

## Sprint

- [Sprint 01](../sprints/MC-0001-Sprint-01.md)
