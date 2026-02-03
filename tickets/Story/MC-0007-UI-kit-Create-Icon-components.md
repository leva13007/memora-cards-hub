---
id: MC-0007
title: "UI-kit: Create Icon components"
type: Story            # Epic | Feature | Story | Task | Spike | Chore | Improvement
status: ToDo           # ToDo | Sprint ready | In Progress | In Review | Ready for testing | In testing | Issue found | Blocked | Done
priority: Medium       # Low | Medium | High | Critical
area: "ui-kit"  # ui-kit | backend | infra
author: "Oleh Levchenko"
assignee: ""
estimated: 5            # in story points
created: 2026-01-09
updated: 2026-01-09
started:               # YYYY-MM-DD
ended:                 # YYYY-MM-DD
sprint-id: MC-0001-Sprint-01
labels: ["frontend"]             # free-form tags (optional)
---

# MC-0007 — UI-kit: Create Icon components

## Description (required)

Introduce a reusable `Icon` atom (and associated SVG glyph exports) so product teams can render consistent pictograms that follow the visual + accessibility rules defined in [DE-0007-Icons](../../design/design/DE-0007-Icons.md).

Key goals:
- Ship an inline SVG based `Icon` component that accepts a finite `name` list (star, star-fill, bookmark, bookmark-fill, check-circle, x-circle, info-circle, alert-triangle) curated in the spec.
- Ensure icons inherit color via `currentColor`.
- Provide `aria-hidden`/`aria-label` handling so icons can be decorative by default but accessible when needed.
- Expose icons in Storybook (`UI / Atoms / Icon`) with controls for `name`.

## Design References (source of truth)

- Icon spec: [DE-0007-Icons](../../design/design/DE-0007-Icons.md)
- Tokens:
	- [design/foundations/tokens.md](../../design/foundations/tokens.md)
- Theme + colors:
	- [design/foundations/theme.md](../../design/foundations/theme.md)

## Acceptance Criteria / Definition of Done (required)

1. Provide an `Icon` component that renders inline SVG paths sourced from the curated glyph map defined in `DE-0007-Icons`;
2. SVG displays according to the glyph definition in `DE-0007-Icons`.
3. Storybook stories exist under `UI / Atoms / Icon`. Stories must load without console errors.

## Test Coverage  
(Manual or auto-generated)

- Related test cases:
	- ...

## Related  
- Depends on:
	- `DE-0007-Icons` approval (design handoff)
- Blocks:
	- Future icon consumers in cards/features that need consistent pictograms
- Duplicate of:
- Additional Links:
	- Storybook docs (planned): `https://leva13007.github.io/memora-cards-storybook/?path=/docs/ui-atoms-icon--docs`
	- Default story (iframe): `https://leva13007.github.io/memora-cards-storybook/iframe.html?id=ui-atoms-icon--default&viewMode=story`
	- Bootstrap Icons reference (source set): https://icons.getbootstrap.com/

## Sprint
- [Sprint 01](../../sprints/MC-0002-Sprint-02.md)

