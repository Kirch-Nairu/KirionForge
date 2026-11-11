# Feature Contract — TEMPLATE

> **R2-001 proposed use.** Copy this file into the target project's private issue/PR or documentation. For LOW isolated changes, use an abbreviated contract: observable outcome, exact baseline, owned scope, protected behavior, required tests and accountable approval. Mark irrelevant sections NOT APPLICABLE with reason; do not write fictitious business/data contracts merely to fill a template. For MEDIUM/HIGH/CRITICAL changes, complete the materially affected role, interface, state, data and negative-test dimensions. The Second Brain model has four tiers; protected HIGH/CRITICAL changes require an attributable pre-integration clearance. A blank **relevant** section is UNKNOWN, not implicitly approved. No separate docs-only merge is required solely to activate an already approved feature.

- Feature / contract ID:
- Contract revision:
- Owner / Engineer:
- Repository / product:
- Status: DRAFT / OPERATOR_APPROVED / SUPERSEDED
- Effective date:
- Related issue / evidence:
- Approver and approval record:

## 1. Business intent and boundaries

**Problem to solve:**

**Expected business outcome:**

**In scope:**

**Explicitly out of scope:**

**Protected existing behavior (must not regress):**

## 2. Roles, data visibility and action authority

| Role | Can view which fields? | Can create/update/approve/void? | Explicitly forbidden | Audit identity |
| --- | --- | --- | --- | --- |
| | | | | |

Distinguish **menu visibility, API read permission, sensitive field visibility and API mutation permission**. A role that may create a request does not thereby obtain vendor financial data or managerial approval powers.

## 3. User journeys

| Journey ID | Actor | Preconditions | Steps / expected UI | Expected API/data result | Failure/retry behavior |
| --- | --- | --- | --- | --- | --- |
| J-01 happy path | | | | | |
| J-02 denied path | | | | | |
| J-03 edge/restart | | | | | |

Attach approved wireframes/screenshots where visual structure is material.

## 4. Business state lifecycle

**Entities and authoritative owner:**

| From | Event/action | Authorized actor | Preconditions | To | Audit event |
| --- | --- | --- | --- | --- | --- |
| | | | | | |

**Invalid transitions, duplicate replay, cancellation, reversal, partial completion and idempotency:**

## 5. Data & financial contract

- Models / relationships:
- Source of truth:
- Inputs, units, rounding and authoritative equations:
- Uniqueness and concurrency constraints:
- Transaction boundaries / rollback:
- Migration and old-data compatibility:
- Offline/restart/backup behavior:
- Document/print/export reconciliation:
- Privacy and retention requirements:

For monetary documents, specify all relevant components (e.g., subtotal − discount + tax + shipping = total). Do not allow invalid amounts to print as plausible totals.

## 6. UI and accessibility

- Pages/routes and navigation by role:
- Search, entry, empty, loading and error states:
- Keyboard/scanner interaction if relevant:
- Validation, confirmation and feedback:
- Responsive, printing and accessibility requirements:
- Screens or reference designs:

## 7. Audit and observability

| Business event | Actor source | Entity | Before/after fields | Reason | Atomic with which transaction? |
| --- | --- | --- | --- | --- | --- |
| | | | | | |

## 8. Acceptance matrix

| ID | Requirement | Positive test | Denial / negative | Edge / replay | Required evidence layer |
| --- | --- | --- | --- | --- | --- |
| A-01 | | | | | API / DB / UI / Installed |

Identify tests that cannot execute in the worker environment and who will run them. A test passing must not be promoted to manual installed acceptance.

## 9. Open decisions and risks

| ID | Unknown or conflict | Impact if guessed | Decision owner | Required answer/evidence | Blocking? |
| --- | --- | --- | --- | --- | --- |
| O-01 | | | | | |

## 10. Operator approval

- Decision: APPROVED / PARTIALLY APPROVED / REJECTED
- Approved revision and exact scope:
- Conditions or excluded slices:
- Record of explicit approval:

**This contract defines business intent. The maintainer must separately verify repository feasibility before GO.**
