---
status: accepted
date: 2026-11-12
decision-makers: jim@openphase-labs.com
---

# Architecture decisions are recorded, and a record states one as of its date

## Context and Problem Statement

TSIGMA is built to be adopted by agencies that did not commission it and extended by
vendors who will never speak to its authors. Code shows what was built, not what was
rejected or why. Without that reasoning, a deliberate decision gets reversed by
accident, because nothing marked it as one.

## Decision Drivers

* Reasoning outlives the people who made the decision.
* Rejected options stay findable, so the same ground is not re-argued.
* A reader can tell a deliberate decision from an incidental choice.

## Considered Options

* Architecture Decision Records, one decision per file, each as of its date
* A design document or wiki page describing the current architecture
* Commit messages and change descriptions
* Recording nothing

## Decision Outcome

Chosen option: "Architecture Decision Records, one decision per file, each as of its
date", because it is the only option that keeps rejected options and the reasoning
behind a choice.

Significant architecture and design decisions are recorded in `docs/developers/adr/`.
A record states one decision as of its date. It is not updated to track what the
system later became.

### Consequences

* Good, because the set is a history of how the design took its shape, including the
  options it declined.
* Bad, because no record describes the system as it stands today; a reader asking how
  a subsystem works now needs a different document.
* Neutral, because a record going stale as a description of the system is expected,
  not a defect.

### Confirmation

Review: a significant decision has a record, and each record states exactly one
decision.

## Pros and Cons of the Options

### Architecture Decision Records, one decision per file, each as of its date

* Good, because the reasoning and the rejected options are kept.
* Good, because each decision has one stable place to be cited.
* Bad, because the set does not describe the current system.

### A design document or wiki page describing the current architecture

* Good, because it describes the present.
* Bad, because it is edited toward the current state until the rejected options are gone.

### Commit messages and change descriptions

* Good, because they are written anyway.
* Bad, because one decision spans many changes, and some span none.
* Bad, because a reader must already know when a decision was made to find it.

### Recording nothing

* Good, because it costs nothing.
* Bad, because the reasoning leaves with the people who hold it.

## More Information

* ADR-0002
* ADR-0003
