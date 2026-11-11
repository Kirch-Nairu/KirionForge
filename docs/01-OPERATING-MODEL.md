# 01 — KirionForge Operating Model

## Purpose and boundary

KirionForge governs the transition from **desired behavior** to **authorized code work**. Its primary failure mode to prevent is an AI maintainer converting incomplete evidence into a broad implementation order.

Source code describes current behavior; operator-approved documentation describes intended behavior. They can contradict each other. The maintainer must surface, not silently settle, that contradiction.

## Authority matrix

| Role | Accountable for | Cannot do unilaterally |
| --- | --- | --- |
| Operator / Engineer | Business intent, functional policy, risk tolerance, scope, acceptance and release decisions | Treat an unverified AI claim as proven runtime evidence |
| Maintainer | Discovery, gap analysis, dependency map, contract reconciliation, readiness decision and handoff accuracy | Invent requirements, approve its own assumptions, quietly expand scope or claim tests ran |
| Implementation worker | One authorized change, affected code/contracts, tests, evidence and transparent blockers | Redesign unapproved workflows or alter protected systems outside scope |
| Independent reviewer | Evaluate frozen candidate against approved contract, touched boundaries and evidence | Become a parallel writer or create product policy through review |
| Runtime QA / operator | Actual environment, data and human-journey proof | Equate a source assertion or mocked test with installed acceptance |

A named agent can perform a role, but the role is not owned by a model or product. Independence means separate evaluative responsibility and no unreported self-approval; it is not automatically achieved by switching model names.

## Lifecycle states

| State | Entry condition | Exit condition |
| --- | --- | --- |
| INTAKE | Operator observation, request or defect arrives | Scope and evidence classified |
| DISCOVERY | Code, business policy or dependencies unresolved | Relevant sources and unknowns recorded |
| CONTRACT_READY | Versioned intended behavior + testable criteria exist | Maintainer gate completed |
| AUTHORIZED | GO or bounded CONDITIONAL GO recorded | Single writer accepts exact mission |
| IMPLEMENTING | Worker edits only approved scope | Tests and evidence available; changes frozen |
| FROZEN_FOR_REVIEW | Exact commit SHA and contract revision locked | Reviewer disposition published |
| REWORK | Review/runtime failure classified | Bounded correction verified or contract reauthorized |
| ACCEPTED_FOR_QA | Independent review cleared material blockers | Operator environmental/manual QA completed |
| RELEASE_AUTHORIZED | Engineer explicitly approves exact artifact | Deployment under separate release controls |
| CLOSED | Evidence, disposition and learning captured | N/A |

**BLOCKED / NO-GO** is a valid outcome from any pre-authorization or rework reassessment. A draft PR is not a release state.

## Standard flow

1. **Intake.** Preserve original screenshots/logs and describe what was actually observed. Separate repro from interpretation.
2. **Operator contract.** Define desired outcomes, valid/invalid journeys, roles, state transitions, data, failures and protected behavior. Record open decisions honestly.
3. **Maintainer discovery.** Inspect affected code at an exact SHA, trace connected APIs, storage, auth, UI and tests, then flag gaps.
4. **Reconciliation.** Resolve conflicts between desired and existing behavior. Each product decision requires operator authority.
5. **Gate.** Record GO / CONDITIONAL GO / NO-GO with evidence and frozen scope.
6. **Execution.** One writer implements a vertical slice, including negative behavior and tests. Material discoveries are escalated.
7. **Review.** An independent reviewer checks the changed risk surface and contract, not an improvised new wishlist.
8. **Acceptance.** Runtime, data and human journey evidence precede release authorization.

## Risk-scaled paths

**Short path:** Isolated deterministic defects with established contract and no material financial, security, authorization, migration or cross-module effect. Still record baseline, repro, expected behavior, test and exact SHA.

**Full path:** New workflows, payment/ledger/accounting logic, identity/role permissions, migrations, external integrations, offline synchronization, architectural redesign and broad UI+backend changes.

**Conditional path:** A mixed mission may contain ready and unready slices. Authorize only independent ready slices. Document the deferred ones with boundaries; do not call a partial implementation complete.

## Separation of discovery and verification

Discovery asks: *What should be built, what exists, and what else can be affected?*

Verification asks: *Did the frozen implementation satisfy the approved contract without violating protected invariants?*

A reviewer finding a previously unknown requirement is a **maintainer readiness escape**, not merely worker rework. A reviewer finding code contrary to an explicit requirement is normally a **worker implementation defect**. Both labels must be supported by evidence; causation can be shared.

## Non-interruption policy

When a worker is active, new ideas and noncritical findings are recorded for the next checkpoint. Interrupt only for a probable security exposure, data/financial integrity threat, destructive operation, unapproved scope change, or an invalidating business requirement. A maintainer does not micromanage mid-run because it has reconsidered its earlier instructions.

## Release principle

Implementation PASS, source-invariant PASS, build PASS, unit/API PASS, reviewer ACCEPT, installed runtime PASS and operator authorization are **distinct assertions**. Never collapse them into "done".
