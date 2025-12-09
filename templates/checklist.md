---
id: CL-XXXX
title: ""
type: Smoke           # Smoke | Sanity | Regression | Release | UI-Kit | Custom
scope: ""             # e.g. pre-release, sprint-04, ui-kit only, editor module, staging
created: YYYY-MM-DD
updated: YYYY-MM-DD
owner: ""             # person responsible for checklist definition
status: Active        # Active | Deprecated
---

# {{id}} — {{title}}

## Purpose  
Describe why this checklist exists and when it should be used.  
Example:  
“To quickly validate that all critical UI-kit typography components work after design token updates.”

---

## Preconditions  
Environment or setup required before executing this checklist.

Examples:
- Staging build deployed
- Storybook running
- User logged in
- Test account prepared

---

## Checklist Items  

Mark with `[ ]` when unchecked, `[x]` when completed.

(You can group them into logical sections.)

---

### UI / Typography
- [ ] H1 renders correctly (light theme)
- [ ] H1 renders correctly (dark theme)
- [ ] Paragraph text uses correct line height
- [ ] All text tokens resolve correctly

---

### Theming
- [ ] Light theme loads without errors
- [ ] Dark theme loads without flicker
- [ ] Color tokens apply consistently
- [ ] No mixed-light/dark inconsistencies

---

### Navigation
- [ ] App loads without console errors
- [ ] Sidebar renders all sections
- [ ] Navigation between pages works

---

### Core Flows
- [ ] Cards Editor opens
- [ ] Editing a card updates preview
- [ ] Adding a new card works
- [ ] Saving a deck works

---

### Error Handling
- [ ] Error toast appears on API failure
- [ ] Validation errors show correctly

---

### Additional Checks
- [ ] No layout shifts
- [ ] No broken icons/images
- [ ] No console warnings

---

## Notes  
Additional information, anomalies, screenshots, or observations.

---

## Related  
- Test Runs: TR-XXXX  
- Tickets: MC-XXXX  
- Docs: …