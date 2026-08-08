# Five-check auditor

A tool that walks five checks on any failing setup and returns a scored audit with a severity story, a call, and a tripwire.

---

## Worked example: Store FAQ bot that picks an answer from the help center

**What goes wrong:** Shoppers get the wrong policy and leave the cart

**The standard:** The answer matches the shopper's real ask — not a nearby FAQ about the same product

---

## Verdict

**Hold.** No part of the system currently treats refund/return/cancel words as a priority signal — ship engineering lead needs to add a dedicated check before Black Friday. Reopen once the three specimen sentences all route correctly with refund words present.

---

## Tripwire

Watch the count of tickets containing an explicit refund/return/cancel word that get answered with shipping content. If that exceeds 10 per day during sale week, CX manager escalates to engineering — because that's a fixable, specific miss, not noise.

---

## Check scores

| Check | Score |
|-------|-------|
| unowned | 4 |
| copies | 2 |
| room | 1 |
| stitch | 2 |
| ablation | 1 |

**Deciding check:** unowned

---

## Real failing inputs

Source: Store help-desk chat logs

```
how long do i have to return the Nova Buds after they ship
Nova Buds delivery says Friday — can i still cancel
refund for wrong size on the Trail Jacket, not a shipping question
```

---

## One-paste rebuild block

Copy this into your audit session to reproduce the worked example:

```
Specimen: Store FAQ bot that picks an answer from the help center
Stakes: Shoppers get the wrong policy and leave the cart
Standard: The answer matches the shopper's real ask — not a nearby FAQ about the same product
Usage reality: Short mobile questions with product names in the middle

Failing inputs:
- how long do i have to return the Nova Buds after they ship
- Nova Buds delivery says Friday — can i still cancel
- refund for wrong size on the Trail Jacket, not a shipping question

Source: Store help-desk chat logs
```

---

## What a stranger gets

Describe your own failing setup — what it's supposed to do, who gets hurt when it fails, and a few real failing inputs. The Five-check auditor walks all five checks conversationally, proposes findings with the measurement that would confirm each, and returns a scored audit with a severity story, a call (ship / ship-with-conditions / hold), and a tripwire with a number, a danger line, and a watcher.

---

See [charter.md](charter.md) for the full audit.  
See [METHOD.md](METHOD.md) for the five-check framework.  
See [VERIFY.md](VERIFY.md) for stranger verification steps.

<!-- educationpals-build-verified -->
