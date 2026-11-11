# 03 — Context Integrity & Evidence Discipline

> **R2-001 DRAFT / NOT ADOPTED.** Evidence and authority are retained; routine work does not require duplicate publication transactions.

## The problem

AI context windows, conversation summaries and agent handoffs are useful transports, **not an authoritative project database**. Over long work, a source fact can be compressed, detached from its revision, repeated as a conclusion, then mistaken for an approved requirement. Confidence and fluency do not prevent this.

## Durable sources of truth

Maintain distinct **facts and decision types** in linked durable sources, not necessarily six separately committed files or approval packages:

1. **Feature Contract:** Operator-approved intended business behavior.
2. **Readiness Decision:** Maintainer's verified current-code map, unknowns and execution scope.
3. **Implementation/PR:** Actual source diff at exact SHA, owned paths, local mechanical checks and integrated candidate reference.
4. **Review Record:** Risk-triggered early security findings and/or independent integrated feature judgment, with reviewed SHA and disposition.
5. **Runtime/Acceptance Record:** Exact executable/installed artifact, relevant user journeys and operator-observed result.
6. **Rework Record:** Classification, changed dependency surface, retained-valid evidence and bounded rerun proof.

Conversations may point to these records; they do not replace them. **A single issue/PR plus linked feature contract and evidence manifest may hold these records**; there is no universal requirement for an independently merged docs-only START/CLOSE on canonical main before each worker session, candidate handback, reviewer invocation or routine correction. A formal approval must remain explicit and attributable.

## Evidence labels

| Label | Meaning | Minimum provenance |
| --- | --- | --- |
| OBSERVED | Reproduced or supplied actual behavior | Actor, date, environment, screenshot/log/reference |
| CODE_VERIFIED | Confirmed in actual source | Repo, commit SHA, path and relevant lines |
| TEST_VERIFIED | Executed test and obtained result | SHA, command, environment, exit/status and log |
| OPERATOR_APPROVED | Explicit business decision from responsible human | Decision, author, timestamp, contract revision |
| INFERRED | Reasonable explanation not directly proven | Reasoning and missing proof |
| UNKNOWN | Not yet established | Impact and required next evidence |
| SUPERSEDED | Earlier claim invalidated by newer evidence/decision | Replacement reference and effective revision |

Never promote INFERRED to CODE_VERIFIED, TEST_VERIFIED or OPERATOR_APPROVED just by repeating it.

## Claim ledger format

| ID | Claim | Status | Source ref / SHA | Checked by / when | Consequence if false |
| --- | --- | --- | --- | --- | --- |
| C-001 | Example: requester may create PR | OPERATOR_APPROVED | Feature contract R2 §Roles | Engineer / date | Unauthorized access |
| C-002 | Example: endpoint shares manage permission | CODE_VERIFIED | Repository SHA + file:lines | Maintainer / date | Broad privilege |
| C-003 | Example: installed app renders PO correctly | UNKNOWN | QA pending | — | Misleading vendor document |

Example claims are illustrative, **not actual approval**.

## Minimal evidence manifest and state transfer

At each meaningful feature boundary, retain: `feature_id`, `approved_contract_revision`, `authority_ref`, `baseline_sha`, `candidate_sha`, `integrated_sha` (if any), `owned_paths`, `risk_tier` (LOW/MEDIUM/HIGH/CRITICAL), `pre_integration_hold` and exact-SHA nonauthor `clearance` where applicable, `tests_run` (command/environment/exit/artifact), `tests_not_run`, `review_findings`, `open_blockers`, `next_owner_action`. Do not manufacture a SHA where the operation has not happened.

A session handoff is a **delta event**, not a new GO/ACCEPT/RELEASE decision. Update the existing issue/PR or concise [Handoff Capsule](../templates/HANDOFF-CAPSULE.md) only when source, scope, evidence, blocker or next action changed; otherwise reuse the last verified pointer. Keep local and branch snapshots distinguishable from the currently authoritative contract and current Git ref.

When references conflict, resolution order is: explicit current Engineer/authorized business decision for intent; approved contract revision for behavior; actual Git and executed evidence for implementation; linked reviewer/QA decisions for acceptance. A historical `SSOT_CURRENT` narrative or branch-local copy must not silently override newer verified decisions.

## Rehydration before making decisions

At every context-window reset, new agent, long pause, revised branch, or conflicting summary:

- Read the latest authoritative contract revision, scope and GO/hold record from their durable links.
- Recheck current source head and integration branch ancestry; do not reuse a historical SHA as current.
- Load only affected unresolved decisions, dependency changes and active rework findings.
- Verify path ownership, pending critical holds and which evidence remains valid.
- Identify contradicted historical claims as SUPERSEDED, not as current decisions.
- Rehydrate a compact [Handoff Capsule](../templates/HANDOFF-CAPSULE.md) from those pointers when actual context is needed; do not copy entire review histories.

If a cited private source is inaccessible, label the claim UNVERIFIED in the current session. Do not silently pretend to have inspected it.

## Anti-hallucination discipline

- Quote or paraphrase only accessible evidence and separate facts from hypotheses.
- Never invent results of builds, tests, GitHub CI, database queries, screenshot inspections or user approvals.
- Do not invent source paths, line numbers, commits or claims of completeness.
- If the review scope is partial, report partial coverage and explicit exclusions.
- Use immutable SHA and contract version in handoffs; branch names alone move.
- A passed test is scoped to its checked assertions and environment.
- When evidence conflicts, record both and stop relying on the disputed claim until reconciled.

## Multi-agent write discipline

One active source writer per owned path/change; multiple independent slices may proceed under the same feature authorization when collisions and shared contracts are controlled. A dedicated integration writer combines approved-to-integrate slices without granting acceptance. A reviewer is read-only for the code it assesses. Never let two writers correct the same branch or shared path concurrently. Different models do not create independence unless their responsibilities and evidence are separated.

Local mechanical checks attach to each checked candidate SHA. Formal independent **feature** findings attach to the integrated SHA and approved contract revision; HIGH-protected/CRITICAL clearance records attach to the exact risk-bearing candidate and record whether a protected trust boundary was actually cleared. A blank or NOT_RUN clearance cannot be inferred from a green local build. After a new commit, inherit only evidence whose checked dependency paths and assumptions remain unchanged. Runtime evidence stays tied to the artifact/configuration it actually tested.

## Privacy

This repository is public. Use sanitized examples and references only. Private code, customer identifiers, security material, local database contents, credentials and original client screenshots must stay in their authorized private systems. A public methodology is not permission to publish a private incident.
