# Audit: Store FAQ bot that picks an answer from the help center

## Specimen under review

**Tool:** Store FAQ bot that picks an answer from the help center

**Stakes if unfixed:** Shoppers get the wrong policy and leave the cart

**Standard for success:** The answer matches the shopper's real ask — not a nearby FAQ about the same product

---

## Real inputs

**Usage pattern:** Short mobile questions with product names in the middle

**Source:** Store help-desk chat logs

### Failing messages (verbatim)

1. how long do i have to return the Nova Buds after they ship
2. Nova Buds delivery says Friday — can i still cancel
3. refund for wrong size on the Trail Jacket, not a shipping question

---

## Five-check ratings

| Check | Score |
|-------|-------|
| unowned | 4 |
| copies | 2 |
| room | 1 |
| stitch | 2 |
| ablation | 1 |

---

## Deciding check

**Top crack:** unowned

The system scores highest (worst) on the unowned check. No part of the routing logic currently owns the refund/return/cancel signal — it falls through to whatever else matches, which is shipping content keyed to the product name.

---

## Call

Hold. No part of the system currently treats refund/return/cancel words as a priority signal — ship engineering lead needs to add a dedicated check before Black Friday. Reopen once the three specimen sentences all route correctly with refund words present.

---

## Tripwire

Watch the count of tickets containing an explicit refund/return/cancel word that get answered with shipping content. If that exceeds 10 per day during sale week, CX manager escalates to engineering — because that's a fixable, specific miss, not noise.

---

## Summary

This audit examined a store FAQ bot that routes shopper questions to help-center answers. The bot currently latches onto product names and returns shipping content even when the shopper explicitly asks about refunds, returns, or cancellations. The unowned check is the decider: no component in the system prioritizes refund-family words. Until engineering adds that dedicated check, the bot should not ship for the sale week. After release, the CX manager watches for refund-word tickets answered with shipping content — 10 per day triggers escalation.
