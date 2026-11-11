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
| LOCAL_VERIFIED | Targeted build/tests and ownership/compatibility checks honestly reported | Eligible for isolated integration **only if** relevant PRE_INTEGRATION_HOLD is cleared |
| INTEGRATED_CANDIDATE | Eligible slices composed on a quarantined non-release branch; all applicable pre-integration clearances verified against exact input SHAs | Run feature-wide integrated tests and independent judgment review |
| UNDER_REVIEW | Frozen integrated SHA/feature contract version, review scope and evidence specified | Independent acceptance recommendation, bounded rework or contract escalation |
| TARGETED_REWORK | Confirmed defect, failed evidence, or changed approved contract | Repair affected scope and rerun invalidated checks; return to integrated review as applicable |
| FEATURE_ACCEPTED | No material findings; final integrated SHA passes required feature journeys/contract assertions, nonauthor review and risk-appropriate runtime evidence | Eligible to request project-authorized trunk promotion or release; **neither is automatic** |
| RELEASE_AUTHORIZED | Engineer or valid project release authority approves exact artifact and destination under release controls | Deployment/tagging/installation may proceed under separate operator safeguards |
| CLOSED | Verified final disposition and unresolved obligations linked | No automatic effect on other missions |

**BLOCKED / NO-GO** can suspend the affected slice or feature at any stage. **PRE_INTEGRATION_HOLD** is a blocking flag on affected risk-bearing slices, not a separate whole-feature approval state. **SESSION_HANDOFF**, **COMMIT_PUSHED**, **PR_UPDATED** and **TRUNK_MERGED** are evidence events, never acceptance states. An integrated candidate may remain unaccepted; it must not be promoted to stable trunk or released merely because it builds or composes.

## Proposed R2 delivery sequence

1. **Agree on a feature outcome.** Record client-visible behavior, roles, positive/denied/edge journeys, data/contract dependencies and protected invariants. Obtain only missing material human decisions.
2. **Approve one bounded contract and readiness GO.** The maintainer verifies the source baseline and safe ownership slices. GO authorizes implementation of that revision until a material contract change or safety stop; it is not renewed for each session.
3. **Implement and check locally.** Each code writer preserves exact SHA, owned paths, meaningful targeted tests/builds and a compact handback. CI can run repeatedly; local green is not independent acceptance.
4. **Integrate early without promotion.** The integration owner composes only eligible slices in a quarantined branch. Shared-API/permission/schema interfaces require compatibility/negative checks. Every active **PRE_INTEGRATION_HOLD** must be cleared against the exact risk-bearing slice before integration; HIGH protected and CRITICAL scopes are covered by the clearance rule below.
5. **Freeze a reviewable integrated feature candidate.** Verify exact SHA, dependent real consumers, relevant security negatives, and primary end-to-end journeys/contract acceptance on the **final integrated SHA** for MEDIUM/HIGH/CRITICAL work. Request independent judgment review **of this integrated outcome**, not each ended session. Unexecuted mandatory proof is a HOLD, not a PASS.
6. **Repair precisely if necessary.** Correct the defect or obtain a changed contract; preserve valid findings and rerun only impacted tests/review areas. Material changes affecting a protected invariant reopen the corresponding risk review.
7. **Accept, promote and release under distinct authority.** FEATURE_ACCEPTED qualifies the frozen candidate for **a separate repository-authorized promotion to stable trunk** under branch protection, ownership and exact-SHA checks; it does not itself issue permission to merge. Record any trunk merge SHA and confirm required postmerge checks. **RELEASE_AUTHORIZED** governs external deployment, tagging or installation on the exact accepted/promoted artifact. If merge-to-main automatically deploys, that merge is itself a release-impacting operation and must satisfy release authority **before merging**.

## Feature size and reviewer capacity

A feature is the smallest **client-demonstrable, end-to-end behavior** that can be integrated and assessed coherently. Do not accumulate an entire sprint or unrelated workflows into one giant acceptance diff. When a candidate exceeds reviewer capacity, **split the delivery into smaller, independent vertical features that each include their required UI/API/permission/data/consumer journeys**, with a reviewable integrated SHA for each. Specialized security or performance reviewers may inspect individual layers, but that evidence **never substitutes for the end-to-end interaction review** required for feature acceptance. A truncated or sampled review cannot award approval for unexamined behavior.

## Pre-integration clearance for protected changes

The Engineer/maintainer classifies each authorized slice against the shared **LOW / MEDIUM / HIGH / CRITICAL** risk model. A slice is marked `PRE_INTEGRATION_HOLD=ACTIVE` when it is **CRITICAL**, or **HIGH with an authorization, confidentiality, financial, irreversible-state, retained-data/migration or other protected trust boundary**, including one discovered after initial GO. If a supposedly lower-risk slice unexpectedly touches such a boundary, suspend **that affected slice** immediately and reassess its risk; independent unaffected slices may proceed only when their interfaces and evidence remain valid.

