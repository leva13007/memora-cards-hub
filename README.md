# Memora Hub

Memora Hub is a lightweight, file-based workspace for organizing QA activities and product knowledge for the Memora Cards project.

It stores:

- tickets (including bugs),
- test cases,
- test runs,
- executions,
- checklists,
- templates,
- and automation tooling.

Everything lives in Git, is reviewable via pull requests, and is simple enough to maintain by hand.

---

## Folder structure

- `automation/`  
  Reserved for automated tests, scripts, or tooling related to this hub (for example, linters, generators, CI checks).

- `qa_checklists/`  
  High-level QA checklists (for example, regression, smoke, accessibility).  
  Each checklist is usually based on `templates/checklist.md`.

- `qa_executions/`  
  Records of specific test executions (for example, a particular run of a regression suite for a release).  
  Based on `templates/execution.md`.

- `qa_test-cases/`  
  Individual test case definitions.  
  Each file should follow `templates/test-case.md`.

- `qa_test-runs/`  
  Definitions of test runs or campaigns (for example, “Release 1.2 regression”).  
  Uses `templates/test-run.md`.

- `tickets/`  
  Issue and bug tickets tracked as Markdown files.  
  Examples:  
  - `MC-0001-UI-kit-Create-Text-component.md`  
  - `MC-BUG-0001-Dark-theme-H1-color.md`  

  Use:
  - `templates/ticket.md` for general tickets (Story/Task/Feature/etc.)
  - `templates/ticket-bug.md` for bug-specific tickets.

- `templates/`  
  Source templates for creating new artifacts:
  - `checklist.md` – structure for QA checklists
  - `execution.md` – structure for test execution reports
  - `test-case.md` – structure for individual test cases
  - `test-run.md` – structure for test runs or campaigns
  - `ticket.md` – generic ticket template
  - `ticket-bug.md` – bug ticket template

---

## Conventions

### Naming

All IDs are Memora-specific and use the `MC` prefix where relevant.

Recommended patterns:

- Tickets:  
  - `MC-0001-Short-descriptive-title.md`  
  - Bugs: `MC-BUG-0001-Short-descriptive-title.md`
- Test cases:  
  - `TC-MC-0001-Feature-or-area.md`
- Test runs:  
  - `TR-MC-2025-12-09-Release-1.2-regression.md`
- Executions:  
  - `EX-MC-2025-12-09-TR-MC-2025-12-09-Release-1.2-regression.md`
- Checklists:  
  - `CL-MC-UI-regression-checklist.md`

Use **kebab-case** for the descriptive part (`words-separated-with-dashes`).

### Dates

Use ISO format for dates: `YYYY-MM-DD` (for example, `2025-12-09`).

### Frontmatter

All artifacts (tickets, test cases, test runs, executions, checklists) start with YAML frontmatter.  
Follow the corresponding template in `templates/` when creating new files.

### Links and cross-references

Reference related items using relative links where possible, for example:

- From a ticket to a test case:  
  `See [TC-MC-0001-Profile-update](../qa_test-cases/TC-MC-0001-Profile-update.md)`
- From an execution to its test run:  
  `Based on [TR-MC-2025-12-09-Release-1.2-regression](../qa_test-runs/TR-MC-2025-12-09-Release-1.2-regression.md)`

---

## How to create new items

### New ticket

1. Copy `templates/ticket.md` or `templates/ticket-bug.md`.
2. Save it under `tickets/` with the next incremental ID, for example:  
   - `MC-0002-Short-title.md` (general)  
   - `MC-BUG-0002-Short-title.md` (bug)
3. Fill in all required sections:
   - summary / description
   - requirements / specifications
   - acceptance criteria
   - (for bugs) steps to reproduce, expected vs actual, environment
   - links to related test cases, runs, executions, PRs

### New test case

1. Copy `templates/test-case.md`.
2. Save it under `qa_test-cases/` with a new ID, for example `TC-MC-0002-Login-with-2FA.md`.
3. Document at least:
   - Objective
   - Preconditions
   - Steps
   - Expected results
   - Related tickets or features

### New test run

1. Copy `templates/test-run.md`.
2. Save it under `qa_test-runs/`, for example `TR-MC-2025-12-09-Release-1.2-regression.md`.
3. Specify:
   - Purpose and scope
   - Environment
   - Included test cases (links)
   - Entry and exit criteria

### New execution

1. Copy `templates/execution.md`.
2. Save it under `qa_executions/`, for example `EX-MC-2025-12-09-TR-MC-2025-12-09-Release-1.2-regression.md`.
3. Record:
   - Who executed it and when
   - Environment and build or version
   - Summary (total, passed, failed, blocked, skipped)
   - Per-test-case results
   - Discovered issues (with ticket links)

### New checklist

1. Copy `templates/checklist.md`.
2. Save it under `qa_checklists/`, for example `CL-MC-UI-regression-checklist.md`.
3. Fill in checklist items, grouped by area or feature (UI kit, editor, navigation, etc.).

---

## Workflow

A typical QA workflow using Memora Hub:

### 1. Plan work

- Create or update tickets in `tickets/`.
- Prepare or update test cases in `qa_test-cases/`.
- Define a test run in `qa_test-runs/`.

### 2. Execute tests

- Run the test run and record details in a new execution file under `qa_executions/`.
- Use checklists in `qa_checklists/` to ensure coverage of critical areas.

### 3. Log and track issues

- For each found issue, create or update a ticket in `tickets/`.
- Link tickets with relevant test cases, executions, and runs.

### 4. Review and iterate

- Use pull requests / code review to validate new or updated Markdown files.
- Adjust templates in `templates/` as the process evolves.
- Keep cross-links up to date (tickets ↔ test cases ↔ runs ↔ executions).

---

## Contribution guidelines

- Keep templates up to date and in sync with the current QA process.
- Prefer small, focused changes (for example, one new test case or ticket per commit).
- Keep language concise and factual; avoid duplicating information across files—link instead.
- When changing a template, coordinate with the team and update any docs that reference it.