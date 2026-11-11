# KirionForge

**An evidence-led engineering governance harness for human operators, AI maintainers, implementation workers, and independent reviewers.**

> Current established baseline: Maintainer Gate R1 · 2026-11-11  
> **R2-001 branch status: PROPOSED / NOT ADOPTED.** This draft revises authorization and feature-acceptance boundaries. The existing standard remains authoritative for active projects until their Engineer explicitly adopts an accepted revision. This repository is governance documentation, not executable verification or a reliability certification.

## Why this exists

Strong execution discipline does not compensate for an unready assignment. A screenshot proves an observed symptom; it does not automatically define a complete business workflow. A passing test proves its assertions, not that every affected contract was examined. A confident AI explanation is not evidence.

KirionForge closes the **maintainer readiness gap** between an operator's feature intent and a worker's authority to modify code. It is designed for linear development, cross-module change, and dynamic rework without turning review into delayed requirements discovery.

## The operating chain

**FEATURE INTENT → RISK-SCALED READINESS + GO → OWNED WRITER SLICES + LOCAL CHECKS → EARLY ISOLATED INTEGRATION → INDEPENDENT INTEGRATED-FEATURE REVIEW → FEATURE ACCEPTANCE → SEPARATE ENGINEER RELEASE AUTHORIZATION**

Worker session completion is a **handoff/evidence event**, not an acceptance gate. Critical security, financial, retained-data and irreversible-change boundaries retain early focused review and negative verification before unsafe integration. A feature's code may be integrated into an isolated, **unaccepted** candidate; stable or production promotion is never implied.

The conversation is not the system of record. The **versioned feature contract, evidence record, exact Git revision, and explicit decisions** are.

## Start here

| Document | Purpose |
| --- | --- |
| [Operating Model](docs/01-OPERATING-MODEL.md) | Authority, responsibility, workflow states and boundaries |
| [Maintainer Gate R1](docs/02-MAINTAINER-GATE.md) | Risk-scaled readiness checks and GO / CONDITIONAL GO / NO-GO decisions |
| [Context & Evidence](docs/03-CONTEXT-AND-EVIDENCE.md) | Anti-drift rules, provenance, claims and rehydration |
| [Dynamic Rework](docs/04-DYNAMIC-REWORK.md) | Severity, classification, interruption policy and bounded repair |
| [Measurement](docs/05-MEASUREMENT.md) | How to measure escapes and rework without invented statistics |
| [R2 Pilot & Compatibility](docs/06-R2-PILOT-AND-COMPATIBILITY.md) | Proposed replacement boundaries, compatibility and two sanitized pilot scenarios; not operational adoption |
| [Feature Contract](templates/FEATURE-CONTRACT.md) | Operator-provided, versioned intended behavior |
| [Readiness Decision](templates/READINESS-DECISION.md) | Maintainer evidence and executable authorization |
| [Rework Record](templates/REWORK-RECORD.md) | Triage for defects versus missing requirements |
| [Handoff Capsule](templates/HANDOFF-CAPSULE.md) | Compact state transfer across agents, chats and context windows |
| [Procurement Case](examples/PROCUREMENT-REWORK-CASE.md) | Anonymized case explaining the failure mode |

## Non-negotiable rules

1. **No implementation authorization from symptoms alone** when business behavior, permissions, money, lifecycle or persistence remain undefined.
2. **Unknown is not approved.** Maintain separate labels for observed, code-verified, test-verified, operator-approved, inferred, unknown and superseded claims.
3. **One active writer per owned change/path.** Multiple independent slices may run concurrently only with safe interface and ownership boundaries; independent reviewers do not become competing writers.
4. **Protect existing invariants.** Every feature contract includes what must not change.
5. **Risk determines gate depth.** A narrow, demonstrable bug may use an abbreviated gate; a financial or authorization-sensitive workflow may not.
6. **Independent judgment validates the frozen integrated feature and relevant critical pre-integration boundaries.** Local mechanical checks repeat as needed; a session end does not mandate formal review. New requirements return for operator decision, not silent implementation.
7. **No manufactured confidence rates.** Rework percentages and success probabilities require measured denominators and explicit methods.
8. **No release from green tests alone.** Local green, integrated green, independent acceptance, installed/QA evidence and operator release approval are distinct claims.
9. **No duplicate governance dependency for routine progress.** One durable, attributed feature contract/authorization plus issue/PR evidence suffices for ordinary handbacks; do not require a separate docs-only merge for every session or reviewer transition.

## What KirionForge is not

It is not a guarantee of bug-free code, a replacement for engineering judgment, a demand for heavy paperwork on minor fixes, or permission for an AI maintainer to decide product policy. It does not automatically operate on other repositories.

This public repository must contain **only sanitized examples**. Never copy private project code, customer data, credentials, screenshots, or internal audit artifacts here.

## Governance change rule

Changes to the maintainer gate are proposed as versioned documentation changes. A change to policy does **not** retroactively alter an active worker assignment, other repository's START/CLOSE protocol, or release authorization. This R2-001 proposal requires independent review, a bounded pilot, and explicit Engineer adoption before it becomes operational authority.

**Owner of business intent and release authority:** Human Engineer/Operator.  
**Owner of implementation readiness and evidence quality:** Maintainer.
