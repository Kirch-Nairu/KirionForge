# 02 — Maintainer Gate R1

**Decision owner:** Maintainer recommends. **Authority:** Engineer/Operator approves business decisions and may authorize execution. This is a process gate, not an automated code-quality certificate.

## Gate inputs

- Operator-owned [Feature Contract](../templates/FEATURE-CONTRACT.md), with revision and owner.
- Repro/evidence for defect work: environment, expected/actual, provenance.
- Source repository and **exact baseline commit**.
- Existing related specs, prior decisions, accepted behavior and protected constraints.
- Runtime and test capability inventory: what can be executed, by whom, and what remains unverified.

If an input cannot be obtained, record it as UNKNOWN and assess whether it blocks the specific scope.

## Seven maintainer checks

### G1 — Establish the problem

Identify the business purpose, actual symptom, affected roles and definition of success. Do not turn a screenshot's absence of a button into an invented authorization policy.

### G2 — Freeze a source baseline

Record owner/repository, base SHA, branch/PR relationships, known installed artifact (if any), data version and test environment. Verify the file/API mapping against that SHA. A stale path or another branch's implementation is not baseline proof.

### G3 — Trace the **affected contract surface**

Inspect only relevant dependencies, but trace them **end-to-end**:

| Surface | Questions |
| --- | --- |
| UI/navigation | How does each role reach it; what state and disabled actions appear? |
| API/permissions | Which endpoints reuse the permission; what data can each read/write? |
| Business state | Valid predecessors, terminal states, retries, idempotency, cancellation and reversals? |
| Financial arithmetic | All inputs and authoritative equation, rounding, discounts, taxes, fees and derived balances? |
| Persistence | Tables, migrations, keys, transactions, uniqueness, concurrency and restart behavior? |
| Audit | Who acted, on which entity, before/after state, reason, and atomicity? |
| Adjacent features | Which protected workflows share models, permissions or data mutations? |
| Runtime | What can be tested locally and what needs actual installed/manual evidence? |

Do not use the word "complete" if a material row was not examined.

### G4 — Reconcile intended and actual behavior

Record each discrepancy as: **operator-approved change, implementation defect, unresolved product decision, or unsupported assumption**. Ask the Engineer only for decisions with material consequences. The maintainer must not silently decide refund, credit, access or accounting rules.

### G5 — Define acceptance before implementation

For each material behavior, require a positive case, denial/invalid case, edge/replay case where applicable, and preservation test. Mark whether proof is source-only, unit, API, transaction, installed runtime, or manual operator. UI contracts need actual journey validation; printed amounts need rendered-document verification, not just numeric helper tests.

### G6 — Evaluate unknowns and risk

| Risk | Examples | Gate depth |
| --- | --- | --- |
| LOW | Local text, narrow deterministic mapping with known consumers | Abbreviated gate; focused regression |
| MODERATE | Role-specific UI, API mapping, shared state with bounded impact | Dependency trace + allow/deny and alternate-path tests |
| HIGH | Auth/data exposure, payments, stock/AR/AP, irreversible states, schema, offline sync | Full contract; transaction and negative tests; independent review; runtime acceptance |

Risk is based on plausible consequences, not diff size or perceived implementation difficulty.

### G7 — Issue written decision

**GO** if critical business rules are approved, high-risk dependencies are mapped, acceptance tests are executable or explicitly assigned, and protected constraints are clear.

**CONDITIONAL GO** if ready slices are independently bounded, remaining unknowns cannot affect authorized slices, and deferred scope is explicitly excluded.

**NO-GO** if material business policy, permission boundary, monetary equation, data ownership, migration safety or acceptance basis remains unknown; or if the baseline cannot be verified.

A NO-GO must say exactly **which missing decision/evidence** blocks work and **how to close it**. Do not create arbitrary paperwork or infinite research.

## Mandatory decision output

Use [Readiness Decision](../templates/READINESS-DECISION.md) with:

1. Current source SHA and contract revision.
2. Claims table: approved / verified / inferred / unknown, each with provenance.
3. Explicit authorized and forbidden scope.
4. Affected components and protected invariants.
5. Executable acceptance matrix, including negative tests and manual/installed gaps.
6. GO / CONDITIONAL GO / NO-GO and accountable sign-off.

**No implicit GO from a completed checklist.** The recorded decision is the permission to assign implementation.

## Guardrails against false readiness

- "Source compiled" is not "transaction correct."
- "Five suites passed" is not "every shared permission safe."
- "Code exists" is not "operator approved its behavior."
- "No failure found" is not "no defect exists."
- "AI estimated 85% likely" is not a calibrated prediction.
- Missing material inputs are not replaced by plausible narratives.

## Handling newly discovered material facts

**Before execution:** Revise gate and contract before GO.

**During execution:** Classify impact; interrupt only under the critical stop policy, otherwise checkpoint the discovery. If it changes authorized behavior, update contract version and reauthorize affected scope before worker modifies it.

**After frozen review:** Return bounded code defects to the writer; return policy/contract gaps to maintainer + operator. Review cannot silently redefine intent.

## Acceptance conditions for this gate itself

An independent person should be able to open the gate record and answer: What source did we inspect? What did the operator approve? What can the writer change? What must remain unchanged? What will count as success or denial? What remains unknown? Who authorized it?
