# Theming — Foundations

This document defines the theming model used across the Memora design system.
It describes how visual themes are structured, applied, and activated at runtime.

Theming is a **global concern** and affects all UI components consistently.

## 1. Purpose

The purpose of theming is to provide a consistent visual experience
by switching sets of design tokens that control colors and related visual properties.

Themes do not change component structure or behavior —
only their visual appearance.

## 2. Supported Themes

The design system currently supports the following themes:

- **Light**
  - Default theme
  - Light background with dark text

- **Dark**
  - Alternative theme
  - Dark background with light text

Additional themes may be introduced in the future if explicitly defined.

## 3. Design Scope

Theming affects:
- color tokens (text, background, borders, accents)
- semantic color mappings (e.g. primary, warning, danger)

Theming does **not** affect:
- layout
- spacing
- typography scale
- component structure

## 4. Theme Activation Model

Themes are activated **globally** via a data attribute on the root HTML element.

### Activation mechanism

For **Light theme**:
```html
<html data-theme="light">
```

For **Dark theme**:
```html
<html data-theme="dark">
```
* The data-theme attribute on the <html> element defines the active theme.
* All theme-dependent tokens must be scoped under this attribute.
* Components must not manage or override the active theme locally.

This mechanism is considered part of the design system contract.

## 5. Token Resolution Rules

* Design tokens must be defined in a theme-aware manner.
* Theme-specific values must be scoped using the data-theme attribute.

Example (conceptual):

```css
:root[data-theme="light"] {
  --color-text: #0f172a;
  --color-background: #ffffff;
}
:root[data-theme="dark"] {
  --color-text: #f5f7fb;
  --color-background: #1a202c;
}
```

Components must rely only on semantic tokens
and must not reference theme values directly.

## 6. Usage Rules

* Both Light and Dark themes must maintain sufficient color contrast.
* Theme changes must not reduce readability or usability.
* Contrast requirements are validated via design tokens, not per component.

## 7. Accessibility Considerations

* Both Light and Dark themes must maintain sufficient color contrast.
* Theme changes must not reduce readability or usability.
* Contrast requirements are validated via design tokens, not per component.
