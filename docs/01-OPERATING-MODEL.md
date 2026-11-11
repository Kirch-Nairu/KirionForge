# 01 — KirionForge Operating Model

> **R2-001 DRAFT / NOT ADOPTED.** Proposed replacement lifecycle for the public KirionForge standard. Current authorized work in other repositories keeps its existing rules until separately approved.

## Purpose and boundary

KirionForge governs the transition from **desired behavior** to **authorized code work**. Its primary failure mode to prevent is an AI maintainer converting incomplete evidence into a broad implementation order.

Source code describes current behavior; operator-approved documentation describes intended behavior. They can contradict each other. The maintainer must surface, not silently settle, that contradiction.

## Authority matrix

| Role | Accountable for | Cannot do unilaterally |
| --- | --- | --- |
| Operator / Engineer | Business intent, functional policy, risk tolerance, scope, acceptance and release decisions | Treat an unverified AI claim as proven runtime evidence |
| Maintainer | Discovery, gap analysis, dependency map, contract reconciliation, readiness decision and handoff accuracy | Invent requirements, approve its own assumptions, quietly expand scope or claim tests ran |
| Implementation worker | Bounded implementation slice, candidate mechanical checks, changed-file inventory and accurate handback | Broaden approved behavior, self-accept or alter protected systems outside scope |
| Integration writer | Compose locally verified, provenance-preserved slices on an isolated integration candidate; run cross-component checks | Treat integration as acceptance, change protected contracts without approval or promote to stable |
| Independent reviewer | Evaluate the integrated feature candidate and applicable early critical-risk boundaries against the frozen contract | Become a parallel writer, self-review authored behavior or create product policy |
| Runtime QA / operator | Actual environment, data and human-journey proof | Equate a source assertion or mocked test with installed acceptance |

A named agent can perform a role, but the role is not owned by a model or product. Independence means separate evaluative responsibility and no unreported self-approval; it is not automatically achieved by switching model names.

## Acceptance unit and lifecycle

**The feature contract and its integrated behavior are the acceptance unit; an AI conversation, worker session, individual commit and routine branch handback are not.** Separate worker slices may be implemented concurrently only when file ownership and interfaces are nonconflicting. Each owned path has one active writer.

| State | Entry condition | Exit / decision |
| --- | --- | --- |
| INTAKE | Requested outcome or observed defect | Classify urgency, behavior and source evidence |
| DISCOVERY | Needed contracts, boundaries or dependencies unclear | Establish approved or explicitly deferred decisions |
| CONTRACT_READY | Testable feature contract, source baseline, risk tier and ownership available | Maintainer recommends readiness |
| AUTHORIZED | Engineer's relevant business/critical approvals and recorded GO or bounded CONDITIONAL GO | Writers may work within approved feature slices |
| IMPLEMENTING | Writer owns authorized scope | Candidate code, changed paths and local check evidence available |
| LOCAL_VERIFIED | Targeted build/tests and ownership/compatibility checks honestly reported | Eligible for isolated integration, subject to risk holds |
| INTEGRATED_CANDIDATE | Provenance-preserved slices composed on non-release branch, dependencies verified | Run integrated tests and applicable independent judgment review |
| UNDER_REVIEW | Frozen integrated SHA/feature contract version, review scope and evidence specified | Independent acceptance recommendation, bounded rework or contract escalation |
| TARGETED_REWORK | Confirmed defect, failed evidence, or changed approved contract | Repair affected scope and rerun invalidated checks; return to integrated review as applicable |
| FEATURE_ACCEPTED | No material outstanding findings under approved feature acceptance contract; integrated/runtime proof appropriate to risk | Eligible for separately controlled release |
| RELEASE_AUTHORIZED | Engineer approves exact accepted artifact and environment under project release controls | Promotion/deployment handled separately |
| CLOSED | Verified final disposition and unresolved obligations linked | No automatic effect on other missions |

**BLOCKED / NO-GO** can suspend the affected slice or feature at any stage. **SESSION_HANDOFF**, **COMMIT_PUSHED** and **PR_UPDATED** are evidence events, never acceptance states. An integrated candidate may remain unaccepted; it must not enter release/stable production merely because it builds or composes.

## Proposed R2 delivery sequence

