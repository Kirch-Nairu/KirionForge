# Maintainer Readiness Decision — FULL TEMPLATE (HIGH / CRITICAL)

> **R2-001 proposal / NOT ADOPTED.** Use for HIGH / CRITICAL features and discovered protected scopes, with only materially relevant evidence rows. This records one bounded GO per approved contract revision; no session-by-session reauthorization. For LOW/MEDIUM, prefer [the compact template](READINESS-DECISION-COMPACT.md).

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
- Risk tier: HIGH / CRITICAL (Second Brain four-tier model; record actual tool-derived mode where available)

## Minimal readiness record (all risk tiers)

- **Approved contract revision + Engineer authorization reference:**
- **Exact baseline SHA and bounded permitted paths:**
- **Expected functional and denied behavior:**
- **Protected invariants and dependent contracts:**
- **Assigned writer(s), integration ownership, collision exclusions:**
- **Locally executable checks, integrated acceptance plan, known NOT_RUN:**
- **Unknowns that block or are expressly excluded:**
- **GO / CONDITIONAL GO / NO-GO, signer and date:**

Complete each **material** HIGH/CRITICAL dimension with exact evidence. Mark irrelevant dimensions NOT APPLICABLE with a reason; an unknown protected authorization, data or money rule blocks its affected scope.

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

**PRE_INTEGRATION_HOLD:** ACTIVE / CLEARED (default ACTIVE for CRITICAL; ACTIVE for HIGH touching protected trust boundaries)

**Required nonauthor clearance type:** SECURITY_CLEARANCE / FINANCIAL_CLEARANCE / MIGRATION_CLEARANCE / OTHER (specify)

**Exact risk-bearing slice SHA and owned paths:**

**Nonauthor reviewer, review link, verdict and timestamp:**

**Executed negative evidence (deny/replay/rollback): commands, environment, results and artifacts; mark mandatory NOT_RUN as HOLD:**

**Engineer/business authority on changed protected policy, if relevant:**

**Integration writer clearance readback for exact live SHA:** PASS / HOLD / NOT CHECKED

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

**Operator approval (required for material policy deviation and protected HIGH/CRITICAL scope):**

No worker receives implementation authority merely because this document exists. The Engineer's applicable authority decision must be explicit and linked. Once GO is recorded, routine session transfers and bounded code fixes under the same contract do **not** require a new GO, docs-only PR, or formal review. A material authorization or protected-interface change reopens only its affected scope. The integration writer **must not integrate a risk-bearing slice while its clearance is absent, stale, negative or NOT_RUN**. No clearance implies whole-feature acceptance or stable-trunk/release permission.
