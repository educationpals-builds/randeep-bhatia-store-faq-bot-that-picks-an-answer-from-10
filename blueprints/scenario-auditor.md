# Five-check auditor

## One-paste spec for conversational audit

This auditor walks five checks against any failing setup a stranger describes, then returns a scored audit with a severity story, a ship call, and a tripwire. The worked example below is grounded in a Store FAQ bot that picks an answer from the help center.

---

## What this auditor does

A stranger pastes:
1. What their failing setup is supposed to do
2. Who gets hurt when it fails
3. A few real failing inputs

The auditor walks five checks conversationally, proposes findings with the measurement that would confirm each, and returns:
- Scored ratings for all five checks
- A severity story naming the top crack
- A ship / ship-with-conditions / hold call with owners on any condition
- A tripwire with a number, a danger line, and a watcher

---

## Worked example: Store FAQ bot

**Specimen:** Store FAQ bot that picks an answer from the help center

**Stakes:** Shoppers get the wrong policy and leave the cart

**Standard line:** The answer matches the shopper's real ask — not a nearby FAQ about the same product

**Usage reality:** Short mobile questions with product names in the middle

**Source:** Store help-desk chat logs

### Failing inputs (verbatim)

```
how long do i have to return the Nova Buds after they ship
Nova Buds delivery says Friday — can i still cancel
refund for wrong size on the Trail Jacket, not a shipping question
```

---

## Five-check ratings (worked example)

| Check | Rating | What it measures |
|-------|--------|------------------|
| Unowned | 4 | Does any part of the system own this failure mode? |
| Copies | 2 | Are there duplicate or conflicting handlers? |
| Room | 1 | Is there space in the architecture to fix this? |
| Stitch | 2 | Do the pieces hand off cleanly? |
| Ablation | 1 | If you removed one piece, would you notice? |

**Top crack:** Unowned (rated 4)

---

## Severity story

No part of the system currently treats refund/return/cancel words as a priority signal. When a shopper types "how long do i have to return the Nova Buds after they ship," the bot latches onto "Nova Buds" and "ship" and returns shipping times instead of the return policy. The shopper gets the wrong policy and leaves the cart.

---

## Ship call (worked example)

Hold. No part of the system currently treats refund/return/cancel words as a priority signal — ship engineering lead needs to add a dedicated check before Black Friday. Reopen once the three specimen sentences all route correctly with refund words present.

---

## Tripwire (worked example)

Watch the count of tickets containing an explicit refund/return/cancel word that get answered with shipping content. If that exceeds 10 per day during sale week, CX manager escalates to engineering — because that's a fixable, specific miss, not noise.

---

## How a stranger uses this auditor

1. Paste your failing setup description (what it does, who gets hurt, 3+ real failing inputs)
2. The auditor walks each of the five checks, asking clarifying questions as needed
3. For each check, the auditor proposes a finding and names the measurement that would confirm it
4. The auditor returns:
   - A scored rating table (1–5 for each check)
   - The top crack with a severity story
   - A ship call with owners on any conditions
   - A tripwire with a number, a danger line, and a watcher

---

## Sample asks

**Stranger paste 1:**
> My support ticket router is supposed to send billing questions to the billing team, but it keeps routing them to general support when the customer mentions a product name. Last week three customers waited 48 hours for billing help. Here are real tickets that failed:
> - "I got charged twice for the Pro Plan, need a refund"
> - "Pro Plan billing issue — can someone fix my invoice?"
> - "why did my Pro Plan renewal cost more than last month"

**Stranger paste 2:**
> Our appointment reminder bot should send SMS reminders 24 hours before appointments, but it's sending reminders for cancelled appointments. Patients show up confused. Real failures:
> - Patient cancelled Monday, got reminder Tuesday morning
> - Rescheduled from 3pm to 5pm, got reminder for 3pm slot
> - Cancelled via phone call, system still sent SMS

The auditor walks all five checks against each stranger's setup, scores them, identifies the top crack, and returns a call and tripwire specific to their situation.
