# 05 — Measure Reliability Without Inventing It

## Baseline warning

Neither a proposed "60% dynamic-rework failure rate" nor an AI-generated "75–85% acceptance chance" is a measured KirionForge statistic. Do not cite either as historical performance. A reliability estimate needs a defined outcome, observation window, population and denominator.

## Unit of analysis

**Mission:** One operator-authorized implementation scope and contract revision, tracked from GO decision to acceptance or termination. Count multiple commits and returns under the same mission, not as independent missions. Reauthorized scope expansion starts a new contract revision and should be tracked separately.

## Proposed measures

| Metric | Formula | Why it matters |
| --- | --- | --- |
| Readiness escape rate | GO missions with material missing contract/requirement discovered post-GO ÷ all GO missions | Maintainer quality |
| First-pass review acceptance | Frozen candidate accepted on its first independent review ÷ candidates receiving a first review | End-to-end handoff quality |
| Worker implementation defect rate | Missions with source behavior violating an explicit approved contract ÷ reviewed missions | Worker quality |
| Test coverage escape rate | Missions with material approved behavior untested at first freeze ÷ reviewed missions | Acceptance design |
| Rework cycles per mission | Number of returned frozen candidates ÷ missions completed | Rework burden |
| Late operator decision rate | Missions requiring an operator policy decision after GO ÷ GO missions | Readiness quality |
| Installed acceptance escape rate | Missions with defects discovered in installed/manual QA after source review acceptance ÷ missions reaching installed QA | Runtime realism |

Use separate severity bands. Do not treat a test-fixture mistake as an accounting code defect, or mix authorized scope changes with unplanned corrections.

## Data capture per mission

Capture mission ID, risk tier, approved contract revision, GO decision date, baseline SHA, writer, reviewer, test environment, number of freeze/review rounds, finding IDs, severity, rework classes, unresolved decisions, installed acceptance and release result.

Record **known unknowns** that were explicitly accepted at CONDITIONAL GO; they are not automatically readiness escapes if isolated and honored.

## Interpretation

- Small samples produce unstable percentages. Publish counts with denominators (e.g., "2 of 7"), not falsely precise predictions.
- Compare like-for-like risk tiers. A copy fix and a financial ledger redesign have different failure surfaces.
- Reviewer strictness can change detection rates; a lower apparent defect rate can reflect weaker review.
- Avoid gameable targets such as "zero review comments." The objective is fewer **preventable late discoveries**, not fewer reported problems.
- Treat any probability forecast as a subjective judgment unless calibration data exists and methodology is disclosed.

## Initial measurement practice

First establish a baseline over a meaningful sequence of missions. A provisional review after roughly 20 or more comparable missions may be useful for discussion, but is **not** a statistically guaranteed threshold. Record event counts now; delay claims of reliable trend until evidence warrants them.

At each closeout, ask: Which finding was preventable by maintainer discovery? Which was a coding mistake? Which required operator policy? Which was genuinely unknowable before runtime? Use the answers to improve gates rather than add indiscriminate paperwork.