1. **Agree on a feature outcome.** Record client-visible behavior, roles, positive/denied/edge journeys, data/contract dependencies and protected invariants. Obtain only missing material human decisions.
2. **Approve one bounded contract and readiness GO.** The maintainer verifies the source baseline and safe ownership slices. GO authorizes implementation of that revision until a material contract change or safety stop; it is not renewed for each session.
3. **Implement and check locally.** Each code writer preserves exact SHA, owned paths, meaningful targeted tests/builds and a compact handback. CI can run repeatedly; local green is not independent acceptance.
4. **Integrate early without promotion.** The integration owner brings eligible slices into one quarantined branch. Shared-API/permission/schema interfaces require compatibility/negative checks. Any CRITICAL pre-integration holds must have passed before a sensitive slice is combined.
5. **Freeze one integrated feature candidate.** Verify exact SHA, dependent real consumers, relevant security negatives and appropriate runtime journeys. Request independent judgment review **of this integrated outcome**, not each ended session.
6. **Repair precisely if necessary.** Correct the defect or obtain a changed contract; preserve valid findings and rerun only impacted tests/review areas. Material changes affecting a protected invariant reopen the corresponding risk review.
7. **Accept the feature, then separately authorize release.** Only the Engineer or delegated project authority makes the release decision for the exact verified artifact. Installed/manual, client and production controls remain distinct.

## Feature size and reviewer capacity

A feature is the smallest **client-demonstrable, end-to-end behavior** that can be integrated and assessed coherently. Do not accumulate an entire sprint or unrelated workflows into one giant acceptance diff. If an integrated change exceeds what an independent reviewer can reliably inspect, split it into traceable contract/permission/data/UI review partitions against the **same frozen integrated SHA**, or split the feature into smaller independently testable vertical outcomes. Recombine the findings in one feature disposition; never infer whole-feature approval from a truncated or sampled review. Critical-risk boundaries cannot be omitted by partitioning.

## Mechanical checks versus judgment gates

**Repeatable per-candidate checks:** source/branch ancestry; path ownership and scope; formatting/typecheck/build; focused tests; security negatives tied to changed surfaces; dependency/consumer compatibility; evidence validity and exact SHA. These may fail and block integration without requiring a new approval ceremony.

**Formal judgment:** readiness of material business authority, CRITICAL pre-integration security/irreversible-change review, integrated feature acceptance, and actual release authorization. A risk-specific independent check can occur before integration **and** integrated review when it protects a genuinely different failure boundary; document the distinction and reuse unaffected evidence.

A routine session change or handoff requires only the delta and current source/evidence pointer, not a new mission, independent acceptance, paired issue/ledger publication, or documentation-only merge. A feature may use existing issue/PR and versioned contract records; duplicate state publication is not a prerequisite in this proposal.

## Risk-scaled paths

**LOW / short path:** Isolated deterministic defects and presentation changes without material financial, security, authorization, migration or shared-state effects. Record baseline, expected behavior, mechanical proof and exact SHA; perform lightweight integrated acceptance. Independent judgment can be batched at the feature boundary.

**MODERATE / full feature path:** CRUD journeys, shared state, API consumers or multi-layer features require integrated runtime journeys and nonauthor review. **CRITICAL / protected path:** identity/permissions, sensitive records, financial integrity, irreversible state, retained-data migrations or other high-consequence operations require explicit relevant human authority plus early focused independent security/architecture inspection and negative proof before unsafe integration; retain integrated and release gates.

**Conditional path:** A mixed mission may contain ready and unready slices. Authorize only independent ready slices. Document the deferred ones with boundaries; do not call a partial implementation complete.

## Separation of discovery and verification

Discovery asks: *What should be built, what exists, and what else can be affected?*

Verification asks: *Did the frozen implementation satisfy the approved contract without violating protected invariants?*

A reviewer finding a previously unknown requirement is a **maintainer readiness escape**, not merely worker rework. A reviewer finding code contrary to an explicit requirement is normally a **worker implementation defect**. Both labels must be supported by evidence; causation can be shared.

## Non-interruption policy

When a worker is active, new ideas and noncritical findings are recorded for the next checkpoint. Interrupt only for a probable security exposure, data/financial integrity threat, destructive operation, unapproved scope change, or an invalidating business requirement. A maintainer does not micromanage mid-run because it has reconsidered its earlier instructions.

## Release principle

LOCAL_VERIFIED, integrated tests PASS, nonauthor review, feature acceptance, installed runtime PASS and operator release authorization are **distinct assertions** tied to appropriate exact SHAs/artifacts. Never collapse them into "done". A new feature, changed contract or critical defect may invalidate selected earlier evidence; revalidate the affected dependencies rather than blindly restarting every gate.
