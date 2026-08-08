# Verification: Store FAQ bot that picks an answer from the help center

Use this checklist to confirm the Five-check auditor surfaces the correct findings when a stranger runs it against the sample setup.

---

## Setup to test

Paste this failing-setup description into `/play`:

> **What's broken:** Store FAQ bot that picks an answer from the help center  
> **What goes wrong if unfixed:** Shoppers get the wrong policy and leave the cart  
> **How you'll know it's fixed:** The answer matches the shopper's real ask — not a nearby FAQ about the same product  
> **Real inputs look like:** Short mobile questions with product names in the middle  
> **Three failing messages:**  
> - how long do i have to return the Nova Buds after they ship  
> - Nova Buds delivery says Friday — can i still cancel  
> - refund for wrong size on the Trail Jacket, not a shipping question  
> **Source:** Store help-desk chat logs

---

## What the tool must surface

### 1. Deciding-check finding

The auditor must identify **unowned** as the top crack — the check that decides the verdict.

Confirm the output names this check and explains why it's the decider for this specimen.

### 2. Numeric measurement demand

The auditor must demand a specific, countable measurement for the unowned finding — not a vague "monitor it" instruction.

For this specimen, the measurement is:

> Watch the count of tickets containing an explicit refund/return/cancel word that get answered with shipping content. If that exceeds 10 per day during sale week, CX manager escalates to engineering — because that's a fixable, specific miss, not noise.

Confirm the tool asks for or proposes a number (e.g., tickets per day) and a threshold (e.g., 10) that would confirm the finding.

### 3. Call with owner

The auditor must return a ship/hold/ship-with-conditions call that names an owner for any condition.

For this specimen, the call is:

> Hold. No part of the system currently treats refund/return/cancel words as a priority signal — ship engineering lead needs to add a dedicated check before Black Friday. Reopen once the three specimen sentences all route correctly with refund words present.

Confirm the output includes a position (Hold), an owner (engineering lead), and a checkable condition (three specimen sentences route correctly).

---

## Pass criteria

| Check | Pass if… |
|-------|----------|
| Deciding check surfaced | Output names **unowned** as the top crack |
| Measurement demanded | Output specifies a count + threshold (e.g., 10 misrouted tickets/day) |
| Call with owner | Output states Hold + names engineering lead + states reopen condition |
| Tripwire present | Output includes who watches (CX manager) and escalation trigger |

If all four pass, the auditor is working correctly for this specimen domain.
