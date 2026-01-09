# Design Tokens

This document defines concrete, implementation-ready values
used across the Memora project.

All numeric values must be defined here and must not be duplicated
in tickets, test cases, or other documentation.

## Container

| Token               | Mobile | Tablet | Desktop |
|---------------------|--------|--------|---------|
| --container-width   | fluid  | 720px  | 1200px  |
| --container-padding | 16px   | 16px   | 16px    |

## Typography

Font family for all text components:
- `Inter`, sans-serif or `inherit` from parent(which resolves to `Inter`).

The height of the font is controlled via `line-height: normal;` across all components.

### Typography — base font size

| Token                 | Mobile   | Tablet   | Desktop |
|-----------------------|----------|----------|---------|
| --font-size-h-1       | 1.5rem   | 1.75rem  | 2rem    |
| --font-size-h-2       | 1.125rem | 1.25rem  | 1.5rem  |
| --fonts-size-text     | 0.75rem  | 0.875rem | 1rem    |

### Typography — font weights

| Token                 | Value |
|-----------------------|-------|
| --font-weight-light   | 300   |
| --font-weight-normal  | 400   |
| --font-weight-semi    | 600   |
| --font-weight-bold    | 700   |

## Colours

| Token                 | Light theme | Dark theme |
|-----------------------|-------------|------------|
| --color-text          | #0f172a   | #e5e7eb  |
| --color-warning       | #ec1515   | #ec1515  |
| --color-link          | #1a73e8   | #8ab4f8  |
| --color-link-hover    | #174ea6   | #174ea6  |

## Rules

- Tokens defined here are the **source of truth** for concrete values.
- Tickets must not redefine token values; they should reference token names (and the relevant design docs).
- QA test cases may assert concrete values (px, rem, etc.) but should reference the corresponding token name and keep expectations in sync with this file.
- Any token change requires:
  - updating affected test cases
  - re-running related test runs