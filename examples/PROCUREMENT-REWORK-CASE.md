# Case Study — Procurement Correction Escapes (Sanitized)

> Methodological example drawn from a real multi-module POS procurement correction sequence. All repository names, exact source references, client details and private artifacts are deliberately omitted because KirionForge is public. This is a causal illustration, **not** a statistically validated study or live project status page.

## Observed incident pattern

An operator found obvious defects in an installed application: a PO action failed, a printable amount was invalid, and procurement/customer-order interfaces did not meet expected workflows. A corrective implementation also changed cashier access to purchase requests.

A Windows Release build passed. A focused lifecycle suite initially failed because the **test itself** tried to approve a PO that PR conversion had already approved. Correcting the test—not weakening the valid state machine—allowed the focused suites to pass.

An independent review later found two contract escapes:

1. The requester permission reused by a purchase-request workflow also exposed supplier/payment fields and permitted a supplier-quotation write. Role-based tests had checked some forbidden endpoints but not **all consumers of the shared permission**.
2. A printable PO fixed missing subtotal/tax values but omitted discount and shipping, despite those values contributing to the authoritative total. Tests lacked the nonzero-component document case.

These findings do not prove the implementation worker was intentionally producing a partial solution. They show that **requirements discovery, dependency mapping and test design were insufficiently complete at authorization**.

## Why these are different failures

| Finding | Proper classification | Maintainer action |
| --- | --- | --- |
| Invalid second-approval test | R2 — test/design defect | Correct test expectation; preserve valid production state transition |
| Shared permission leaking supplier data | R4/R3 — incomplete auth contract + coverage escape | Trace every permission consumer and sensitive field; obtain clear requester access policy |
| Incomplete monetary print components | R4/R3 — incomplete document/financial contract + coverage escape | Trace complete authoritative amount equation and rendered output |

The tests passing after the first repair did not prove the latter two untested cases.

## Prevention at Maintainer Gate

**Before authorizing cashier PR:**

- Explicitly enumerate the cashier's readable fields and permitted writes.
- Trace every route using the requester permission.
- Require a safe product/UOM catalog and negative supplier/quotation API tests.
- Preserve manager/admin procurement responsibilities.

**Before authorizing printed PO correction:**

- Read authoritative source fields and full arithmetic equation.
- Verify frontend type/normalization mapping and actual printed rows.
- Require a regression with nonzero discount, tax and shipping.
- Reject fake fallback totals when data is invalid.

## Learning

A review should verify the frozen contract. If it first has to discover the contract, record a **readiness escape**. This is shared process feedback, not a reason to bury findings or invent a precise likelihood of success.

This case documents a failure mode and a proposed control. It does not claim the gate has yet been empirically proven to reduce failures.
