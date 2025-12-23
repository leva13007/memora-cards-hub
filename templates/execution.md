---
id: EX-MC-XXXX-YYYY-MM-DD
run-id: TR-MC-XXXX-YYYY-MM-DD     # reference to the test-run
executed-by: ""              # person, CI, MCP agent, etc.
environment: ""              # local | dev | staging | prod | storybook
started: YYYY-MM-DD HH:MM
finished: YYYY-MM-DD HH:MM
result: Pending              # Passed | Failed | Partial | Canceled | Pending
notes: ""
---

# {{id}} — Execution of {{run-id}}

## Summary  

| Metric        | Value |
|---------------|-------|
| Total         | X     |
| Passed        | X     |
| Failed        | X     |
| Blocked       | X     |
| Skipped       | X     |
| Duration      | HH:MM |

(These values can be manually added or auto-generated later.)

---

## Test Results  

A structured list or table of all test cases included in this execution with individual outcomes.

### Recommended table format:

| Test Case ID | Result  | Notes                           |
|--------------|---------|----------------------------------|
| TC-MC-0001   | Passed  |                                  |
| TC-MC-0002   | Failed  | Wrong color token in dark mode   |
| TC-MC-0003   | Passed  |                                  |
| TC-MC-0004   | Skipped | Not applicable for staging env   |

### Allowed result statuses:
- **Passed**
- **Failed**
- **Blocked**
- **Skipped**

---

## Failure Details  

(This section appears only if something failed.)

### Example format:

### TC-MC-0002 — H1 Typography (Dark Theme)

**Actual result:**  
H1 uses incorrect color token (`--color-text` instead of `--color-text-inverted`)

**Screenshots / Logs:**  
- `artifacts/EX-2025-12-08-01/TC-MC-0002.png`

**Suspected root cause:**  
Dark theme overrides not applied in UI-kit provider.

---

## Attachments  
(Optional: screenshots, logs, videos)

Example:
- `artifacts/{{id}}/screenshot-01.png`
- `artifacts/{{id}}/console-log.txt`

---

## Additional Notes  

Any observations relevant after test execution:

- Environment unstable  
- Build contained unrelated UI regressions  
- CI cache outdated  
- Performance degraded  

---

## Related  
- Test Run: {{run-id}}
- PR: …
- Issue: …