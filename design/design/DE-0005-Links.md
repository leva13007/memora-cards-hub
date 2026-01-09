
# Links — Design Reference

## 1. Purpose
Define the visual and interaction rules for link-style UI so navigation affordances are consistent, accessible, and theme-aware.

## 2. Scope
Applies to link UI-kit components (currently `TextLink`) and any future link primitives that render semantic anchors.
Does not define routing behavior or application navigation patterns.

## 3. Terminology
- Theme: Light / Dark
- Link: a semantic anchor element (`<a href="…">`)
- Focus-visible: keyboard-only focus styling (see a11y rules)

## 4. Design Dependencies
- Theming: [design/foundations/theme.md](../foundations/theme.md)
- Breakpoints: [design/foundations/breakpoints.md](../foundations/breakpoints.md)
- Tokens:
	- [design/foundations/tokens.md#typography](../foundations/tokens.md#typography)
	- [design/foundations/tokens.md#colours](../foundations/tokens.md#colours)
- Shared text typography spec:
	- [DE-0004-Text](./DE-0004-Text.md)

## 5. Conceptual Model
Links are interactive text elements that render semantic anchor tags (`<a>`) with token-driven styles that adapt to the active theme.

## 6. Behavioral Rules
### 6.1 Semantic element
- Link UI must render as a semantic `<a>` element.
- Navigation destination is provided via `href`.

### 6.2 Shared typography rules (TextMedium-aligned)
`TextLink` typography is intentionally the same as `TextMedium`.

Link text must use the shared Text typography rules (see `DE-0004-Text`) and the `TextMedium` baseline; only the semantic element (`<a>`) and link interaction styles (color/hover/focus-visible) differ:
- Font family: `inherit` (must resolve to `Inter` via global typography stack)
- Line height: `normal`
- Font size: `var(--fonts-size-text)` (breakpoint-driven)
- Font weight: `var(--font-weight-normal)`

Font size by breakpoint:

| Token             | Mobile   | Tablet    | Desktop |
|-------------------|----------|-----------|---------|
| --fonts-size-text | 0.75rem  | 0.875rem  | 1rem    |

### 6.3 Visual rules (token-driven)
Links use semantic color tokens:
- Default state: `color: var(--color-link)`
- Hover state: `color: var(--color-link-hover)`

Other baseline styles:
- Cursor: `pointer`
- Text decoration: unset by default (`text-decoration: unset`)

### 6.4 Focus-visible (accessibility)
Keyboard focus must be clearly visible.

Required focus-visible style:

`outline: 1px solid var(--color-link, currentColor)`

Notes:
- The focus indicator must remain visible in both themes.
- Focus styling must use `:focus-visible` (not only `:focus`).

## 7. States & Variants
- Themes: Light / Dark
- States: default, hover, focus-visible
- No additional variants are defined in this document.

## 8. Layout & Responsiveness
- Link UI must behave consistently across the product breakpoints and themes.

## 9. Tokens & Theming
### Required tokens
- `--fonts-size-text`
- `--font-weight-normal`
- `--color-link`
- `--color-link-hover`

## 10. Accessibility
- Links must be keyboard reachable (Tab) and expose a visible focus indicator.
- The rendered element must remain a semantic `<a>` with an `href`.

## 11. Rules & Constraints
- Tickets must not define numeric token values; they must reference token names and this design doc.
- Link UI must not hard-code theme colors; it must rely on semantic tokens (`--color-link`, `--color-link-hover`).
- Link UI must not hard-code typography values; it must rely on typography tokens (`--fonts-size-text`, `--font-weight-normal`) and shared text rules (see `DE-0004-Text`).
- Theme is a global concern:
	- Link UI must not manage or override the active theme locally (see `design/foundations/theme.md`).

## 12. Non-normative Implementation Notes
For clarity only (tokens are the source of truth):

```css
a {
	color: var(--color-link);
	cursor: pointer;
	font-family: inherit;
	font-size: var(--fonts-size-text);
	font-weight: var(--font-weight-normal);
	line-height: normal;
	text-decoration: unset;
}

a:hover {
	color: var(--color-link-hover);
}

a:focus-visible {
	outline: 1px solid var(--color-link, currentColor);
}
```

## 13. Edge Cases
- N/A

## 14. Change Impact
- Any token change to `--color-link` or `--color-link-hover` requires re-running link-related test runs (e.g. TextLink).
- Changes may affect in-content navigation across the product.
