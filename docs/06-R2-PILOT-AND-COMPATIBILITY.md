# 06 — R2-001 Pilot and Compatibility Plan

> **PROPOSAL ONLY / NOT ADOPTED.** This document tests whether feature-scoped authorization, local candidate checks and integrated acceptance preserve useful controls at lower coordination cost. It does not change rules in another repository, authorize release or prove improved throughput.

## Exact proposal boundary

1. **What changes:** A valid, Engineer-approved feature contract plus one recorded maintainer GO can authorize several sequential worker sessions and independent noncolliding slices. A routine chat reset, local revision, reviewer dispatch or PR checkpoint does **not** require an additional mandatory docs-only merge and paired START/CLOSE publication.
2. **What stays:** Named human accountability, permitted paths/ownership, actual source SHA and contract revision, mechanical per-candidate tests, critical-risk pre-integration review, exact integrated validation, nonauthor judgment for material feature acceptance, installed/manual proof where necessary, and explicit human release decision.
3. **What is not automatic:** No GO merely from a template, no automatic merger into stable, no self-approved security exception, no permission to use external systems, no policy change to ongoing missions, and no retroactive grandfathering of previously unreviewed source.

## Boundary and transition tests

| ID | Given | Action | Required result |
| --- | --- | --- | --- |
| T-01 | Approved LOW feature, unchanged contract | Writer ends session; another bounded session resumes | Reuse original GO and source/issue links; new SHA and changed evidence recorded; **no extra formal acceptance** |
| T-02 | Two nonconflicting authorized slices | Each runs scope/build/tests; integration owner composes | Isolated `INTEGRATED_CANDIDATE` permitted; **not** `FEATURE_ACCEPTED` or release-authorized |
| T-03 | Shared consumer/API change | Integrator sees altered interface | Affected compatibility and allow/deny tests run; incompatible slice held until fixed |
| T-04 | Material permission or financial rule missing | Writer proposes behavior | Affected work stops; specific human contract decision required; independent safe work may continue |
| T-05 | CRITICAL sensitive storage/auth/migration scope | Worker asks to integrate before security holds cleared | Integration of risk-bearing changes blocked; early independent inspection and negative checks required |
| T-06 | Frozen integrated feature and relevant evidence | Independent reviewer evaluates | Findings tied to exact integrated SHA/contract, feature accepted only on justified disposition |
| T-07 | Local correction after review | Writer fixes one bounded defect | Rerun invalidated checks, targeted independent disposition on old finding; do not restart untouched feature checks |
| T-08 | Independently reviewed integrated candidate | Installed runtime/manual QA fails | Feature/release held; correct and revalidate relevant consumer or artifact |
| T-09 | Valid feature acceptance | Someone requests production merge/deploy | Distinct Engineer release authorization and project-specific controls still required |
| T-10 | Old project has mandatory two-record START/CLOSE protocol | R2 candidate PR exists only here | **No operational override** until that project expressly approves its migration and compatibility controls |

## Sanitized pilot A — isolated presentation defect

**Scope:** An already-authorized navigation disclosure clips inside a narrow sidebar. The accepted behavior and affected components are known. No sensitive data, permissions, finance, migration or external I/O changes.

**Legacy path to compare:** writer output → formal reviewer → targeted rework → independent rereview → separate readiness-acceptance event → integration. Measure meaningful defect discovery separately from authorization/relay events.

**R2 path to simulate:** feature GO once → bounded writer/source tests → isolated integrated candidate → independent integrated UI/source assessment → targeted correction of the clipping defect, if necessary → affected checks and reviewer finding closure → feature acceptance. Browser/mobile and keyboard evidence are required where visual reachability cannot be established from code. Never turn `NOT_RUN` into `PASS`.

**Pilot question:** Can the same defect be detected and corrected without separate human judgment simply to move corrected source between process states?

## Sanitized pilot B — protected document custody

**Scope:** A nonpublic document-custody module with actor/office authorization, idempotent retries, scanner evidence, isolated storage, and irreversible/data-retention concerns.

**Required before any sensitive integration:** Approved actor/service/office ownership contract; deny-by-default storage root; negative replay/disk/permission tests; focused independent source/security inspection; explicit hold for unexercised real infrastructure controls. A local green unit suite is not sufficient.

**Integrated acceptance:** Verify actual consumer permissions, persistence, replay boundaries and targeted security regressions at the combined SHA. The independent reviewer may reopen a finding when altered code invalidates the original inspection; unrelated passing evidence remains intact.

**Pilot question:** Does R2 preserve detection of privilege/storage failures while eliminating redundant administrative transactions surrounding legitimate repeated corrections? Failure to detect a material issue that the legacy process found is a failed pilot, not evidence that gates should be reduced further.

## Comparison method

Capture from real source/issue/PR/test history where available: feature GO timestamp; first local green; integrated-candidate timestamp; formal review start/finish; feature acceptance; number and type of **manual** Engineer interventions; mandatory governance-only commits; repeat reviews; material confirmed findings; baseline-vs-integrated defects; and installed/client acceptance. Distinguish waiting from actual work and unknown effort from observed elapsed time.

**Do not** manufacture hours saved, infer read-time from comment size or use hypothetical fleet stress-test numbers as evidence. Report both the number of removed coordination actions and whether any meaningful security/functional defect would have escaped.

## Adoption, compatibility and rollback

- Stage this R2 proposal solely in `Kirch-Nairu/KirionForge` as a draft PR; run independent read-only coherence review first.
- Reconcile naming and state transitions with existing historical Forge and its Second Brain before changing any executable state machine.
- Pilot in isolated, unaccepted candidates; **no live client repository protocol edits** are authorized by this document.
- If a pilot shows a material escaped defect, unreviewed critical integration, ambiguous human authority, or irreproducible acceptance state, **hold adoption**, correct the proposal and rerun the failed scenario.
- Adoption requires an explicit Engineer decision, version/effective date, transition plan for ongoing work and precise superseded rules; preserve historical records and existing work authorization.
- Old assignments remain governed by the version under which they were authorized until an accountable project owner deliberately migrates them. No bulk conversion or automatic promotion.

**Exit:** One coherent proposed lifecycle, two risk-differentiated dry runs, no proven critical-control regression, honest event-count comparison and an independent recommendation. This is a review gate for the *policy change*, not an extra gate to impose on ordinary feature execution.
