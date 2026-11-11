# Maintainer Readiness Decision — R2-001 Template Selector

> **PROPOSED / NOT ADOPTED.** Choose a single template **for the feature/contract revision**, not for each worker session. The current project must explicitly authorize adoption before replacing its existing rules.

- **[COMPACT — LOW / MEDIUM](READINESS-DECISION-COMPACT.md)**: Eight fields covering outcome, authorization, exact source, boundaries, ownership, risk, tests and next action. Do not complete twelve irrelevant matrices for a small task.
- **[FULL — HIGH / CRITICAL](READINESS-DECISION-FULL.md)**: Detailed affected contract, source dependency, negative tests and explicit `PRE_INTEGRATION_HOLD` clearance for protected or high-consequence changes.

Risk names align with the Second Brain executable `LOW / MEDIUM / HIGH / CRITICAL` model; existing task-type floors and critical triggers remain authoritative. Do not classify a protected HIGH/CRITICAL scope as MEDIUM to avoid checks.

One approved GO may span multiple bounded sessions, but material policy/permission/migration discoveries suspend their affected scope and require an updated decision. For protected HIGH/CRITICAL work, a matching nonauthor `SECURITY_CLEARANCE` or applicable clearance with observed negative evidence is mandatory before integration. `LOCAL_VERIFIED` does not mean `FEATURE_ACCEPTED`; feature acceptance does not itself authorize merging to `main` or external release.

The project Engineer retains applicable decision rights and must explicitly adopt any new R2 policy before use in active work.
