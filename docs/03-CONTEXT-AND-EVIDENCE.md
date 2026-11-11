# 03 — Context Integrity & Evidence Discipline

## The problem

AI context windows, conversation summaries and agent handoffs are useful transports, **not an authoritative project database**. Over long work, a source fact can be compressed, detached from its revision, repeated as a conclusion, then mistaken for an approved requirement. Confidence and fluency do not prevent this.

## Durable sources of truth

Maintain separate, versioned records:

1. **Feature Contract:** Operator-approved intended business behavior.
2. **Readiness Decision:** Maintainer's verified current-code map, unknowns and execution scope.
3. **Implementation/PR:** Actual source diff at exact SHA and test evidence.
4. **Review Record:** Findings, severity, scope and independent disposition.
5. **Runtime/Acceptance Record:** Exact built/installed artifact and operator-observed result.
6. **Rework Record:** Classification, revised authority and bounded rerun evidence.

Conversations may point to these records; they do not replace them.

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

## Rehydration before making decisions

At every context-window reset, new agent, long pause, revised branch, or conflicting summary:

- Read the authoritative contract and readiness decision **from storage**.
- Recheck actual source head and branch ancestry; do not reuse a historical SHA as current.
- Load unresolved decisions and active rework records.
- Verify who is the active writer and whether any work is frozen.
- Identify old claims now SUPERSEDED.
- Recreate a [Handoff Capsule](../templates/HANDOFF-CAPSULE.md) containing exact refs and open gates.

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

One source writer per change. Reviewer is read-only unless operator explicitly reassigns the role. Never let two workers correct the same branch concurrently. Different models do not create independence unless their responsibilities and evidence are separated.

Review findings attach to **candidate SHA**; after a new commit, only unchanged relevant findings can be inherited. Runtime evidence remains tied to the build it tested.

## Privacy

This repository is public. Use sanitized examples and references only. Private code, customer identifiers, security material, local database contents, credentials and original client screenshots must stay in their authorized private systems. A public methodology is not permission to publish a private incident.
