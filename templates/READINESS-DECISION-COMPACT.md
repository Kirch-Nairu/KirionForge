# Maintainer Readiness Decision — COMPACT (LOW / MEDIUM)

> **R2-001 proposal / NOT ADOPTED.** Eight operational fields. Reuse the same feature GO across sessions and local corrections. If a protected HIGH/CRITICAL dependency is discovered, **suspend the affected slice** and use [full readiness](READINESS-DECISION-FULL.md); do not pretend a compact GO authorized the new boundary.

1. **Feature ID / approved outcome and contract revision:**
2. **Engineer authorization record (who, when, GO / CONDITIONAL GO / NO-GO):**
3. **Repository@exact baseline SHA and allowed owner/paths:**
4. **Required behavior and forbidden/regression-sensitive behavior:**
5. **Risk: LOW / MEDIUM (from four-tier model); dependencies / escalation signals:**
6. **Writer and integration owner; noncolliding scope and exclusions:**
7. **Required local checks + final integrated primary journeys/contract assertions (command/environment/NOT_RUN owner):**
8. **Open blockers/deferred decisions, exact next action and invalidation trigger:**

**Usage:** Keep this in the existing issue/PR or linked contract record. The maintainer verifies the affected sources and recommends GO; the Engineer remains responsible for materially consequential business decisions. For MEDIUM, run **every defined primary journey and feature-contract acceptance assertion on the final integrated SHA**, including relevant denied paths. Independent feature review still applies. Routine context resets, handoffs and new commits do **not** require a new GO or docs-only START/CLOSE publication.

**Escalation:** Newly found sensitive auth/data, financial, migration, irreversibility or other protected boundaries invalidate the relevant compact authorization; tag `PRE_INTEGRATION_HOLD=ACTIVE`, stop that affected slice, update risk/contract and obtain applicable nonauthor clearance before integration. Never infer PASS from omitted evidence. `FEATURE_ACCEPTED` is neither stable-trunk merge permission nor production release authority.
