---
status: accepted
date: 2026-11-12
decision-makers: jim@openphase-labs.com
---

# A record is superseded, never rewritten, and the test is whether a reader would build differently

## Context and Problem Statement

Every decision is eventually overtaken. Editing the record to say the new thing keeps
the set looking current and silently erases the history the set exists to keep.
Treating every edit as a supersession spends numbers on typo fixes. The line between
the two needs a test, not a feeling.

## Decision Drivers

* The history of a decision stays intact and readable.
* Typo and wording fixes do not spend a number.
* The line between correction and supersession is mechanical.
* The rule holds whether or not the set has been published.

## Considered Options

* Supersede, never rewrite, with a build-differently test
* Edit the record to the current decision
* Delete a superseded record
* Exempt records until the set is published
* Amend in place with a change log inside the record

## Decision Outcome

Chosen option: "Supersede, never rewrite, with a build-differently test", because it
is the only option that keeps the overtaken reasoning and still allows corrections.

A record is never edited to change what it decided. A later record supersedes it; the
superseded record's status becomes `superseded by ADR-NNNN` and its text is left as
written.

Editorial correction in place is allowed: typographical fixes, a repaired
cross-reference, clearer wording of the same decision. The date does not change.

The test: if a reader following the old record would build something different from a
reader following the new one, it is a supersession. A change to what the reader owns,
what they may not do, or where a boundary sits is a supersession even when the title
survives.

Status is one of:

* `proposed` -- written, not yet settled.
* `accepted` -- in force.
* `rejected` -- considered and declined; never in force. The record is kept and its
  number stays spent.
* `deprecated` -- still usable, but no longer preferred. The old and new decisions may
  both apply for a time, and that time may run longer than planned. Deprecated is never
  an end state: it always ends as superseded or retired.
* `retired` -- was in force, and ended without a replacement.
* `superseded by ADR-NNNN` -- overtaken, and the replacement is named. A deprecated
  record becomes superseded only when the later record has fully taken over the
  reason for the original decision.

The rule applies from acceptance, published or not.

### Consequences

* Good, because overtaken reasoning stays readable for the reader about to propose it again.
* Bad, because the set grows and never shrinks, and a reader must check status before acting.
* Neutral, because a supersession spends a number on a decision that may largely restate
  its predecessor; the pair records that the question was reopened.
* Neutral, because rejected records sit in the set, so status lives in every record's
  header, not only in the index.

### Confirmation

Review: a change to an accepted record either passes the build-differently test as an
editorial correction, or it is a new record and the old record's status names it.

## Pros and Cons of the Options

### Supersede, never rewrite, with a build-differently test

* Good, because the history is intact.
* Good, because corrections stay cheap.
* Bad, because the set accumulates superseded records.

### Edit the record to the current decision

* Good, because it is the cheapest change.
* Bad, because it turns a decision history into a description of the present.

### Delete a superseded record

* Good, because the set stays small.
* Bad, because it breaks every citation, and the number cannot be reused.

### Exempt records until the set is published

* Good, because early drafts can be reshaped freely.
* Bad, because the exemption has no natural end; no moment makes a set published enough.

### Amend in place with a change log inside the record

* Good, because one subject stays in one file.
* Bad, because the record has no single date and no single answer to what was decided.

## More Information

* ADR-0001
* ADR-0002
