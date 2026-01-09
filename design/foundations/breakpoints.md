# Breakpoints — Foundations

This document defines the official responsive breakpoints used across the Memora project.
All UI components, layouts, and test cases must rely on these breakpoints.

Breakpoints are defined in **viewport width (px)** and are **inclusive** unless stated otherwise.

## Terminology

The following breakpoint names are **canonical terms** across the Memora project:

- **Mobile**
- **Tablet**
- **Desktop**

These terms must be used consistently in:
- tickets
- test cases
- test runs
- executions
- documentation
- code comments

When referring to a breakpoint in **product documentation** (tickets, specs), prefer the **term name** (e.g. `Desktop`) instead of numeric values.

Numeric ranges (px) are defined in this document and should be treated as the source of truth.

## Breakpoint definitions

| Name    | Range (px)            | Description |
|--------|-----------------------|-------------|
| Mobile | `< 768`               | Small screens, phones |
| Tablet | `768 – 1279`          | Tablets and small laptops |
| Desktop| `≥ 1280`              | Standard desktop screens |

## Rules

1. **Mobile**
   - Applies when viewport width is **less than 768px**
   - Used for phone-sized devices

2. **Tablet**
   - Applies when viewport width is **from 768px up to 1279px**
   - Includes tablets and small laptop windows

3. **Desktop**
   - Applies when viewport width is **1280px or greater**
   - Default target for full desktop layout

## Usage rules

- Breakpoints must be used consistently across:
  - UI components
  - Layout components
  - Typography
  - QA test cases
  - Documentation
- No custom or component-specific breakpoints are allowed unless explicitly documented.
- Media queries must align exactly with the ranges defined above.

- Tickets and design specs should reference breakpoints by name (Mobile / Tablet / Desktop).
- QA test cases may include explicit pixel values **only** when needed for boundary checks (e.g. 767/768, 1279/1280) and must match the ranges defined above.

## CSS reference (example)

```css
/* Mobile */
@media (max-width: 767px) {
}

/* Tablet */
@media (min-width: 768px) and (max-width: 1279px) {
}

/* Desktop */
@media (min-width: 1280px) {
}