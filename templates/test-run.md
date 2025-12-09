---
id: TR-YYYY-MM-DD-XX
title: ""
type: Regression        # Regression | Smoke | UI | E2E | Performance | Custom
scope: ""               # sprint-03 | pre-release | ui-kit | nightly | hotfix
created: YYYY-MM-DD
owner: ""               # who defines the run
environment: ""         # local | dev | staging | production | storybook
status: Planned         # Planned | In Progress | Completed | Canceled
related-tickets: []     # MC-XXXX if applicable
---

# {{id}} — {{title}}

## 🎯 Purpose  
Short explanation of why this test run exists.  
Example:
- Validate UI-kit typography before merging to `develop`
- Sprint 03 regression before release candidate
- Smoke test after deployment to staging

---

## Scope  
Clearly define what is *in scope* and what is *out of scope*.

### In Scope
- …
- …

### Out of Scope
- …
- …

---

## Preconditions  
What must be ready before running tests?

Examples:
- Build version: `0.4.7-alpha`
- Staging environment deployed
- Test data seeded
- Storybook available

---

## Test Suite  
List of test cases included in this run.

Format A (simple):

TC-MC-0001 — H1 Typography (Light Theme)
TC-MC-0002 — H1 Typography (Dark Theme)
TC-MC-0003 — Button Primary States

Format B (table — recommended):

| ID          | Title                                | Area               | Priority |
|-------------|----------------------------------------|--------------------|----------|
| TC-MC-0001  | H1 Light Theme Typography              | ui-kit/typography  | High     |
| TC-MC-0002  | H1 Dark Theme Typography               | ui-kit/typography  | High     |
| TC-MC-0003  | Button Primary States                  | ui-kit/buttons     | Medium   |

---

## Related Materials  
(Optional)

- Release notes: …
- Design docs: …
- API changes: …
- Figma updates: …

---

## Notes  
Any additional context for testers or automation owners.

---

## Executions  
List actual executions of this test run.

(Execution details live in `executions/EX-*.md`)

Format:

- EX-YYYY-MM-DD-01 — Oleh — Local — Passed
- EX-YYYY-MM-DD-02 — CI Nightly — Failed
- EX-YYYY-MM-DD-03 — Rerun after fixes — Passed