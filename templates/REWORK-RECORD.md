# Rework Record — TEMPLATE

> **R2-001 proposal:** this is a material-defect record, not a compulsory document at each session/candidate transition. Prefer the existing feature issue/PR; no fresh GO for a localized fix within the approved contract.

- Rework ID:
- Mission / PR:
- Frozen candidate SHA:
- Approved contract revision:
- Observed by / timestamp:
- Reviewer or runtime evidence:
- Severity: BLOCKER / HIGH / MEDIUM / LOW
- Class: R1 / R2 / R3 / R4 / R5 / R6 / R7 / R8 (see Dynamic Rework)
- Primary cause / contributing causes:

## Evidence

**Expected according to approved contract:**

**Actual behavior:**

**Source/test/runtime proof with exact SHA:**

**What remains verified and passing:**

## Contract effect

- Is requirement already explicit? YES / NO
- Is this a new product decision? YES / NO
- Does it invalidate earlier GO? YES / NO
- Is it safe to continue independent in-progress work? YES / NO
- Operator escalation required? YES / NO
- Immediate interruption required under critical stop policy? YES / NO

## Bounded correction

**Single responsible writer:**

**Allowed source/test scope:**

**Prohibited changes:**

**Acceptance assertions (positive, negative, replay):**

**Test rerun set and evidence not reusable:**

**Exact handback requirements:**

## Resolution

- New candidate SHA:
- Tests / results / log paths:
- Independent finding disposition (only when a formal review finding applies; otherwise NOT APPLICABLE):
- Updated readiness decision / contract revision (if needed):
- Operator acceptance required:
- Status: OPEN / BLOCKED / VERIFIED / DEFERRED

A rework record does not authorize implementation outside the existing approved scope. Re-run invalidated tests and obtain targeted nonauthor closure of material prior findings; a new full-feature review or documentation-only acceptance PR is not automatic. Actual integrated feature acceptance remains at the frozen combined SHA.