**Clearing an active hold requires an attributable pre-integration clearance record** (e.g., `SECURITY_CLEARANCE` for auth/data protection, `FINANCIAL_CLEARANCE`, or `MIGRATION_CLEARANCE`) containing: feature/slice ID, contract revision, exact candidate SHA and owned paths, protected invariants, positive/deny/replay/rollback tests with actual command, environment, result and artifact (or explicit NOT_RUN), independent nonauthor reviewer identity and disposition, required Engineer/authorized business decision, and the named integration owner. A `PASS` must not be awarded from a missing test or unverified reviewer statement.

**Integration writer enforcement:** before composing source, resolve the live slice SHA, verify a matching `CLEARANCE=PASS` and completed required negative checks, and confirm no relevant code/contract/authority drift. If missing, stale, rejected or NOT_RUN for mandatory proof: `PRE_INTEGRATION_HOLD=ACTIVE`, **do not integrate the affected slice**. After any risk-bearing change, re-clear the changed boundary. The clearance is a **procedural release of an integration hold**, not a feature acceptance, stable-trunk promotion or production release.

## Trunk promotion and external release

`FEATURE_ACCEPTED` makes the exact integrated candidate **eligible** for trunk promotion. A protected-branch merge still requires the repository's separately valid owner/maintainer authorization, required checks, review and branch policies. Record the resulting exact trunk SHA and any mandatory postmerge checks; no new routine writer-session gate is implied. `RELEASE_AUTHORIZED` is a distinct human decision for deployment, installation or release tagging. Repos where merges trigger deployment must treat trunk promotion as a release-impacting operation and obtain the release authority first.

## Mechanical checks versus judgment gates

**Repeatable per-candidate checks:** source/branch ancestry; path ownership and scope; formatting/typecheck/build; focused tests; security negatives tied to changed surfaces; dependency/consumer compatibility; evidence validity and exact SHA. These may fail and block integration without requiring a new approval ceremony.

**Formal judgment:** readiness of material business authority; HIGH-protected and CRITICAL pre-integration clearance when triggered; integrated feature acceptance; repository-specific trunk promotion approval; and actual release authorization. A risk-specific independent check can occur before integration **and** integrated review when it protects a genuinely different failure boundary; document the distinction and reuse unaffected evidence.

A routine session change or handoff requires only the delta and current source/evidence pointer, not a new mission, independent acceptance, paired issue/ledger publication, or documentation-only merge. A feature may use existing issue/PR and versioned contract records; duplicate state publication is not a prerequisite in this proposal.

## Risk-scaled paths

**LOW / short path:** Isolated deterministic defects and presentation changes with no material protected, migration or shared-state effects. Keep baseline, scope, focused checks and exact SHA; lightweight integrated acceptance is enough.

**MEDIUM / feature path:** Bounded CRUD journeys and cross-layer/shared state require end-to-end contract and primary journey testing on the final integrated SHA, plus independent feature review.

**HIGH / protected-dependent path:** Shared contracts, sensitive permissions/data, financial or migration surfaces require stronger affected-consumer and denial/replay proof. When the slice changes a protected trust boundary, `PRE_INTEGRATION_HOLD` and nonauthor clearance are mandatory.

**CRITICAL / strict path:** High-consequence security, retained-data, irreversible/production recovery and similar blast radius require a complete affected contract, explicit authorized human decision, independent pre-integration clearance, integrated negative/transaction proof, runtime acceptance and separate release authority.

**Compatibility:** Risk names match the existing Second Brain `LOW / MEDIUM / HIGH / CRITICAL` model. Its executable task-type floors and critical triggers remain authoritative where installed; this public documentation does not recalculate or override them. Legacy projects using `MODERATE` do not silently migrate—project owners must map and approve that transition.

**Conditional path:** A mixed mission may contain ready and unready slices. Authorize only independent ready slices. Document the deferred ones with boundaries; do not call a partial implementation complete.

## Separation of discovery and verification

Discovery asks: *What should be built, what exists, and what else can be affected?*

Verification asks: *Did the frozen implementation satisfy the approved contract without violating protected invariants?*

A reviewer finding a previously unknown requirement is a **maintainer readiness escape**, not merely worker rework. A reviewer finding code contrary to an explicit requirement is normally a **worker implementation defect**. Both labels must be supported by evidence; causation can be shared.

## Non-interruption policy

When a worker is active, new ideas and noncritical findings are recorded for the next checkpoint. Interrupt only for a probable security exposure, data/financial integrity threat, destructive operation, unapproved scope change, or an invalidating business requirement. A maintainer does not micromanage mid-run because it has reconsidered its earlier instructions.

## Release principle

LOCAL_VERIFIED, pre-integration clearance (when triggered), final-SHA primary journeys/contract tests, integrated feature review and acceptance, repository trunk-promotion approval, installed runtime PASS and Engineer release authorization are **distinct assertions** tied to appropriate exact SHAs/artifacts. Never collapse them into "done". A new feature, changed contract or critical defect may invalidate selected earlier evidence; revalidate the affected dependencies rather than blindly restarting every gate.
