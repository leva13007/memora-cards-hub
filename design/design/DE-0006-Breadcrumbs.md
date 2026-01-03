
# Breadcrumbs — Design Reference

## 1. Purpose
Define the composition, semantics, and accessibility rules for the `Breadcrumbs` UI-kit molecule so navigation trails are consistent across themes and breakpoints.

## 2. Scope
Applies to the `Breadcrumbs` molecule only.
Does not define routing behavior, URL construction, truncation, or single-line ellipsis behavior.

## 3. Terminology
- Breadcrumbs: a navigation trail representing the current page location.
- Item: one segment in the trail (label + optional link).
- Current page item: the last item in the trail.
- Separator: a visual delimiter rendered between items.
- Breakpoint: Mobile / Tablet / Desktop (see `design/foundations/breakpoints.md`).
- Theme: Light / Dark (see `design/foundations/theme.md`).

## 4. Design Dependencies
- Theming: [design/foundations/theme.md](../foundations/theme.md)
- Breakpoints: [design/foundations/breakpoints.md](../foundations/breakpoints.md)
- Tokens:
	- [design/foundations/tokens.md#typography](../foundations/tokens.md#typography)
	- [design/foundations/tokens.md#colours](../foundations/tokens.md#colours)
- Shared text typography spec:
	- [DE-0004-Text](./DE-0004-Text.md)
- Link styles spec:
	- [DE-0005-Links](./DE-0005-Links.md)

## 5. Conceptual Model
Breadcrumbs is a **composed** component that uses existing typography atoms:
- Non-last items with a destination are rendered as `TextLink`.
- Items without a destination are rendered as `TextMedium`.
- The **last item** is always the **current page** and is rendered as `TextMedium` (never a link).

## 6. Behavioral Rules

### 6.1 Semantic structure
- Root element is a navigation landmark: `<nav aria-label="breadcrumbs">`.
- Inside the nav, breadcrumbs are represented as an ordered list: `<ol>`.
- Each breadcrumb item is a list item: `<li>`.

### 6.2 Separator rules
- Separators render **only between items**.
- Default separator character is `/`.
- Separator content may be customized by the component API (string input).
- Separator visual must be rendered using `TextMedium` typography (so typography stays token-driven and consistent).
- Separators must be non-interactive and ignored by assistive technology:
	- `aria-hidden="true"`
	- not focusable

### 6.4 Wrapping
- Breadcrumbs must support wrapping onto multiple lines by default.
- Wrapping behavior is required at all breakpoints.
- Truncation / single-line behavior is out of scope.

## 7. States & Variants
- No Breadcrumbs-specific visual variants are defined in this document.

## 8. Layout & Responsiveness
- Breadcrumbs layout must remain valid across Mobile / Tablet / Desktop breakpoints.
- Breadcrumbs must allow line wrapping (multi-line) without breaking semantics or keyboard navigation.
- No breakpoint-specific spacing or sizing rules are defined here; typography is inherited from `TextMedium`/`TextLink`.

## 9. Tokens & Theming
Breadcrumbs must not introduce new typography or color values; it composes existing components and their token contracts.

## 10. Accessibility
- Must render a `nav` landmark with `aria-label="breadcrumbs"`.
- Must use `ol` + `li` structure.
- Current page:
	- last item has `aria-current="page"`
	- last item is not a link (`a[href]` must not exist for current page)
- Separators:
	- have `aria-hidden="true"`
	- are not focusable
- Keyboard navigation:
	- focus lands only on actual breadcrumb links (non-last items with `link`).
	- focus does not land on separators or the current page item.

## 11. Rules & Constraints
- Tickets must not define numeric token values; they must reference token names and this design doc.
- Breadcrumbs must not hard-code typography values; it must use `TextMedium` and `TextLink` composition.
- Breadcrumbs must not render the last item as a link, even if a link is provided.
- Separators must be purely presentational (not links, not buttons, not focusable).
- No truncation / ellipsis / single-line-only behavior is defined here.

## 12. Non-normative Implementation Notes
For clarity only (design/tokens/specs are the source of truth):

Composition intent (UI-kit):
- Non-last links: `TextLink`
- Separator: `TextMedium` with `aria-hidden="true"`
- Current page: `TextMedium` with `aria-current="page"`

## 13. Edge Cases
- `items` is an empty array: recommended behavior is to render nothing (or an empty nav) without errors.
- Single-item breadcrumb:
	- render a single `TextMedium` current page item (with `aria-current="page"`) and no separators.
- Last item includes `link` in data:
	- still render as `TextMedium` current page (no link).
- Very long labels:
	- must wrap; separators must remain non-focusable and `aria-hidden`.
- Custom separator values:
	- must still be rendered using `TextMedium` and remain `aria-hidden`.

## 14. Change Impact
- Changes to `DE-0004-Text` or `DE-0005-Links` may affect Breadcrumbs typography and interaction states.
- Any update to separator rules, composition rules, or semantics requires re-running Breadcrumbs-related test runs.
