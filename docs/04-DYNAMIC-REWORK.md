# 04 — Dynamic Rework Protocol

A rework is not automatically evidence of an incapable worker. Classify **what failed**, **why its acceptance basis failed**, and **who owns the missing decision** before issuing another task.

## Classification and routing

| Class | Evidence | Primary routing | Required action |
| --- | --- | --- | --- |
| R1 — Local implementation defect | Frozen contract unambiguous; code violates it | Single writer | Targeted repair + affected regression |
| R2 — Test/design defect | Test expects impossible state or misses its asserted contract | Writer + maintainer | Fix test specification; do not weaken valid production rules |
| R3 — Coverage escape | Requirement existed, but tests omitted relevant path | Maintainer + writer | Extend allow/deny/edge tests; patch only if behavior fails |
| R4 — Readiness/contract escape | Required business, financial or auth boundary missing at GO | Maintainer + operator | Reconcile and revise contract; reauthorize affected scope |
| R5 — Architecture/dependency discovery | Shared contract, migration or data path contradicts plan | Maintainer | Impact assessment; conditional continuation or NO-GO |
| R6 — New scope/change request | Feature addition not in approved contract | Operator | Version and schedule separately; do not smuggle into correction |
| R7 — Environmental failure | Toolchain, installer, permissions, fixture or host differs | Runtime QA / maintainer | Isolate environment; gather proof before changing application |
| R8 — Reviewer disagreement | Finding conflicts with documented policy or actual source | Maintainer + independent reviewer | Reproduce and adjudicate; no speculative patch |

A single incident may have contributing factors from multiple classes. Record primary and contributing causes; avoid blaming by model identity.

## Severity is separate from class

- **BLOCKER:** Strong evidence of data loss, privilege bypass, financial corruption, destructive migration, or an unapproved irreversible operation.
- **HIGH:** Violates material contract, confidentiality, accounting or acceptance boundary.
- **MEDIUM:** Functional/document/integration mismatch without demonstrated irreversible harm.
- **LOW:** Local polish, minor presentation or bounded noncritical test improvement.

Severity informs interrupt and release decisions. It does not prove root cause.

## During active implementation

**Do not interrupt** for newly imagined improvements, formatting or nonblocking observations. Queue them for the planned checkpoint.

**Interrupt and quarantine affected work** for credible blocker/high risk involving data security, financial integrity, destructive writes, significant unauthorized scope, or invalidated operator intent. Preserve worker state and stop potentially damaging operations; do not overwrite in-progress work.

If a new finding changes **the approved requirement**, revise contract and readiness decision before touching that behavior. If it simply shows a code deviation from an approved requirement, issue a bounded correction.

## Bounded correction packet

Every return to writer states:

1. Exact candidate SHA and contract revision.
2. Symptom, actual evidence and failure class/severity.
3. What existing behavior is correct and protected.
4. Minimal allowed source area and forbidden changes.
5. New positive, negative and edge assertions.
6. Tests to rerun; which prior evidence is unchanged.
7. Exit condition and handback SHA.

Avoid "fix everything," unbounded audits and implementation by reviewer.

## Test selection

- **Local error:** Affected test + directly coupled regression.
- **Shared API/auth/model change:** Enumerate all consumers of changed permission/model, run positive and denial tests across roles.
- **Money/state/persistence change:** Transaction, replay, compensation, audit and restart checks.
- **At frozen acceptance:** One independent review on exact SHA and appropriate integration/manual checks.

Never inherit a PASS for code that has changed on that test's dependency path. Never rerun all suites reflexively if a narrow test change is demonstrably isolated.

## Review dispositions

**ACCEPT FOR NEXT GATE:** No unresolved material findings within approved scope; exclusions explicit.

**RETURN FOR TARGETED REWORK:** Contract clear, defect localized; writer retains ownership.

**ESCALATE CONTRACT / NO-GO:** Material business ambiguity or architecture contradiction invalidates prior authority.

**DEFER SEPARATE CHANGE:** Legitimate new enhancement outside approved scope.

"Accepted for next gate" is **not** production approval.

## Closeout

A rework closes only when the relevant test evidence and reviewer disposition are attached to a new frozen SHA, and any contract revision is recorded. Recurrent escapes feed [Measurement](05-MEASUREMENT.md); avoid retroactively rewriting the original gate record.
