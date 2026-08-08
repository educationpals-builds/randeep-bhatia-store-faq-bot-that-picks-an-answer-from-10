# The PRISM Framework

When a setup claims to split work across multiple checks, heads, or routing paths, use these five principles to audit whether the split actually happens.

---

## P — Partition the Space

Every possible input must land in exactly one bucket. If two checks can both claim the same message, or if some messages fall through with no check claiming them, the partition is broken.

**What to measure:** Count inputs that trigger zero checks or multiple checks. A clean partition means every input fires exactly one.

---

## R — Run in Parallel

Each check should operate independently. If check B can only run after check A finishes, or if check A's output changes what check B sees, you have a dependency chain masquerading as parallel checks.

**What to measure:** Trace the execution order. Document any check that waits on another or reads another's intermediate state.

---

## I — Individuate the Pattern

Each check must recognize a distinct signal. If two checks both fire on the same keywords, or if one check is a strict subset of another, you have redundant heads pretending to be separate.

**What to measure:** List the trigger conditions for each check. Flag any overlap where the same input feature activates multiple checks.

---

## S — Stitch the Spectra

When checks produce different kinds of outputs (confidence scores, category labels, extracted entities), something must combine them into a single decision. If the stitching logic is missing or defaults to "first one wins," the split is cosmetic.

**What to measure:** Document the merge rule. Confirm it handles conflicts explicitly rather than by accident of execution order.

---

## M — Map What Each Head Sees

Each check should have a defined input scope. If all checks see the full input but only care about part of it, you risk one check latching onto a feature meant for another.

**What to measure:** For each check, list what portion of the input it actually uses. Flag checks that scan the whole input but only need a fragment.

---

## The Collapse-to-Monochrome Anti-Pattern

A system looks like it has multiple checks, but in practice one check dominates. The others either never fire, always defer, or get overridden. The "split" exists in the code but not in the behavior.

**How to detect it:** Run a sample of real inputs and count how often each check is the deciding factor. If one check decides 90%+ of cases, the others are decorative.

**Why it matters:** Teams believe they have coverage they don't have. When the dominant check fails, there's no backup — the other checks were never really working.

---

## Using PRISM in an Audit

Walk each principle in order. For every finding, name the specific measurement that would confirm or refute it. A check that "seems fine" without a number is not a finding — it's a guess.

The goal is a scored audit where each principle gets a rating, the weakest principle gets called out as the decider, and the final call (ship / hold / ship-with-conditions) traces back to that decider.
