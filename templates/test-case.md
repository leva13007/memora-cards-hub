---
id: TC-MC-XXXX
title: ""
type: UI              # UI | Functional | Integration | E2E | Regression | Smoke
priority: Medium      # Low | Medium | High | Critical
area: ""              # ui-kit/typography | ui-kit/buttons | app/editor | settings | backend
component: ""         # optional; UI component or module name
related-ticket: ""    # MC-XXXX
status: Active        # Active | Draft | Deprecated
created: YYYY-MM-DD
updated: YYYY-MM-DD
---

# {{id}} — {{title}}

## 🎯 Objective  
What is the goal of this test case?  
Describe what exactly should be validated and why.

---

## Preconditions  
Requirements before executing the test.

Examples:
- Application is running
- User is logged in
- Storybook is open
- Theme is set to light
- Test data exists

---

## Test Data  
(Optional) Any specific data, inputs, or configuration needed.

Example:

| Device   | Width (px) |
|----------|------------|
| Desktop  | ≥ 1280    |
| Tablet   | 768–1279   |
| Mobile   | ≤ 767      |

---

## Steps  
Step-by-step instructions to perform the test.

1. …
2. …
3. …
4. …

**All steps must be reproducible manually.**

---

## Expected Result  
The expected outcome after completing all steps.  
Should be clear, verifiable, and measurable.

Example:
- Font-size = 2rem on desktop
- Uses token `--color-text`
- No visual artifacts
- Component matches Figma spec

---

## Screenshots / Attachments  
(Optional) Visual references to aid in validation.

---

## Edge Cases  
(Optional) Additional cases worth checking:

- …
- …

---

## Notes  
Any additional comments, references, screenshots, logs, etc.

---

## Related  
- Ticket: MC-XXXX  
- Other test cases: TC-MC-YYYY  
- Figma / Docs / PR links (optional)