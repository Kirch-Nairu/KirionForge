# 05 — Measure Reliability Without Inventing It

> **R2-001 DRAFT / NOT ADOPTED.** Measure accepted client-usable feature throughput, not agent sessions or raw commit volume.

## Baseline warning

Neither a proposed "60% dynamic-rework failure rate" nor an AI-generated "75–85% acceptance chance" is a measured KirionForge statistic. Do not cite either as historical performance. A reliability estimate needs a defined outcome, observation window, population and denominator.

## Unit of analysis

**Feature:** One Engineer-authorized, client-observable outcome and approved contract revision, tracked from GO through integrated feature acceptance, hold or termination. Multiple worker sessions, code slices, commits, reviews and correction rounds belong to that feature; do not count each as another accepted unit. Track contract revisions separately, but preserve a stable feature ID so deliberate reauthorization cannot hide total delivery cost.

## Proposed measures

| Metric | Formula | Why it matters |
| --- | --- | --- |
| Readiness escape rate | GO feature revisions with material missing contract/requirement discovered after GO ÷ all GO feature revisions | Maintainer quality |
| First-pass integrated acceptance | Frozen integrated feature candidate accepted on first independent feature review ÷ integrated features receiving first review | Feature readiness / review quality |
| Worker implementation defect rate | Reviewed features with source behavior violating an explicit approved contract ÷ reviewed features | Worker quality |
| Test coverage escape rate | Reviewed integrated features with material approved behavior untested at first freeze ÷ reviewed integrated features | Acceptance design |
| Rework cycles per feature | Returned material findings/rework rounds per completed feature | Rework burden |
| Accepted-feature lead time | Timestamp of integrated feature acceptance minus original approved GO timestamp; report holds separately | End-to-end throughput |
| Manual authority interventions | Distinct human decisions or manual relays per feature, by reason | Engineer coordination burden |
| Formal judgment reviews per feature | Nonauthor substantive review events divided by features accepted | Gate amplification; interpret alongside escaped defects |
| Governance-only transitions | Number of mandatory docs-only merges, duplicate crosslinks or state-publication holds per feature | Avoidable bureaucracy |
| Integration defect/reconciliation count | Material compatibility, collision and failed integrated tests with source attribution | Late integration risk |
| Client-alignment rework count | Approved work materially revised because actual client-visible intent was missed or changed; identify which | Product alignment risk |
| Late operator decision rate | GO feature revisions requiring an operator policy decision after GO ÷ GO feature revisions | Readiness quality |
| Installed acceptance escape rate | Features with defects discovered in installed/manual QA after source review acceptance ÷ features reaching installed QA | Runtime realism |

Use separate severity bands. Do not treat a test-fixture mistake as an accounting code defect, or mix authorized scope changes with unplanned corrections.

## Data capture per mission

Capture feature ID, risk tier, contract revisions, approved GO timestamp, baseline SHA, writer sessions and ownership, integration SHA/time, reviewer events, test environment, actual acceptance time, manual coordination events, governance-only PRs, defect IDs, severity/classes, known scope changes, unresolved decisions, installed acceptance and release result. Mark missing times/effort as UNKNOWN; do not infer hours from GitHub comment counts or use hypothetical throughput models as measured results.

Record **known unknowns** that were explicitly accepted at CONDITIONAL GO; they are not automatically readiness escapes if isolated and honored.

## Interpretation

- Small samples produce unstable percentages. Publish counts with denominators (e.g., "2 of 7"), not falsely precise predictions.
- Compare like-for-like risk tiers. A copy fix and a financial ledger redesign have different failure surfaces.
- Reviewer strictness can change detection rates; a lower apparent defect rate can reflect weaker review.
- Avoid gameable targets such as "zero review comments." The objective is fewer **preventable late discoveries**, not fewer reported problems.
- Treat any probability forecast as a subjective judgment unless calibration data exists and methodology is disclosed.

## Initial measurement practice

First establish a baseline over a meaningful sequence of missions. A provisional review after roughly 20 or more comparable missions may be useful for discussion, but is **not** a statistically guaranteed threshold. Record event counts now; delay claims of reliable trend until evidence warrants them.

At each feature closeout, ask: Which finding was preventable by maintainer discovery? Which was a coding mistake? Which required operator policy? Which was genuinely unknowable before runtime? Which approval or duplicate publication changed no engineering decision? Track both gate cost and safety value rather than minimizing review counts in isolation.
