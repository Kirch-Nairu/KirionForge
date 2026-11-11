# Maintainer Readiness Decision — TEMPLATE

> R2-001 proposed use: **one GO for a feature/contract revision**, not one per worker session. The compact fields below are the baseline. Complete detailed evidence matrices proportionately for material and CRITICAL risks; do not turn irrelevant rows into compulsory paperwork.

- Feature ID / client-visible outcome:
- Mission ID (if distinct):
- Operator feature contract and revision:
- Technical authority:
- Maintainer:
- Assessment date:
- Repository / baseline branch:
- **Exact baseline SHA:**
- Known installed/runtime artifact and hash (if relevant):
- Related issues/PRs:
- Risk tier: LOW / MODERATE / CRITICAL

## Minimal readiness record (all risk tiers)

- **Approved contract revision + Engineer authorization reference:**
- **Exact baseline SHA and bounded permitted paths:**
- **Expected functional and denied behavior:**
- **Protected invariants and dependent contracts:**
- **Assigned writer(s), integration ownership, collision exclusions:**
- **Locally executable checks, integrated acceptance plan, known NOT_RUN:**
- **Unknowns that block or are expressly excluded:**
- **GO / CONDITIONAL GO / NO-GO, signer and date:**

If this record is complete for a truly LOW isolated change, the extended sections below may be marked `NOT APPLICABLE` with a short reason. For MODERATE/CRITICAL, supply every **material** affected dimension; irrelevant dimensions do not require invented detail.

## A. Evidence ledger

| ID | Material assertion | OBSERVED / CODE_VERIFIED / TEST_VERIFIED / OPERATOR_APPROVED / INFERRED / UNKNOWN | Precise evidence + SHA | Impact |
| --- | --- | --- | --- | --- |
| | | | | |

## B. Readiness matrix

Mark each **VERIFIED, APPROVED, NOT APPLICABLE or UNKNOWN**. Provide evidence, not checkboxes alone.

| Contract dimension | Status | Evidence / missing work |
| --- | --- | --- |
| Business purpose and scope | | |
| Roles, readable fields and mutation rights | | |
| State lifecycle and denial/replay | | |
| UI journeys / document output | | |
| API request/response consumers | | |
| Persistence, migrations and transaction boundaries | | |
| Monetary equations / reconciliation | | |
| Audit attribution and atomicity | | |
| Protected adjacent features | | |
| Test environment and runnable acceptance | | |
| Installed/manual acceptance owner | | |
| Open product decisions | | |

## C. Verified component and dependency map

| Requirement | UI | API / auth | Service | Data / audit | Test | Evidence |
| --- | --- | --- | --- | --- | --- | --- |
| | | | | | | |

## D. Authorized execution scope

**Permitted work:**

**Forbidden / protected work:**

**Deferred work (CONDITIONAL GO only):**

**Expected slice branches, one writer per owned path, and integration owner:**

**Independent feature reviewer (read-only for the reviewed code; schedule at integrated acceptance):**

**Additional critical pre-integration risk review / hold (if applicable):**

**Required deliverables and evidence:**

## E. Acceptance plan

| Test ID | Assertion (including forbidden behavior) | Command / procedure | Environment | Evidence recipient |
| --- | --- | --- | --- | --- |
| | | | | |

## F. Unknowns and consequences

| Unknown | Could it change authorized implementation? | Closure evidence / human decision | Blocker? |
| --- | --- | --- | --- |
| | | | |

## G. Formal gate

**Decision: GO / CONDITIONAL GO / NO-GO**

**Reason (supported, not inferred):**

**For NO-GO: exact closure conditions:**

**For CONDITIONAL GO: independent boundaries and forbidden assumptions:**

**Contract revision authorized:**

**Maintainer signature / timestamp:**

**Operator approval (required for business-policy deviations and high-risk scope):**

No worker receives implementation authority merely because this document exists. The Engineer's applicable authority decision must be explicit and linked. Once GO is recorded, routine session transfers and bounded code fixes under the same contract do **not** require a new GO, docs-only PR, or formal review. A material authorization or protected-interface change reopens only its affected scope.
