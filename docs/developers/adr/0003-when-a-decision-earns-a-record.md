---
status: accepted
date: 2026-11-12
decision-makers: jim@openphase-labs.com
---

# A decision earns a record when reversing it is expensive or constrains work not yet done

## Context and Problem Statement

A set that records everything stops being read; a set that records too little loses the
decisions that felt obvious, which are the ones nobody later recognises as decisions.
The threshold has to be stated, or it drifts with whoever is writing.

## Decision Drivers

* The set stays short enough to be read.
* Expensive decisions are recorded even when nobody disputed them.
* The threshold is the same whoever is writing.

## Considered Options

* A record when any of three stated criteria holds
* A record per change or pull request
* A record only where there was disagreement
* A record for every decision, split into tiers

## Decision Outcome

Chosen option: "A record when any of three stated criteria holds", because it captures
the expensive and the uncontroversial decisions without turning the set into a changelog.

A decision earns a record when any of these holds:

* Reversing it is expensive -- in data, deployed installations, published contracts, or
  work that would have to be redone.
* It constrains work not yet done, and a future developer could not otherwise know.
* A later reader would plausibly propose the rejected option again.

These do not earn a record:

* Names, module decomposition, and the ordinary structure of code.
* Reversible choices inside an architecture a record already settles.
* Detail that emerges while implementing a decision already recorded.
* A choice nobody made.

A decision nobody argued with still earns a record when a criterion holds.

### Consequences

* Good, because the set holds decisions, not a log of work.
* Good, because uncontroversial decisions are recorded, not only disputed ones.
* Bad, because the criteria need judgment and will be applied inconsistently at the margins.
* Neutral, because the absence of a record is not evidence a question was overlooked.

### Confirmation

Review question: would someone who did not know this decision do the wrong thing? If
yes, it has a record.

## Pros and Cons of the Options

### A record when any of three stated criteria holds

* Good, because the threshold is written down.
* Good, because it catches decisions whose cost is in the future.
* Bad, because the margins still need judgment.

### A record per change or pull request

* Good, because it needs no judgment.
* Bad, because the set becomes a changelog too large to read.

### A record only where there was disagreement

* Good, because the set stays small.
* Bad, because it misses expensive decisions nobody disputed.

### A record for every decision, split into tiers

* Good, because nothing is left out.
* Bad, because choosing a tier is the same judgment with an extra step.

## More Information

* ADR-0001
