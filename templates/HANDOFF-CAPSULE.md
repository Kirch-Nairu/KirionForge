# KirionForge Handoff Capsule — TEMPLATE

> R2-001 proposed format. A session handback is **not** an independent review, new readiness GO or feature acceptance. Use this capsule only when a material state delta needs transfer.

Compact, factual state transfer for an AI context reset, new maintainer, writer or reviewer.

- Feature ID / approved outcome:
- Session or slice ID (optional; not acceptance unit):
- Mission:
- Repository and relevant private/public classification:
- Technical authority / approved business owner:
- **Feature contract revision and location:**
- **Maintainer gate decision and location:**
- **Baseline SHA:**
- **Frozen candidate SHA (if any):**
- Branch / PR relationship:
- Feature lifecycle state: INTAKE / DISCOVERY / CONTRACT_READY / AUTHORIZED / IMPLEMENTING / LOCAL_VERIFIED / INTEGRATED_CANDIDATE / UNDER_REVIEW / TARGETED_REWORK / FEATURE_ACCEPTED / RELEASE_AUTHORIZED / CLOSED / BLOCKED
- Last event: SESSION_HANDOFF / COMMIT_PUSHED / LOCAL_TEST / INTEGRATED / REVIEWED / OTHER (not automatically a state transition)
- Approved GO / authority link (reuse until materially changed):
- Integrated candidate SHA (if any):
- Risk tier and active pre-integration hold (if any):
- Active sole implementation writer:
- Independent reviewer:
- Protected invariants:

## Verified facts only

| Claim | Evidence label | Precise source + SHA/log | Status |
| --- | --- | --- | --- |
| | | | |

## Open unknowns / decisions

| Item | Impact | Decision owner | Next evidence |
| --- | --- | --- | --- |
| | | | |

## Latest test and review evidence

- Command / environment / result / exit:
- Scope of what that test actually proves:
- Formal review findings still open (if any; not mandatory per session):
- Which exact tests/reviews become invalid on the next changed dependency path:

## Next authorized action

**Allowed next action:**

**Forbidden actions:**

**Stop / escalate condition:**

**No inferred success:** On resumption, recheck relevant source/contract/issue pointers and current head. Do not force a full-history reload or reapproval where neither scope nor authority changed. This capsule is a pointer to source evidence, not proof by itself. Do not publish private paths or incident details into this public template repository.
